---
title: "Beginner configures Mythbuntu"
date: 2010-02-27
forum: Mythbuntu
---

### Post by perjojek on 2010-02-27
[FONT=Times New Roman][SIZE=3]I have a number of problems with configuring MythTV (Mythbuntu) on my HTPC.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1)[/SIZE] [SIZE=3]my remote control (case [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]techsolo TC-600[/SIZE][/FONT]]("http://www.techsolo.net/site/product.php?lang=en&do=show&product_id=263&class_id=34")[FONT=Times New Roman][SIZE=3]) seems not to be supported[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2)[/SIZE] [SIZE=3]7.1 sound card (on-board [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]M5N78-VM[/SIZE][/FONT]]("http://www.asus.com/product.aspx?P_ID=CMQkJloA9dyXDIeS")[FONT=Times New Roman][SIZE=3]) does not work. I can hear music when I hook up a stereo head-set to the front panel. However, my AV-Receiver does not get any signal from the SPDIF port.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3)[/SIZE] [SIZE=3]When scanning channels (backend > Channel Editor) I get the following message: “Error parsing parameters”. I have [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]Mystique CaBiX-C2[/SIZE][/FONT]]("http://translate.google.com/translate?u=http://www.mystique-tv.de/download/cat_view/44-produktpraesentation--product-presentation.html&hl=en&ie=UTF-8&sl=auto&tl=en")[FONT=Times New Roman][SIZE=3] capture card, not sure if it works properly.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]4)[/SIZE] [SIZE=3]DVD plays neither films nor music. When you select “Play DVD”, the screen displays the background and switches back to the menu window after a second.[/SIZE][/FONT]
 
[FONT=Times New Roman]Please, help me to convince myself (and others) that it is possible to configure Mythbuntu to work decently[/FONT]

---

### Post by nickrout on 2010-02-27
what is the remote device receiver? Is it usb? if so what does lsusb tell you?

what audio devices do you have and what have you set myth to output to? try running aplay -L and aplay -l and report back.

I have never heard of your tuner card, is a driver found for it by the kernel? what does dmesg tell you?

Have you set it up in mythtv-setup? With what results?

When you try to play a dvd what does mythfrontend.log tell you?

---

### Post by tony.keller on 2010-02-27
As for the DVD player not working...make sure that you have the right name for the drive in your MythTV Frontend Settings.  /dev/dvd or whatever may not be your name of your drive.

Execute this command from a terminal
blkid

That command should show info about the drives hooked to your machine.  Just note the section that applies to the DVD drive and copy the /dev/scd0 or whatever they list.

---

### Post by nickrout on 2010-02-28
wow I never knew about blkid before. By the way I found it did nothing unless run nby root, ie sudo blkid

---

### Post by SiHa on 2010-02-28
> 3) When scanning channels (backend > Channel Editor) I get the following message: “Error parsing parameters”.

Not sure about the rest, but I got this error (albeit for a DVB-S scan) when I had a character it wasn't expecting in one of the settings entry boxes - in my case it was a '.' in the transponder frequency.

---

### Post by perjojek on 2010-02-28
> **nickrout said:**
> what is the remote device receiver? Is it usb? if so what does lsusb tell you?

The remote control was delivered together with the TC-600 case. Yes, it has a usb transmitter. Here is how I connected it (see the attached jpg and the [techsolo support site]("http://www.techsolo.net/site/support.php?lang=en#target13") > case): 
VCC : VCC
D0- : USB1-
D0+ : USB1+
GND: GND

lsusb
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1130:6604 Tenx Technology, Inc. 
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is any of them an IR transmitter?

---

### Post by perjojek on 2010-02-28
> **nickrout said:**
> what audio devices do you have and what have you set myth to output to? try running aplay -L and aplay -l and report back.

Audio output device: ALSA:default
Max Audio Channels: 5.1

aplay-L result:
default:CARD=NVidia
    HDA NVidia, ALC887 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


aplay-l results:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by perjojek on 2010-02-28
> **nickrout said:**
> I have never heard of your tuner card, is a driver found for it by the kernel? what does dmesg tell you?


Mystique CaBiX-C2 tuner card, per information from the  manufacturer, is identical to KNC1 TV-Station DVB-C and works well with its drivers.

