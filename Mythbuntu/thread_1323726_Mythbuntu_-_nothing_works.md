---
title: "Mythbuntu - nothing works"
date: 2009-11-12
forum: Mythbuntu
---

### Post by MountainX on 2009-11-12
Problem: There is apparently more than one issue. I can't seem to narrow it down or make any progress solving anything. I have no live TV. No ability to watch mpg videos. I tried to play a DVD and even that failed. I have no experience with MythTV, so I'm finding trouble shooting a bit difficult.

(Actually, the only thing that works is playing music.)

The most common error message I see when trying to watch TV is:
TV Error: LiveTV not successfully started

Sometimes, while testing different configs, I have gotten this:
"Mythtv is using all inputs, but there are no active recordings?" 			 		

I've spent some time googling all the error messages. My backend IP address is correct. My folder permissions look correct. I can't seem to find anything wrong. 

Here is the trouble shooting I have done:

[LIST=1]
[*]SageTV will run on this hardware without problems.
[*]cat /dev/video0 > test.mpg successfully records a video that VLC will play back.
[*]vlc /dev/video0 shows live TV on the channel guide channel (Comcast cable)
[/LIST]

I'll list my system info for starters:

==> uname -a <==
```
Linux MythbuntuBox 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux
```

==> lsb_release -a <==
```
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
```


==> /var/log/Xorg.0.log <==
```

(II) RADEON(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: GWY  Model: 13  Serial#: 16843009
(II) RADEON(0): Year: 1998  Week: 0
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 27
(II) RADEON(0): Gamma: 2.30
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.605
(II) RADEON(0): blueX: 0.150 blueY: 0.065   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #6: hsize: 720  vsize 405  refresh: 70  vid: 51771
(II) RADEON(0): #7: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 202.5 MHz   Image Size:  360 x 270 mm
(II) RADEON(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) RADEON(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 95 kHz,
(II) RADEON(0): Monitor name: GATEWAY VX900
(II) RADEON(0): Serial No: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff001ef9130001010101
(II) RADEON(0):     000801010e241b82e800b9a057499b26
(II) RADEON(0):     10484cffef80a94f8199615961404559
(II) RADEON(0):     45403bca31591a4f403062b0324040c0
(II) RADEON(0):     1300680e1100001e000000fd0032a01e
(II) RADEON(0):     5fff000a202020202020000000fc0047
(II) RADEON(0):     415445574159205658393030000000ff
(II) RADEON(0):     002020202020202020202020202000ee
(II) RADEON(0): EDID vendor "GWY", prod id 19
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
```

