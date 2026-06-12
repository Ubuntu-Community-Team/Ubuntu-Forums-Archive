---
title: "Could not get inputs for the capturecard. bind video sources to your card's inputs"
date: 2009-10-13
forum: Mythbuntu
---

### Post by broozm on 2009-10-13
Trying out 9.10 with a Hauppauge WinTV Nova-T 500 PCI - almost working after following the steps here. [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)
:)...

but I get:
"mythtv is using all inputs but there are no active recordings"

The backend log looks like this

2009-10-14 11:49:29.216 mythbackend version: trunk [22304] [www.mythtv.org](www.mythtv.org)
2009-10-14 11:49:29.284 Using runtime prefix = /usr
2009-10-14 11:49:29.343 Using configuration directory = /home/mythtv/.mythtv
2009-10-14 11:49:29.393 Empty LocalHostName.
2009-10-14 11:49:29.434 Using localhost value of bm-desktop
2009-10-14 11:49:29.483 New DB connection, total: 1
2009-10-14 11:49:29.530 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:49:29.568 Closing DB connection named 'DBManager0'
2009-10-14 11:49:29.611 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:49:29.656 Current MythTV Schema Version (DBSchemaVer): 1244
2009-10-14 11:49:29.696 MythBackend: Starting up as the master server.
2009-10-14 11:49:29.740 New DB connection, total: 2
2009-10-14 11:49:29.778 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:49:29.824 TVRec(6) Error: Problem finding starting channel, setting to default of '3'.
2009-10-14 11:49:29.881 ChannelBase(6) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-10-14 11:49:29.922 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2009-10-14 11:49:29.982 ChannelBase(7) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-10-14 11:49:30.020 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2009-10-14 11:49:30.065 New DB connection, total: 3
2009-10-14 11:49:30.130 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:49:30.145 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-14 11:49:30.229 Main::Registering HttpStatus Extension
2009-10-14 11:49:30.279 Enabled verbose msgs:  important general
2009-10-14 11:49:30.332 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-14 11:50:50.072 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min


and the front end:

Starting mythfrontend.real..
2009-10-14 11:42:59.733 mythfrontend version: trunk [22304] [www.mythtv.org](www.mythtv.org)
2009-10-14 11:42:59.733 Using runtime prefix = /usr
2009-10-14 11:42:59.733 Using configuration directory = /home/bm/.mythtv
2009-10-14 11:43:00.587 Empty LocalHostName.
2009-10-14 11:43:00.588 Using localhost value of bm-desktop
2009-10-14 11:43:00.599 New DB connection, total: 1
2009-10-14 11:43:00.606 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:43:00.607 Closing DB connection named 'DBManager0'
2009-10-14 11:43:00.626 ScreenSaverX11Private: Gnome screen saver support enabled
2009-10-14 11:43:00.627 DPMS is active.
2009-10-14 11:43:00.630 Primary screen: 0.
2009-10-14 11:43:00.631 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:43:00.633 Using screen 0, 1680x1050 at 0,0
2009-10-14 11:43:00.657 MythUI Image Cache size set to 20971520 bytes
2009-10-14 11:43:00.658 Enabled verbose msgs:  important general
2009-10-14 11:43:00.668 Primary screen: 0.
2009-10-14 11:43:00.669 Using screen 0, 1680x1050 at 0,0
2009-10-14 11:43:00.671 Using theme base resolution of 1280x720
2009-10-14 11:43:00.682 LIRC: Successfully initialized '/dev/lircd' using '/home/bm/.mythtv/lircrc' config
2009-10-14 11:43:00.683 JoystickMenuThread Error: Joystick disabled - Failed to read /home/bm/.mythtv/joystickmenurc
2009-10-14 11:43:00.958 Using the Qt painter
2009-10-14 11:43:01.035 Loading base theme from /usr/share/mythtv/themes/Mythbuntu-9.10/base.xml
2009-10-14 11:43:01.040 Loading base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-10-14 11:43:01.045 Loading base theme from /usr/share/mythtv/themes/default/base.xml
2009-10-14 11:43:01.046 Unable to load window 'backgroundwindow' from base
2009-10-14 11:43:01.049 Current MythTV Schema Version (DBSchemaVer): 1244
2009-10-14 11:43:01.229 Desktop video mode: 1680x1050 59.9556 Hz
2009-10-14 11:43:01.351 Registering Internal as a media playback plugin.
2009-10-14 11:43:01.408 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.410 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.416 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.423 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.426 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.430 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-10-14 11:43:01.434 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-14 11:43:01.451 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-10-14 11:43:01.483 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-10-14 11:43:01.494 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-10-14 11:43:01.553 Loading window theme from /usr/share/mythtv/themes/Mythbuntu-9.10/menu-ui.xml
2009-10-14 11:43:01.564 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-10-14 11:43:01.565 Found mainmenu.xml for theme 'Mythbuntu-9.10'
2009-10-14 11:43:02.239 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-10-14 11:43:02.240 Using protocol version 50
2009-10-14 11:43:05.450 New DB connection, total: 2
2009-10-14 11:43:05.451 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:43:13.153 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-10-14 11:43:15.627 Loading window theme from /usr/share/mythtv/themes/Mythbuntu-9.10/gallery-ui.xml
2009-10-14 11:43:18.071 New DB connection, total: 3
2009-10-14 11:43:18.072 Connected to database 'mythconverg' at host: localhost
2009-10-14 11:43:18.095 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2009-10-14 11:43:18.123 XMLParse: LoadTheme using '/usr/share/mythtv/themes/Mythbuntu-9.10/music-ui.xml'
2009-10-14 11:43:34.956 Deleting UPnP client...


and the devices seem ok:

bm@bm-desktop:/var/log/mythtv$ dmesg | grep -i dvb
[    6.821936] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    6.821942] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    7.069635] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.796028] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[    7.796076] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    7.797633] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[    8.023841] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    8.200499] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.200731] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[    8.340654] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    8.532376] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb2/2-1/input/input6
[    8.532417] dvb-usb: schedule remote query interval to 50 msecs.
[    8.532420] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[    8.532573] usbcore: registered new interface driver dvb_usb_dib0700
bm@bm-desktop:/var/log/mythtv$ 


TIA

---

### Post by michaelb001 on 2009-10-30
I have the exact same problem. The TV Card Nova T 500 is working for example with vlc but not mythtv. I am getting the same error messages as above.

---

### Post by ian_hawdon on 2009-11-09
I get the same problem on my Nova-T 500 PCI on Karmic, a temporary work around is to open the backend setup and then close it again! Myth works fine after that until the next reboot!

I am using the 1.20 version of the firmware, and a self compiled version of the v4l-dvb package (to get the IR control to work!)

Btw, I upgraded from Jaunty, did anyone have this issue from a clean install, or have we all upgraded?

---

### Post by michaelb001 on 2009-11-10
I did not set my Video Sources right in myttv-setup. Now the tv-card works fine.

---