I have no clue if kernel found a driver for it. How do I check it? I attached the dmesg results as a text file. Are you able to diagnose anything?

---

### Post by perjojek on 2010-02-28
> **nickrout said:**
> I have never heard of your tuner card, is a driver found for it by the kernel? what does dmesg tell you?

Have you set it up in mythtv-setup? With what results?

In Backend Setup > Capture Cards I selected "DVB DTV capture card (v3.x)". Two problems that I encounter are:
1) I am not able to scann channels (Error parsing parameters)
2) When exiting from Backend setup  I get the following message: "Card 1 (CardDVBInput) is set to start on channel
Please add, which does not exist
Card 2 (CardDVBInput) is set to start on channel
Please add, which does not exist"

---

### Post by perjojek on 2010-02-28
> **nickrout said:**
> When you try to play a dvd what does mythfrontend.log tell you?

Where do I find the log file? Can you give me the path?

---

### Post by SiHa on 2010-02-28
Should be **/var/log/mythtv/mythfrontend.log**

---

### Post by perjojek on 2010-02-28
> **tony.keller said:**
> As for the DVD player not working...make sure that you have the right name for the drive in your MythTV Frontend Settings.  /dev/dvd or whatever may not be your name of your drive.

Execute this command from a terminal
blkid

blkid generated: 
/dev/sde1: UUID="91b66492-e610-4842-894c-6e0df28f0cb5" TYPE="ext4" 
/dev/sde5: UUID="42b1569a-6558-49f7-9b91-4554ede0661c" TYPE="swap" 

I tired both but without success..

---

### Post by nickrout on 2010-02-28
> **perjojek said:**
> Audio output device: ALSA:default
Max Audio Channels: 5.1

aplay-L result:
default:CARD=NVidia
    HDA NVidia, ALC887 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


aplay-l results:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Try setting the audio device to ALSA:hdmi

---

### Post by nickrout on 2010-02-28
> **perjojek said:**
> The remote control was delivered together with the TC-600 case. Yes, it has a usb transmitter. Here is how I connected it (see the attached jpg and the [techsolo support site]("http://www.techsolo.net/site/support.php?lang=en#target13") > case): 
VCC : VCC
D0- : USB1-
D0+ : USB1+
GND: GND

lsusb
Bus 003 Device 003: ID 1130:6604 Tenx Technology, Inc. 

Is any of them an IR transmitter?

I thought we were talking about an IR receiver In any event the tenx one is your receiver. don't know if this works in linux. you will have to use your google skills :)

---

### Post by nickrout on 2010-02-28
> **perjojek said:**
> In Backend Setup > Capture Cards I selected "DVB DTV capture card (v3.x)". Two problems that I encounter are:
1) I am not able to scann channels (Error parsing parameters)
2) When exiting from Backend setup  I get the following message: "Card 1 (CardDVBInput) is set to start on channel
Please add, which does not exist
Card 2 (CardDVBInput) is set to start on channel
Please add, which does not exist"

so did you see and check the above message about > I got this error (albeit for a DVB-S scan) when I had a character it wasn't expecting in one of the settings entry boxes - in my case it was a '.' in the transponder frequency from SiHa?

---

### Post by nickrout on 2010-02-28
> **perjojek said:**
> blkid generated: 
/dev/sde1: UUID="91b66492-e610-4842-894c-6e0df28f0cb5" TYPE="ext4" 
/dev/sde5: UUID="42b1569a-6558-49f7-9b91-4554ede0661c" TYPE="swap" 

I tired both but without success..

clearly neither of those is a dvd drive. They are your swap partition and an ext4 partition.

Try ```
dmesg|grep -i dvd
``` for further clues.

---

### Post by perjojek on 2010-03-02
> **nickrout said:**
> clearly neither of those is a dvd drive. They are your swap partition and an ext4 partition.

Try ```
dmesg|grep -i dvd
``` for further clues.


mateo@HTPC:~$ dmesg|grep -i dvd
[    1.405889] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB01, max UDMA/100
[    1.411554] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB01 PQ: 0 ANSI: 5
[    1.418726] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[ 4291.990836] UDF-fs INFO UDF: Mounting volume 'DR_HOUSE_DVD1', timestamp 2008/11/04 08:16 (103c)