==> lspci <==
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
```

==> lsusb <==
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 010: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 002 Device 009: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 005: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 002 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 002: ID 04ca:0009 Lite-On Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by blackoper on 2009-11-12
First thing I would check are the mythtvbackend.log files in /var/log/mythtv directory. I like to delete them with the rm command and then use nano to read the logs after making the error happen in the frontend.

Were your capture cards setup correctly in mythbackend setep?

next the lspci isn't very helpful try a sudo lspci -v  (the verbose lets us know more info about your capture cards).

Also you can't play dvd's in mythbuntu by default without installing a 3rd party codec/program called css to decrypt the dvd. You can activate this in the mythbuntu control center under proprietary codecs i believe

---

### Post by wewantutopia on 2009-11-12
can you watch anything in vlc player?  I've been playing with the nvidia 190 driver and now vlc player wont play anything.  Nor will movie player now I check.  Audio, but no video.  Just wondering if they are related.

---

### Post by MountainX on 2009-11-12
> **blackoper said:**
> First thing I would check are the mythtvbackend.log files in /var/log/mythtv directory. I like to delete them with the rm command and then use nano to read the logs after making the error happen in the frontend.

Were your capture cards setup correctly in mythbackend setep?

next the lspci isn't very helpful try a sudo lspci -v  (the verbose lets us know more info about your capture cards).

Also you can't play dvd's in mythbuntu by default without installing a 3rd party codec/program called css to decrypt the dvd. You can activate this in the mythbuntu control center under proprietary codecs i believe
Thanks for your help.
I believe the capture cards are set up correctly in the backend setup.
I did add the codecs for playing DVDs previously.
I verified that vlc /dev/video0 still works -- it does. It even starts on channel 53, which is what I configured in MythTV setup as the starting channel. (I assume MythTV tuned to that channel when I tried to watch live TV - without success.)
After deleting the backend log as you suggested, then starting the frontend and producing this error, there is a frontend log but no backend log was created.

Here's the other info you requested.

```
Starting mythfrontend.real..
2009-11-12 02:01:12.167 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-12 02:01:12.168 Using runtime prefix = /usr
2009-11-12 02:01:12.168 Using configuration directory = /home/username/.mythtv
2009-11-12 02:01:13.023 Empty LocalHostName.
2009-11-12 02:01:13.023 Using localhost value of MythFire
2009-11-12 02:01:13.024 Testing network connectivity to '10.10.1.1'
2009-11-12 02:01:13.040 New DB connection, total: 1
2009-11-12 02:01:13.102 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:01:13.103 Closing DB connection named 'DBManager0'
2009-11-12 02:01:13.118 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-12 02:01:13.119 DPMS is active.
2009-11-12 02:01:13.122 Primary screen: 0.
2009-11-12 02:01:13.177 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:01:13.180 Using screen 0, 1600x1200 at 0,0
2009-11-12 02:01:13.198 MythUI Image Cache size set to 20971520 bytes
2009-11-12 02:01:13.199 Enabled verbose msgs:  important general
2009-11-12 02:01:13.212 Primary screen: 0.
2009-11-12 02:01:13.213 Using screen 0, 1600x1200 at 0,0
2009-11-12 02:01:13.214 Using theme base resolution of 1280x720
2009-11-12 02:01:13.227 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2009-11-12 02:01:13.227 JoystickMenuThread Error: Joystick disabled - Failed to read /home/username/.mythtv/joystickmenurc
2009-11-12 02:01:13.571 Using the Qt painter
2009-11-12 02:01:13.888 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-12 02:01:13.902 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-12 02:01:13.925 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-12 02:01:13.926 Unable to load window 'backgroundwindow' from base
2009-11-12 02:01:13.940 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-12 02:01:13.966 New DB connection, total: 2
2009-11-12 02:01:14.021 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:01:15.744 Desktop video mode: 1600x1200 75.0019 Hz
2009-11-12 02:01:16.293 Registering Internal as a media playback plugin.
2009-11-12 02:01:16.492 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2009-11-12 02:01:16.497 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2009-11-12 02:01:16.508 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2009-11-12 02:01:16.514 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-12 02:01:16.836 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-12 02:01:16.934 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-12 02:01:16.994 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-12 02:01:17.131 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-12 02:01:17.232 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-12 02:01:17.237 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-12 02:01:18.732 MythContext: Connecting to backend server: 10.10.1.1:6543 (try 1 of 1)
2009-11-12 02:01:18.733 Using protocol version 50
2009-11-12 02:01:23.389 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-12 02:01:23.391 MythContext: Connecting to backend server: 10.10.1.1:6543 (try 1 of 1)
2009-11-12 02:01:23.392 Using protocol version 50
2009-11-12 02:01:23.467 Spawning LiveTV Recorder -- begin
2009-11-12 02:01:23.896 Spawning LiveTV Recorder -- end
2009-11-12 02:01:23.914 We have a playbackURL(/var/lib/mythtv/livetv/1053_20091112020123.nuv) & cardtype(V4L)
2009-11-12 02:01:23.916 We have a RingBuffer
2009-11-12 02:02:03.971 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-11-12 02:02:03.971 TV Error: LiveTV not successfully started
2009-11-12 02:02:03.975 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-12 02:02:03.980 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-12 02:02:09.678 Deleting UPnP client... 
``````
# lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80f2
    Flags: bus master, fast devsel, latency 0
    Memory at 84000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [e4] Vendor Specific Information <?>
    Capabilities: [a0] AGP version 3.0
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7e00000-f7efffff
    Prefetchable memory behind bridge: e0000000-ebffffff
    Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Flags: fast devsel
    Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at cc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7dffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7f00000-fbffffff
    Prefetchable memory behind bridge: ec000000-f6ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fc00 [size=16]
    Memory at 80000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: medium devsel, IRQ 11
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80f3
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at c000 [size=256]
    I/O ports at c400 [size=64]
    Memory at f7dff800 (32-bit, non-prefetchable) [size=512]
    Memory at f7dff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
    Subsystem: C.P. Technology Co. Ltd Device 2037
    Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at d000 [size=256]
    Memory at f7ef0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at f7ec0000 [disabled] [size=128K]
    Capabilities: [58] AGP version 2.0
    Capabilities: [50] Power Management version 2
    Kernel modules: radeon, radeonfb

