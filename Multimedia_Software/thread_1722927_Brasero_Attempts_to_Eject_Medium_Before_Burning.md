---
title: "Brasero Attempts to Eject Medium Before Burning"
date: 2011-04-06
forum: Multimedia Software
---

### Post by Destructo47 on 2011-04-06
This issue is new to me; I've used Brasero before with no problems.

I tried to burn some FLAC songs onto a disc (I've done this operation before with no problems), but it seems that Basero wants to eject the CD before it can burn it. I tried holding the disc tray closed to see if it would do anything, but it just kept trying to eject the CD. If I click cancel while it says "Ejecting Medium", it gives me a message telling me to manually remove the disc because it needs to be removed for the operation to continue. It then ejects it, and tells me "**Error While Burning**: Internal data stream error."

Below is a log from running brasero --brasero-burn-debug --brasero-media-debug &> brasero-debug.txt

```

progname=brasero; RGBA=on
BraseroBurn: (at burn-basics.c:233) Initializing Brasero-burn 2.30.2
BraseroMedia: (at brasero-media.c:533) Initializing Brasero-media 2.30.2
BraseroMedia: (at brasero-medium-monitor.c:657) Probing drives and media
BraseroMedia: (at brasero-medium-monitor.c:662) Found 2 drives
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium-monitor.c:387) Drive is optical
BraseroMedia: (at brasero-drive.c:1456) Initializing drive /dev/sr0 from device
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8ad84c8
BraseroMedia: (at brasero-drive.c:1327) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-drive.c:1042) Still initializing the drive properties
BraseroMedia: (at brasero-medium-monitor.c:378) Testing drive /dev/fd0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:184) No handle: Permission denied
BraseroMedia: (at brasero-medium-monitor.c:678) Found 0 volumes
BraseroBurn: (at burn-plugin-manager.c:440) opening plugin directory /usr/lib/brasero/plugins
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-growisofs.so
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image BIN 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W blank 
BraseroMedia: (at brasero-drive.c:1354) No medium inserted
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD POW W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD POW W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD DL SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc BD SRM W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD SRM W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (jump) W blank 
BraseroMedia: (at brasero-drive.c:1201) Checking supported profiles
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD RAM RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroMedia: (at scsi-get-configuration.c:127) Unaligned data (60) setting to max (65530)
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrdao.so
BraseroMedia: (at scsi-get-configuration.c:162) Sizes mismatch asked 65530 / received 60
BraseroMedia: (at brasero-drive.c:1212) Dectected medium is 0x0
BraseroMedia: (at brasero-drive.c:1419) Drive caps are 127
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CDRDAO 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CUE 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CDRDAO format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"toc2cue" could not be found in the path
"cdrdao" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module Image Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-local-track.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:439) Created new caps Image CLONE 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module File Downloader has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readom.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdrwformat.so
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc BD DL RW closed with data 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-wodim.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-genisoimage.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW blank Unformatted 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW blank 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:767) Adding blank caps for Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"cdrecord" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-transcode.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW RAW (little endian)
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio DTS WAV 
BraseroBurn: (at burn-plugin.c:1268) Module transcode has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vcdimager.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 44100 VCD Video DVD 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"vcdimager" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-mkisofs.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"mkisofs" is a symbolic link pointing to another program
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-cdda2wav.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdcss.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD DL ROM closed protected with data 
BraseroBurn: (at brasero-caps-plugin.c:660) Created Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"libdvdcss.so.2" could not be found
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-audio2cue.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CUE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW Metadata Information format accepts files pipe 
BraseroBurn: (at burn-plugin.c:1268) Module audio2cue has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-readcd.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data with audio 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with audio 
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN format accepts files pipe 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD ROM closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD ROM closed with data 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"readcd" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-burn-uri.so
BraseroBurn: (at brasero-caps-plugin.c:379) New caps required Image BIN CUE CDRDAO CLONE format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin.c:1268) Module CD/DVD Creator Folder has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-vob.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio RAW MP2 AC3 
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-dvdauthor.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-plugin-manager.c:493) Load failure, no GType was returned 
"dvdauthor" could not be found in the path
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-checksum-file.so
BraseroBurn: (at brasero-caps-plugin.c:567) New caps required Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD + RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD W closed with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW appendable with data 
BraseroBurn: (at brasero-caps-plugin.c:648) Retrieved Disc CD RW closed with data 
BraseroBurn: (at burn-plugin.c:1268) Module File Checksum has no check config function
BraseroBurn: (at burn-plugin-manager.c:462) loading /usr/lib/brasero/plugins/libbrasero-normalize.so
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-plugin.c:459) New caps required Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at brasero-caps-plugin.c:545) Created new caps Audio AUDIO UNDEFINED DTS WAV 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin.c:331) Plugin Normalize is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin.c:331) Plugin File Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin.c:331) Plugin CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin transcode is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin.c:331) Plugin wodim is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin.c:331) Plugin dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin.c:331) Plugin readom is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin.c:331) Plugin File Downloader is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin.c:331) Plugin Image Checksum is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin.c:331) Plugin growisofs is active
BraseroBurn: (at burn-plugin-manager.c:315) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed protected with data 
BraseroBurn: (at burn-basics.c:205) Created 24 links pointing to Disc CD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc CD RW closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc CD RW appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 23 links pointing to Disc CD W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD W closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with audio 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc CD W appendable with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc CD ROM closed with data with audio 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD - (sequential) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (sequential) RW appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD - (restricted) RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL ROM closed with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL + RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL + W blank 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Disc DVD DL + W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL + W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc DVD DL - (sequential) W blank 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Disc DVD DL - (sequential) W closed with data 
BraseroBurn: (at burn-basics.c:205) Created 4 links pointing to Disc DVD DL - (sequential) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD DL - (jump) W blank 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc DVD DL - (jump) W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW blank Unformatted 
BraseroBurn: (at burn-basics.c:205) Created 6 links pointing to Disc BD DL RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL SRM W blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc BD DL POW W blank 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL SRM W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 3 links pointing to Disc BD DL POW W appendable with data 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW blank 
BraseroBurn: (at burn-basics.c:205) Created 5 links pointing to Disc DVD RAM RW closed with data 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED DTS WAV Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 7 links pointing to Audio RAW Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 7 links pointing to Audio RAW Metadata Information format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio MP2 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio MP2 44100 VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 1 links pointing to Audio RAW MP2 AC3 Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Audio RAW RAW (little endian)Metadata Information format accepts files pipe 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Audio RAW RAW (little endian)AUDIO UNDEFINED DTS WAV MP2 AC3 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 25 links pointing to Image BIN format accepts pipe 
BraseroBurn: (at burn-basics.c:205) Created 21 links pointing to Image CUE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CLONE format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 15 links pointing to Image CDRDAO format accepts files 
BraseroBurn: (at burn-basics.c:205) Created 2 links pointing to Data ISO UDF VIDEO 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at burn-basics.c:205) Created 0 links pointing to Data ISO UDF SYMLINK Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at burn-plugin-manager.c:157) Getting list of plugins to be loaded
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Normalize active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdauthor is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode2vob is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. CD/DVD Creator Folder is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readcd is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. audio2cue is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvdcss is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdda2wav is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. mkisofs is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. vcdimager is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. transcode is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrecord is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. genisoimage is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. wodim is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. dvd+rw-format is active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. readom is active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin File Downloader active
BraseroBurn: (at burn-plugin-manager.c:233) Setting plugin Image Checksum active
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. cdrdao is inactive
BraseroBurn: (at burn-plugin-manager.c:201) Plugin set to active. growisofs is active
BraseroBurn: (at burn-plugin-manager.c:241) Watching GConf plugin key
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are 
BraseroBurn: (at brasero-session-cfg.c:673) New should be 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Undefined
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Image CUE 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Image CUE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2085) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CDRDAO 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CLONE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 15 links): Image CLONE 
BraseroBurn: (at brasero-caps-session.c:847) Output not supported Image CLONE 
BraseroBurn: (at brasero-caps-session.c:835) Checking support for output Image CUE 
BraseroBurn: (at brasero-caps-session.c:836) and input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:837) with flags 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 21 links): Image CUE 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 1 links): Audio MP2 VCD Video DVD Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio AUDIO UNDEFINED VIDEO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 0 links): Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2025) FLAGS: image required
BraseroBurn: (at brasero-caps-session.c:2034) FLAGS: supported no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:2035) FLAGS: compulsory 
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-drive.c:1088) GDrive changed
BraseroMedia: (at brasero-drive.c:1048) Ongoing probe
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:975) Open () cancelled
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at brasero-medium-monitor.c:492) GVolume addition signal
BraseroMedia: (at brasero-medium-monitor.c:500) Existing GDrive skipping
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:1013) Medium inserted
BraseroMedia: (at brasero-drive.c:890) Probing new medium
BraseroMedia: (at brasero-medium.c:3018) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-medium.c:3041) Open () succeeded
BraseroMedia: (at brasero-medium.c:3077) Device ready
BraseroMedia: (at brasero-medium.c:2896) Initializing information for medium in LITE-ON DVDRW SHW-160P6S
BraseroMedia: (at brasero-medium.c:2343) Retrieving media profile
BraseroMedia: (at brasero-medium.c:1508) Retrieving media available speeds
BraseroMedia: (at brasero-medium.c:1331) Retrieving speed (Get Performance)
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (8) setting to max (2048)
BraseroMedia: (at scsi-get-performance.c:204) Sizes mismatch asked 8 / received 104
Re-issuing the command with received size
BraseroMedia: (at scsi-get-performance.c:129) Unaligned data (104) setting to max (2048)
BraseroMedia: (at brasero-medium.c:1346) Successfully retrieved a header: size 104, address 0x8e85c00
BraseroMedia: (at brasero-medium.c:1350) Updated header size = 104
BraseroMedia: (at brasero-medium.c:1363) Got 6 descriptor(s)
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 0, address = 0x8e85c08
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 8467
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 1, address = 0x8e85c18
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 7056
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 2, address = 0x8e85c28
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 5645
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 3, address = 0x8e85c38
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 4234
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 4, address = 0x8e85c48
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 2822
BraseroMedia: (at brasero-medium.c:1377) Descriptor n° 5, address = 0x8e85c58
BraseroMedia: (at brasero-medium.c:1384) RD = 2117 / WRT = 1411
BraseroMedia: (at brasero-medium.c:1393) Maximum Speed (mmc3) 8467
BraseroMedia: (at brasero-medium.c:971) Checking simulate (CD SAO)
BraseroMedia: (at brasero-medium.c:984) SAO feature is supported
BraseroMedia: (at brasero-medium.c:929) Checking simulate (CD TAO)
BraseroMedia: (at brasero-medium.c:942) TAO feature is supported
BraseroMedia: (at brasero-medium.c:951) Medium can be blanked
BraseroMedia: (at brasero-medium.c:1128) Tested simulation 1 1, burnfree 1
BraseroMedia: (at brasero-medium.c:2261) Retrieving media status
BraseroMedia: (at brasero-medium.c:2225) Empty media
BraseroMedia: (at brasero-medium.c:2231) First open track 1
BraseroMedia: (at brasero-medium.c:1869) Retrieving NWA and leadout information
BraseroMedia: (at brasero-medium.c:853) Setting write mode page
BraseroMedia: (at scsi-mode-sense.c:129) Getting page size
BraseroMedia: (at scsi-mode-sense.c:169) Getting page (size = 60)
BraseroMedia: (at brasero-medium.c:874) Former write type 1
BraseroMedia: (at brasero-medium.c:875) Former track mode 4
BraseroMedia: (at brasero-medium.c:876) Former data block type 8
BraseroMedia: (at brasero-medium.c:1938) Next Writable Address is 0
BraseroMedia: (at brasero-medium.c:1945) Free blocks 359843
BraseroMedia: (at brasero-medium.c:1962) Leadout: start = 0 size = 359843
BraseroMedia: (at brasero-medium.c:2948) media is CD W blank 
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-basics.c:443) checking media caps for Disc CD W blank 
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 23 links): Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:308) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-session.c:2037) Available space on medium 359843
BraseroBurn: (at brasero-session-cfg.c:968) Session size 218914/Disc size 359843
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroBurn: (at burn-basics.c:443) checking media caps for Disc CD W blank 
BraseroBurn: (at brasero-session-cfg.c:809) Restoring session properties
BraseroBurn: (at brasero-session-cfg.c:671) Resetting all flags
BraseroBurn: (at brasero-session-cfg.c:672) Current are no grace, check size, 
BraseroBurn: (at brasero-session-cfg.c:673) New should be no grace, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): dao, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): dao, burnproof, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 23 links): Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, dao, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-session.c:2235) Session starting:
BraseroBurn: (at brasero-session.c:2240) Input	= Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-session.c:2241) flags	= eject, no grace, dao, burnproof, check size, 
BraseroBurn: (at brasero-session.c:2283) media type	= Disc CD W blank 
BraseroBurn: (at brasero-session.c:2284) speed	= 1411000
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:197) Mount point is (null)
BraseroBurn: (at brasero-burn.c:798) Media inserted is Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 23 links): Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc CD W blank 
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:527) Device locked
BraseroBurn: (at brasero-burn.c:1741) Checking session consistency
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-caps-session.c:2080) FLAGS: searching available flags for input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:2129) FLAGS (session): eject, no grace, dao, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:1610) FLAGS: trying caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:220) Testing blanking caps for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:247) Searching links for caps Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:278) No blanking capabilities for Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:2177) FLAGS: supported eject, no grace, dao, overburn, burnproof, no tmp file, multi, dummy, check size, 
BraseroBurn: (at brasero-caps-session.c:2178) FLAGS: compulsory dao, 
BraseroBurn: (at brasero-burn.c:1839) Flags after checking = eject, no grace, dao, burnproof, check size, 
BraseroBurn: (at brasero-caps-session.c:1075) Checking support for session. Ouput is  Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:1076) and input is Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 23 links): Disc CD W blank 
BraseroBurn: (at brasero-caps-session.c:568) Found link (with 7 links): Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-session.c:1098) Session supported Disc CD W blank 
BraseroBurn: (at brasero-caps-burn.c:674) Creating recording/imaging task Disc CD W blank 
BraseroBurn: (at brasero-caps-burn.c:684) Input set = Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Disc CD W blank 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio RAW 
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Image CUE 
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:440) Trying wodim with a priority of 0
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image CUE 
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:380) Not connectable
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:440) Trying audio2cue with a priority of 0
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:491) Trying wodim with a priority of 0
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Image BIN 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:440) Trying genisoimage with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Data ISO UDF Level 3 JOLIET VIDEO DEEP 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying genisoimage with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Data ISO SYMLINK Level 3 DEEP 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying genisoimage with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Data ISO UDF VIDEO 
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:404) No plugin found
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:491) Trying wodim with a priority of 0
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio RAW 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio DTS WAV 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio AUDIO UNDEFINED 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio DTS WAV 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:491) Trying wodim with a priority of 0
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:386) Can't go further than DISC caps
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:408) Found candidate link Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:328) find_best_link Audio DTS WAV Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:423) No links found
BraseroBurn: (at brasero-caps-burn.c:440) Trying transcode with a priority of 1
BraseroBurn: (at brasero-caps-burn.c:580) Adding modifiers (position 1) (1 modifiers available) for Audio AUDIO UNDEFINED Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-burn.c:623) Normalize (modifier) added to task
BraseroBurn: (at brasero-caps-burn.c:625) IO type Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:818) New task
BraseroBurn: (at brasero-caps-burn.c:828) transcode added to task
BraseroBurn: (at brasero-caps-burn.c:829) input Audio AUDIO UNDEFINED Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:830) output Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:580) Adding modifiers (position 2) (0 modifiers available) for Audio RAW Metadata Information format accepts files 
BraseroBurn: (at brasero-caps-burn.c:818) New task
BraseroBurn: (at brasero-caps-burn.c:828) wodim added to task
BraseroBurn: (at brasero-caps-burn.c:829) input Audio RAW Metadata Information 
BraseroBurn: (at brasero-caps-burn.c:830) output Disc CD W blank 
BraseroBurn: (at brasero-burn.c:2074) 3 tasks to perform
BraseroBurn: (at burn-task.c:600) Starting fake task (2)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (15 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroNormalize
BraseroBurn: (at burn-job.c:1433) BraseroNormalize called brasero_job_get_action
BraseroBurn: (at burn-task.c:522) ::start skipped for BraseroNormalize
BraseroBurn: (at burn-task.c:619) Task skipped
BraseroBurn: (at brasero-burn.c:2202) Burning from 0 to 0
BraseroBurn: (at burn-task.c:600) Starting normal task (0)
BraseroBurn: (at burn-task-ctx.c:159) Setting current track (15 tracks)
BraseroBurn: (at burn-task.c:336) ::activate method BraseroNormalize
BraseroBurn: (at burn-job.c:1433) BraseroNormalize called brasero_job_get_action
BraseroBurn: (at burn-job.c:1297) BraseroNormalize called brasero_job_get_tracks
BraseroBurn: (at burn-task.c:293) ::start method BraseroNormalize
BraseroBurn: (at burn-job.c:1433) BraseroNormalize called brasero_job_get_action
BraseroBurn: (at burn-job.c:1790) BraseroNormalize called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:667) BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_GPH8SV.cdr
BraseroBurn: (at burn-job.c:511) ext3/ext4 filesystem detected
BraseroBurn: (at burn-job.c:1790) BraseroNormalize called brasero_job_get_session_output_size
BraseroBurn: (at burn-job.c:530) Volume size 268752801792, output size 0
BraseroBurn: (at burn-job.c:1297) BraseroNormalize called brasero_job_get_tracks
BraseroBurn: (at burn-job.c:944) BraseroNormalize called brasero_job_tag_lookup
BraseroBurn: (at burn-normalize.c:360) BraseroNormalize Analysing track file:///home/nick/Music/My%20Music/Linkin%20Park/Specials/EP's%20and%20Specials!/01%20-%20Plaster.flac
BraseroBurn: (at burn-normalize.c:160) BraseroNormalize Creating new pipeline
BraseroBurn: (at burn-normalize.c:134) BraseroNormalize New decoded pad linked
BraseroBurn: (at burn-job.c:1861) BraseroNormalize called brasero_job_set_current_action
BraseroBurn: (at burn-task.c:442) entering loop
BraseroBurn: (at burn-normalize.c:507) BraseroNormalize gstflacdec.c(1082): gst_flac_dec_loop (): /GstPipeline:pipeline15/GstDecodeBin:decodebin15/GstFlacDec:flacdec15:
stream stopped, reason not-negotiated
BraseroBurn: (at burn-job.c:1138) BraseroNormalize called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroNormalize finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroNormalize asked to stop because of an error
	error		= 1
	message	= "Internal data stream error."
BraseroBurn: (at burn-task.c:182) stopping BraseroNormalize
BraseroBurn: (at burn-job.c:906) BraseroNormalize stopping
BraseroBurn: (at burn-task.c:190) stopped BraseroNormalize
BraseroBurn: (at burn-task.c:448) got out of loop
BraseroBurn: (at burn-task.c:177) BraseroNormalize already stopped
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:567) Device unlocked
BraseroBurn: (at brasero-burn.c:389) Ejecting drive/medium
BraseroMedia: (at brasero-volume.c:102) Found volume /dev/sr0
BraseroMedia: (at brasero-volume.c:197) Mount point is (null)
BraseroBurn: (at brasero-burn.c:440) Retrying ejection
BraseroMedia: (at brasero-drive.c:280) Trying to eject drive
BraseroMedia: (at brasero-gio-operation.c:111) Waiting for end of async operation
BraseroMedia: (at brasero-drive.c:1075) Waiting for next unlocking of the drive to probe
BraseroMedia: (at brasero-medium-monitor.c:639) Drive removal signal
BraseroMedia: (at brasero-medium-monitor.c:588) Found device to remove
BraseroMedia: (at brasero-medium-monitor.c:612) Volume removal signal
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-medium-monitor.c:477) GDrive addition signal
BraseroMedia: (at brasero-medium-monitor.c:442) Added signal was emitted but the drive is in the removal list. Updating GDrive associated object.
BraseroMedia: (at brasero-drive.c:1111) Setting GDrive 0x8e815f8
BraseroMedia: (at brasero-drive.c:1048) Ongoing
(brasero:2481): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
 probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:975) Open () cancelled
BraseroMedia: (at brasero-drive.c:1052) Setting new probe
BraseroMedia: (at brasero-drive.c:952) Trying to open device /dev/sr0
BraseroMedia: (at scsi-sg.c:181) Getting handle
BraseroMedia: (at scsi-sg.c:200) Handle ready
BraseroMedia: (at brasero-drive.c:983) No medium inserted
BraseroMedia: (at brasero-drive.c:903) Medium removed
BraseroMedia: (at brasero-volume.c:455) Finalizing Volume object
BraseroMedia: (at brasero-medium.c:3151) Finalizing Medium object
BraseroBurn: (at brasero-burn.c:2839) Session error : Internal data stream error.
BraseroBurn: (at brasero-session.c:2392) Cleaning session
BraseroBurn: (at brasero-session.c:2369) Cleaning /tmp/brasero_tmp_GPH8SV.cdr
```

---

### Post by wkulecz on 2011-04-06
It just keeps getting worse and worse.  Throw it aways and go back to what was in 8.04 which still works (on 8.04).

---

### Post by Destructo47 on 2011-04-06
> **wkulecz said:**
> It just keeps getting worse and worse.  Throw it aways and go back to what was in 8.04 which still works (on 8.04).

If you're telling me to downgrade to 8.04, then you're not really helping. I appreciate your honesty, but I'd prefer to keep my install as is.

---

### Post by wkulecz on 2011-04-07
I kept 8.04 as dual boot when I moved to 10.04.  Good thing! as CD/DVD burning has never worked completely correct in in 10.04 starting with the Betas.

It has had multiple cycles of work, broke, work, broke with updates.  Currently broke again for me now too.

I either dual boot to 8.04 or use a Windows box when I need to burn disks.
This is a major embarrassment to the Ubuntu team IMHO.

My suggestion if disk burning is "mission critical" would be to keep applying updates and if burning start working again, turn off the updates.

Fortunatley I no longer need to burn many disks, but still it is very inconvienent for something than Ubuntu had working way better than on Windows since 6.06 to suddenly be worthless :(

---

### Post by jhbowlin on 2011-04-07
The CD is ejecting for me and I'm trying to burn an image.  I agree that this is embarrassing.

---

### Post by Destructo47 on 2011-04-08
I found a workaround (sort of) by trying to burn in K3b, which is not one the default packages. If Brasero's functionality continually is fixed then re-broken by updates, then it would be nice if we knew specifically what is being updated that breaks it.

As for jhbowlin, try installing k3b:
```
sudo apt-get install k3b
```

Type that into a terminal and it should install.

---

### Post by jhbowlin on 2011-04-10
Thanks for the pointer Destructo47, but unfortunately k3b is failing also:

p, li { white-space: pre-wrap; } [FONT=Monospace]reading sectors 254271 to 273274 with sector size 2056. Length: 19004 sectors, 39072224 bytes.[/FONT]
 [FONT=Monospace]using buffer size of 32 blocks.[/FONT]
 [FONT=Monospace]Problem while reading. Retrying from sector 254335.[/FONT]
 [FONT=Monospace]Read error in sector 254348.[/FONT]
 [FONT=Monospace]Read a total of 64 sectors (131584 bytes)[/FONT]

---

### Post by Destructo47 on 2011-04-11
> **jhbowlin said:**
> p, li { white-space: pre-wrap; } [FONT=Monospace]reading sectors 254271 to 273274 with sector size 2056. Length: 19004 sectors, 39072224 bytes.[/FONT]
 [FONT=Monospace]using buffer size of 32 blocks.[/FONT]
 [FONT=Monospace]Problem while reading. Retrying from sector 254335.[/FONT]
 [FONT=Monospace]Read error in sector 254348.[/FONT]
 [FONT=Monospace]Read a total of 64 sectors (131584 bytes)[/FONT]

Is this during a disc burning session or during the install?

---

### Post by jhbowlin on 2011-04-11
This is happening when I do Tools->Copy Medium.  No problem with the install.

---

### Post by Ohnanka on 2011-05-20
I have the same problem with Braseo, however 'DeVeDee' works fine!  search for it in the software centre.
Anyway, new version soon, maybe they'll fix this?

---

### Post by Destructo47 on 2011-06-02
Ehh, sorry I wasn't more help. Glad to see something works for you, though.

---

### Post by I'mGeorge on 2011-06-02
Brasero is one buggy piece of software, I can't even run it properly from the wm I'm using. Have you considered using k3b or other cd burning software

---

### Post by Destructo47 on 2011-06-04
Actually, I use both. I don't know why, but sometimes using one or the other makes sense to me. Recently, I used Brasero to make a live cd for Natty, but I have used k3b to make a DVD video from an iso image.

---