I changed location of DVD device to: /dev/sr0.  It still does not work. here is the message appended to the log file:

2010-03-02 21:42:49.445 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-03-02 21:42:58.935 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-03-02 21:43:01.846 Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2010-03-02 21:43:01.989 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-03-02 21:44:09.476 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//optical_menu.xml
2010-03-02 21:44:11.330 TV: Attempting to change from None to Watching DVD
libdvdread: Encrypted DVD support unavailable.
libdvdread,ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: DR_HOUSE_DVD1
libdvdnav: DVD Serial Number: 39643a10
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/mateo/.dvdnav/DR_HOUSE_DVD1.map'
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-03-02 21:44:12.281 Failed to open DVD device at /dev/scd0

---

### Post by perjojek on 2010-03-02
> **SiHa said:**
> Should be **/var/log/mythtv/mythfrontend.log**

thx SiHa, I see it

---

### Post by perjojek on 2010-03-02
> **nickrout said:**
> Try setting the audio device to ALSA:hdmi

It do not work with ALSA:hdmi

-03-02 22:15:30.346 Opening audio device 'hdmi'. ch 6(2) sr 44100
2010-03-02 22:15:30.346 Opening ALSA audio device 'hdmi'.
2010-03-02 22:15:30.396 AudioOutput Error: Rate doesn't match (requested 44100Hz, got 48000Hz)
2010-03-02 22:15:30.396 AudioOutput Error: Unable to set ALSA parameters

but works fine with **dev/dsp**.

-03-02 22:11:15.072 Received a remote 'Clear Cache' request
2010-03-02 22:11:19.908 Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2010-03-02 22:11:20.002 Loading menu theme from /usr/share/mythtv/musicmenu.xml
2010-03-02 22:11:20.649 XMLParse: LoadTheme using '/usr/share/mythtv/themes/metallurgy/music-ui.xml'
2010-03-02 22:11:21.183 Opening audio device '/dev/dsp'. ch 6(2) sr 44100
2010-03-02 22:11:21.183 Opening OSS audio device '/dev/dsp'.

as long though as I use a stereo head-set. hooked to the  front panel. AV received does not receive any signal from SPDIF.

---

### Post by perjojek on 2010-03-02
> **SiHa said:**
> Not sure about the rest, but I got this error (albeit for a DVB-S scan) when I had a character it wasn't expecting in one of the settings entry boxes - in my case it was a '.' in the transponder frequency.

I double-checked and I don't see any characters in the "Scan Configuration" window.

---

### Post by perjojek on 2010-03-02
Let me report one more issue. When I start Frontend, after a moment the application crashes. It needs good 30 seconds to start responding again. It may be a minor issue or an indication of a bigger problem.