02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device 80eb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    Memory at f7ffc000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at e800 [size=256]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Vital Product Data <?>
    Kernel driver in use: skge
    Kernel modules: skge

02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
    Subsystem: Hauppauge computer works Inc. Device 8801
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f0000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ivtv
    Kernel modules: ivtv

02:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
    Subsystem: Hauppauge computer works Inc. Device 8801
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at ec000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ivtv
    Kernel modules: ivtv

02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
    Subsystem: Hauppauge computer works Inc. Device 13eb
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f6ffe000 (32-bit, prefetchable) [size=4K]
    Kernel driver in use: bttv
    Kernel modules: bttv

02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
    Subsystem: Hauppauge computer works Inc. Device 13eb
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f6fff000 (32-bit, prefetchable) [size=4K]
    Kernel driver in use: Bt87x
    Kernel modules: snd-bt87x
 
```

---

### Post by MountainX on 2009-11-12
```
# service mythtv-backend restart
mythtv-backend start/running, process 12758

/var/log/mythtv# cat mythbackend.log
2009-11-12 02:21:31.485 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-12 02:21:31.551 Using runtime prefix = /usr
2009-11-12 02:21:31.584 Using configuration directory = /home/mythtv/.mythtv
2009-11-12 02:21:31.618 Empty LocalHostName.
2009-11-12 02:21:31.651 Using localhost value of MythFire
2009-11-12 02:21:31.685 Testing network connectivity to '10.10.1.1'
2009-11-12 02:21:31.733 New DB connection, total: 1
2009-11-12 02:21:31.835 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:21:31.868 Closing DB connection named 'DBManager0'
2009-11-12 02:21:31.961 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:21:32.002 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-12 02:21:32.038 MythBackend: Starting up as the master server.
2009-11-12 02:21:32.080 New DB connection, total: 2
2009-11-12 02:21:32.180 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:21:32.218 New DB connection, total: 3
2009-11-12 02:21:32.360 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:21:32.700 New DB scheduler connection
2009-11-12 02:21:32.804 Connected to database 'mythconverg' at host: 10.10.1.1
2009-11-12 02:21:32.884 Enabling Upnpmedia rebuild thread.
2009-11-12 02:21:34.366 Main::Registering HttpStatus Extension
2009-11-12 02:21:34.394 Enabled verbose msgs:  important general
2009-11-12 02:21:34.431 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-12 02:21:35.848 Reschedule requested for id -1.
2009-11-12 02:21:35.971 Scheduled 0 items in 0.1 = 0.03 match + 0.09 place
2009-11-12 02:21:36.010 Seem to be woken up by USER
2009-11-12 02:21:42.914 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-11-12 02:21:42.955 UPnpMedia: BuildMediaMap Done. Found 3 objects
2009-11-12 02:21:42.975 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/sda1:
2009-11-12 02:21:43.487 UPnpMedia: BuildMediaMap Done. Found 319 objects
2009-11-12 02:21:43.508 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/sdb1:
2009-11-12 02:21:44.432 UPnpMedia: BuildMediaMap Done. Found 627 objects
2009-11-12 02:21:44.466 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/sdd1:

