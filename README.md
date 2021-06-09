# macOS  on Huawei Matebook X 2020 (EUL-W19P)
This repo is currently compatible with macOS Big Sur and OpenCore 0.6.9

Read the entire README before you start.
I am not responsible for any damages you may cause.
Should you find an error or improve anything — whether in the config or in the documentation — please consider opening an issue or pull request.
Complete EFI packs are available in the Releases page (please, refer to the rightside menu).
Please do not clone or download the main branch for daily use: it may include unstable code just because it is my repository.

If you find this bootloader configuration useful, consider giving it a star to make it more visible.

If you find my work useful, please consider donating via PayPal. 

This repository is for personal purposes

Generate your own SMBIOS Information
For privacy reasons, all SMBIOS information has been wiped out in the configuration file EFI/OC/config.plist. You need to generate your unique SMBIOS info by yourself (recommend to use CorpNewt's GenSMBIOS), and inject them into your config.plist.

With every EFI update you retrieve from here, please, remember to transfer your Device details under PlatformInfo -> Generic in your config.plist.
For more details on dual booting settings, please, see also below OpenCore notes.

There are two different config.plist in the release zip. The default one is to use in case you've modded your BIOS for CGF unlock and DMVT to 64MB.
If you haven't done these mods to your BIOS use the other config.plist prior renaming it to config.plist


# WHAT IS WORKING
 Intel(R) UHD 620 Graphics card
 
 Intel(R) Wireless-AC & Intel(R) Bluetooth
 
 Power Management with support for HWP (Intel Speed Shift & Intel SpeedStep)
 
 Sleep and Wake (support for native macOS hibernatemode3)
 
 Hibernation (support for native macOS hibernatemode25 with HibernationFixup.kext)
 
 Battery support with better memory access and integration of Battery Information Supplement
 
 Automatic Backlight control (with more granular levels)
 
 Backlight shortcuts (F1 [brightness level down] - F2 [brightness level up])
 
 Volume shortcuts (F4 [mute] - F5 [audio level down] - F6 [audio level up])
 Audio for Realtek ALC256 card (via AppleALC.kext and layout-id 57)
 
 Speakers & Internal Mic
 
 HDMI 2.0 up to two 4K @60 Hz monitors (via LSPCON). *** ONLY THE RIGHT TYPE-C PORT WORKS TO CONNECT AN EXTERNAL MONITOR USING THE ADAPTER ***
 
 TouchPad (via Polling mode) and native macOS gestures
 
 Touchscreen (via GPIO mode) and native macOS gestures
 
 USB Ports Mapping (Type-C) with proper power levels
 
 NVRAM native support
 
 # WHAT IS NOT WORKING
 HD Camera (Disable using SSDT)
 
 Fingerprint Senson (disabled in BIOS)
 
 
# POST - INSTALL SETTINGS
Sleep and Hibernation
Sleep function works flawlessly (both via software and via clamshell) like hibernation (suspend to disk or S4 sleep). 
In order to get automatic sleep working properly like real Macs, the following settings are mandatory:

sudo pmset -a standby 0

sudo pmset -a powernap 0 

sudo pmset -a proximitywake 0

sudo pmset -a tcpkeepalive 0

sudo pmset -a womp 0

sudo pmset -a hibernatemode 25


Download and install ALCPlugFix from this repository to fix audio problems after sleep