Starting mythfrontend.real..
2010-03-02 22:50:03.569 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-03-02 22:50:03.569 Using runtime prefix = /usr
2010-03-02 22:50:03.570 Using configuration directory = /home/mateo/.mythtv
2010-03-02 22:50:04.426 Empty LocalHostName.
2010-03-02 22:50:04.426 Using localhost value of HTPC
2010-03-02 22:50:04.437 New DB connection, total: 1
2010-03-02 22:50:04.444 Connected to database 'mythconverg' at host: localhost
2010-03-02 22:50:04.444 Closing DB connection named 'DBManager0'
2010-03-02 22:50:04.453 ScreenSaverX11Private: Gnome screen saver support enabled
2010-03-02 22:50:04.454 DPMS is active.
2010-03-02 22:50:04.456 Primary screen: 0.
2010-03-02 22:50:04.457 Connected to database 'mythconverg' at host: localhost
2010-03-02 22:50:04.459 Using screen 0, 1920x1080 at 0,0
2010-03-02 22:50:04.479 MythUI Image Cache size set to 20971520 bytes
2010-03-02 22:50:04.479 Enabled verbose msgs:  important general
2010-03-02 22:50:04.486 Primary screen: 0.
2010-03-02 22:50:04.486 Using screen 0, 1920x1080 at 0,0
2010-03-02 22:50:04.487 Using theme base resolution of 1280x720
2010-03-02 22:50:04.490 LIRC: Successfully initialized '/dev/lircd' using '/home/mateo/.mythtv/lircrc' config
2010-03-02 22:50:04.490 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mateo/.mythtv/joystickmenurc
2010-03-02 22:50:04.622 Using the Qt painter
2010-03-02 22:50:04.720 Loaded base theme from /usr/share/mythtv/themes/metallurgy/base.xml
2010-03-02 22:50:04.743 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-03-02 22:50:04.768 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-03-02 22:50:04.799 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-02 22:50:04.812 New DB connection, total: 2
2010-03-02 22:50:04.823 Connected to database 'mythconverg' at host: localhost
2010-03-02 22:50:04.939 Desktop video mode: 1920x1080 60.0024 Hz
2010-03-02 22:50:05.031 Registering Internal as a media playback plugin.
2010-03-02 22:50:05.071 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.076 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.090 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.106 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.109 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.117 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.129 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.133 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.141 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.153 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.157 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.165 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.177 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.180 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.189 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-02 22:50:05.193 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-03-02 22:50:05.212 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-03-02 22:50:05.240 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-03-02 22:50:05.247 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-02 22:50:05.268 Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2010-03-02 22:50:05.341 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-03-02 22:50:05.418 Found mainmenu.xml for theme 'metallurgy'
2010-03-02 22:50:05.505 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-02 22:50:05.506 Using protocol version 50
2010-03-02 22:50:05.783 Found a handler - 'MythDVD DVD Media Handler'
2010-03-02 22:50:05.906 TV: Attempting to change from None to Watching DVD
libdvdread: Encrypted DVD support unavailable.
libdvdread,ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: DR_HOUSE_DVD1
libdvdnav: DVD Serial Number: 39643a10
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/mateo/.dvdnav/DR_HOUSE_DVD1.map'
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-03-02 22:50:06.842 Failed to open DVD device at /dev/scd0
2010-03-02 22:50:30.549 TV: Attempting to change from None to Watching WatchingLiveTV
2010-03-02 22:50:30.551 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-02 22:50:30.552 Using protocol version 50
2010-03-02 22:50:30.559 Spawning LiveTV Recorder -- begin
2010-03-02 22:50:30.661 Spawning LiveTV Recorder -- end
2010-03-02 22:50:30.663 GetEntryAt(-1) failed.
2010-03-02 22:50:30.664 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2010-03-02 22:50:30.665 TV Error: HandleStateChange(): LiveTV not successfully started
2010-03-02 22:50:30.665 We have a RingBuffer
2010-03-02 22:50:30.715 TV Error: LiveTV not successfully started
2010-03-02 22:50:30.737 ScreenSaverX11Private: DPMS Deactivated 1
2010-03-02 22:50:30.739 ScreenSaverX11Private: DPMS Reactivated 1
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
2010-03-02 22:50:35.487 Failed to mount /dev/sda.
2010-03-02 22:50:35.495 Found a handler - 'MythGallery Media Handler 1/2'
2010-03-02 22:50:35.513 Loading window theme from /usr/share/mythtv/themes/metallurgy/gallery-ui.xml
2010-03-02 22:50:35.525 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.525 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.527 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.534 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.535 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.536 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.536 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.537 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.537 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.538 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.539 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.539 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.540 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.540 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.540 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.541 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.541 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.541 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.541 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.542 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.542 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.542 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.543 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.543 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.543 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.543 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.544 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.544 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.544 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.545 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.545 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.545 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.545 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.546 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.550 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.550 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.551 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.551 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.551 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.551 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.551 Unable to find image file: gallery/mark.png
2010-03-02 22:50:35.555 Unable to find image file: gallery/mark.png
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2010-03-02 22:52:37.304 Failed to mount /dev/sdd.

---

### Post by tgm4883 on 2010-03-02
Looks like you need to install dvd support from medibuntu. This can be done in Mythbuntu Control Centre

---

### Post by perjojek on 2010-03-04
> **tgm4883 said:**
> Looks like you need to install dvd support from medibuntu. This can be done in Mythbuntu Control Centre

could you please explain how to install dvd support? I don't see such an option in Mythbuntu Control Centre.

---

### Post by tgm4883 on 2010-03-04
> **perjojek said:**
> could you please explain how to install dvd support? I don't see such an option in Mythbuntu Control Centre.

I'm not at home right now, so no screenshot. There should be a section in MCC though for Proprietary codecs

---