```

live TV does not work, as stated above.
In addition, in the media library when I try to play videos it finds no files. The log above shows that files are found in my configured video directories (e.g., /media/sda1, etc.)

---

### Post by superm1 on 2009-11-12
Check all your permissions in /var/lib/mythtv.  Does the user 'mythtv' have write access to all files and directories?

---

### Post by MountainX on 2009-11-12
> **superm1 said:**
> Check all your permissions in /var/lib/mythtv.  Does the user 'mythtv' have write access to all files and directories?

It looks good to me. This was one of the first things I checked:
/var/lib/mythtv$ ls -la
```
total 52
drwxr-xr-x 13 root   root   4096 2009-10-28 16:28 .
drwxr-xr-x 54 root   root   4096 2009-11-12 00:45 ..
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 banners
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 coverart
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 db_backups
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 fanart
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:28 livetv
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-09 10:37 music
drwxrwxr-x  3 mythtv mythtv 4096 2009-11-12 02:27 pictures
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 recordings
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 screenshots
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 trailers
drwxrwsr-x  2 mythtv mythtv 4096 2009-11-12 02:21 videos
```

---

### Post by MountainX on 2009-11-12
SOLVED: thanks to newlinux
[http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok-2.html#post48639](http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok-2.html#post48639)
> as mentioned before, your PVR-x50 cards should be setup as MPEG-2 encoder cards in mythtv-setup, not sure what your 3rd card is, but it looks like it should be setup as V4L. At this point, though, I recommend you work on one card at a time and remove the others. Start with one of the mpeg-2 encoders. Lets get that card to work (Delete the others from mythtv).
 
Make those changes, try again, post your logs if it doesn't work. Make sure you have a valid starting channel to tune to. 

---

### Post by YogiPaolo on 2010-01-08
I am having a similar problem. My eyes are bleary and it's 4am as the obsession continues. Such great promise that I hold out to 3TB worth of raid arrays...

Mythweather won't even recognize "new york, new york".

I can play a DVD but that's about it. 

I'll post more info when I get some sleep...

---

### Post by MountainX on 2010-01-08
I gave up on MythTV for now. After every problem I solved, new ones came up that prevented it from working. So I just pulled the plug on my dedicated Mythbuntu server and I'm letting it sit there for a while. I feel like I should have stuck with SageTV for Linux. At least it worked. MythTV shows a lot of promise, but the frustration burned me out on it -- for now.

---

### Post by YogiPaolo on 2010-01-08
I'm in the same boat. I'm almost thinking about "the other os"...


While there I have respect and gratitude for the talent and effort dedicated to the project, if it doesn't work, it doesn't work. I'm going to give it one more go this evening and then explore other alternatives. 

I'll post my experience here and maybe give some useful feedback.

---

### Post by MountainX on 2010-01-08
> **YogiPaolo said:**
> I'm almost thinking about "the other os"...

ha ha. Well, I can certainly sympathize, but why not consider SageTV for Linux if you don't have better luck with MythTV?

---

### Post by YogiPaolo on 2010-01-13
I'll consider sage tv.

In the meantime, I've taken a deep breath and have made some progress.

I have the 2250 card working with the stable drivers. Right now the problem is that the tuners show up twice in mythbackend and the frontend shows them twice also. I don't know what this means. The result seems to be that the backend can't lock stations and recordings crap out part-way through.

---

### Post by MountainX on 2010-01-13
The best help for MythTV is actually found on the mailing lists. I don't think this forum or any other forum will give much help compared to the mailing lists.

As for me, I am still not ready to jump back into MythTV stuff. I got distracted with VoIP and Android. :)

---