### Post by perjojek on 2010-03-11
Guys,
I give up. I am willing to pay for the configuration of the system. It would be best to find an expert in the area of Onsabrück/Germany. Any volonteers?
If this does not work I will unfortunatelly have to consider buying Windows Media Center.

---

### Post by tgm4883 on 2010-03-11
Ok, look at the screenshot. Check 1, then hit apply. Check 2, then hit apply. Check 3 (libdvdcss2) then hit apply

---

### Post by perjojek on 2010-03-12
> **tgm4883 said:**
> Ok, look at the screenshot. Check 1, then hit apply. Check 2, then hit apply. Check 3 (libdvdcss2) then hit apply

Thx tgm4883, I have to admit it was easy. DVD player does work now!

I would appreciate if you could help me with remaining 3 problems:
[FONT=Times New Roman][SIZE=3]1)[/SIZE] [/FONT][FONT=Times New Roman][SIZE=3]7.1 sound card (on-board [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]M5N78-VM[/SIZE][/FONT]]("http://www.asus.com/product.aspx?P_ID=CMQkJloA9dyXDIeS")[FONT=Times New Roman][SIZE=3]) does not work. I can hear music when I hook up a stereo head-set to the front panel. However, my AV-Receiver does not get any signal from the SPDIF port.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2)[/SIZE] [SIZE=3]When scanning channels (backend > Channel Editor) I get the following message: “Error parsing parameters”. I have [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]Mystique CaBiX-C2[/SIZE][/FONT]]("http://translate.google.com/translate?u=http://www.mystique-tv.de/download/cat_view/44-produktpraesentation--product-presentation.html&hl=en&ie=UTF-8&sl=auto&tl=en")[FONT=Times New Roman][SIZE=3] capture card, not sure if it works properly.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3) my remote control (case [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]techsolo TC-600[/SIZE][/FONT]]("http://www.techsolo.net/site/product.php?lang=en&do=show&product_id=263&class_id=34")[FONT=Times New Roman][SIZE=3]) seems not to be supported[/SIZE][/FONT]

---

### Post by nickrout on 2010-03-13
what have you set audio output to in your frontend setup?

what is the output of aplay -L and aplay -l

---

### Post by stanger192 on 2010-03-13
for your remote try this [guide]("https://help.ubuntu.com/community/InstallLirc/Hardy#Adding support for more remotes"). my ir receiver wasnt supported by i was able to add it by following this guide. just make sure you change the lirc version number to the current one and use lirc_mceusb instead of lirc_mceusb2 as the two drivers have been rolled into one.

be sure to forward your ir receiver info to Martin Blatter (martin_a_blatter@yahoo.com) to ensure that the info is contained in future versions

---

### Post by perjojek on 2010-03-13
> **perjojek said:**
> 
[FONT=Times New Roman][SIZE=3]1)[/SIZE] [/FONT][FONT=Times New Roman][SIZE=3]7.1 sound card (on-board [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]M5N78-VM[/SIZE][/FONT]]("http://www.asus.com/product.aspx?P_ID=CMQkJloA9dyXDIeS")[FONT=Times New Roman][SIZE=3]) does not work. I can hear music when I hook up a stereo head-set to the front panel. However, my AV-Receiver does not get any signal from the SPDIF port.[/SIZE][/FONT]

I changed audio output to ALSA: SPDIF. It works as long as long as it is Stereo. It does not work with the 5.1 channels set. Any hints?

---

### Post by perjojek on 2010-03-13
> **nickrout said:**
> what have you set audio output to in your frontend setup?

what is the output of aplay -L and aplay -l

see the attachments

---

### Post by nickrout on 2010-03-13
Have you enabled, in myth, ac3 passthrough to spdif and dts passthrough to spdif?

Have you read ANY instructions?

This wiki page may help

[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

---

### Post by perjojek on 2010-03-13
> **nickrout said:**
> Have you enabled, in myth, ac3 passthrough to spdif and dts passthrough to spdif?

Yes, I have both passthoughs enabled. It does not help.
Thx for the HowTo material . I will look though it tomorrow.

---

### Post by perjojek on 2010-03-13
> **stanger192 said:**
> for your remote try this [guide]("https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes"). my ir receiver wasnt supported by i was able to add it by following this guide. just make sure you change the lirc version number to the current one and use lirc_mceusb instead of lirc_mceusb2 as the two drivers have been rolled into one.

be sure to forward your ir receiver info to Martin Blatter (martin_a_blatter@yahoo.com) to ensure that the info is contained in future versions

I completed steps in the guide. Could you advise, what Remote Control and IR Transmitter should I select in Mythbuntu Control Center?

---

### Post by perjojek on 2010-03-14
> **nickrout said:**
> 
This wiki page may help

[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)


I tested multiple settings from the Tutorial. It may be BIOS problem or a bug reported for ASUS boards (m3n78-em in the Troublleshooting section). I have M4N78-VM. I will keep on investigating.

---

### Post by stanger192 on 2010-03-14
> **perjojek said:**
> I completed steps in the guide. Could you advise, what Remote Control and IR Transmitter should I select in Mythbuntu Control Center?

You set the receiver to lirc_mceusb or a usb media center receiver, not to sure as i did this on xbmc, but there should be something there along those lines


This is the output of dmesg|grep -i lirc

[   16.867604] lirc_dev: IR Remote Control driver registered, major 61
[   16.899644] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   16.899655] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   27.273325] lirc_dev: lirc_register_driver: sample_rate: 0
[   27.279323] lirc_mceusb[2]: Formosa21 eHome Infrared Transceiver on usb3:2
[   27.279463] usbcore: registered new interface driver lirc_mceusb

Before i updated the driver i was just receiving the 16's, i got the messages at 27 after the driver update. If you see 'lirc_mceusb[2]' everything should be working fine.

the comand 'irw' will show you any buttons pressed on you remote to test its all working.

---

### Post by nickrout on 2010-03-15
> **perjojek said:**
> I tested multiple settings from the Tutorial. It may be BIOS problem or a bug reported for ASUS boards (m3n78-em in the Troublleshooting section). I have M4N78-VM. I will keep on investigating.

So what DO you have it set to? All of your audio settings please!

---

### Post by perjojek on 2010-08-29
> **perjojek said:**
> [FONT=Times New Roman][SIZE=3]I have a number of problems with configuring MythTV (Mythbuntu) on my HTPC.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1)[/SIZE] [SIZE=3]my remote control (case [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]techsolo TC-600[/SIZE][/FONT]]("http://www.techsolo.net/site/product.php?lang=en&do=show&product_id=263&class_id=34")[FONT=Times New Roman][SIZE=3]) seems not to be supported[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2)[/SIZE] [SIZE=3]7.1 sound card (on-board [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]M5N78-VM[/SIZE][/FONT]]("http://www.asus.com/product.aspx?P_ID=CMQkJloA9dyXDIeS")[FONT=Times New Roman][SIZE=3]) does not work. I can hear music when I hook up a stereo head-set to the front panel. However, my AV-Receiver does not get any signal from the SPDIF port.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3)[/SIZE] [SIZE=3]When scanning channels (backend > Channel Editor) I get the following message: “Error parsing parameters”. I have [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]Mystique CaBiX-C2[/SIZE][/FONT]]("http://translate.google.com/translate?u=http://www.mystique-tv.de/download/cat_view/44-produktpraesentation--product-presentation.html&hl=en&ie=UTF-8&sl=auto&tl=en")[FONT=Times New Roman][SIZE=3] capture card, not sure if it works properly.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]4)[/SIZE] [SIZE=3]DVD plays neither films nor music. When you select “Play DVD”, the screen displays the background and switches back to the menu window after a second.[/SIZE][/FONT]
 
[FONT=Times New Roman]Please, help me to convince myself (and others) that it is possible to configure Mythbuntu to work decently[/FONT]
 
 
I would like to report a success! After months of struggle I have my HTPC up and running.
 
I resolved most of the problems, i.e. items 1,2 & 4, by installing the latest version of MythTV (0.23).
 
As far as the channel scanning is concerned, some tuner cards do not start the process as lomg as transports are not defined. You need to go to  Channel Editor > Edit Transports > New Transport and define at least one transport manually - e.g. in Germany Frequency 418000000, Symbol Rate 6900000, Modulation QAM-256, Inversion & FEC Auto. This enables the automatic scan.
 
Great thanks to all who supported me.

---

