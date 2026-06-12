---
title: "Why is MythTV so hard to configure? Help please."
date: 2010-01-09
forum: Multimedia Software
---

### Post by Maheriano on 2010-01-09
I've been at this for the last hour. I just put a Hauppage WinTV-TVR-1800 into my machine, rebooted and installed MythTV. I set up the card, the video source and the input as well as configured a few random channels. I click WATCH TV in the menu, it goes to a screen saying, "Please Wait....", then it brings me back to the menu. There's no error, is there some sort of log file I can display for you so you can help me get this working? Thanks.

Here it is run in the terminal:
```
deemar@Chugger:~$ mythfrontend
2010-01-09 20:03:05.636 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-09 20:03:05.663 AudioPulseUtil: Suspend Success
2010-01-09 20:03:05.665 Using runtime prefix = /usr
2010-01-09 20:03:05.665 Using configuration directory = /home/deemar/.mythtv
2010-01-09 20:03:06.445 Empty LocalHostName.
2010-01-09 20:03:06.445 Using localhost value of Chugger
2010-01-09 20:03:06.451 New DB connection, total: 1
2010-01-09 20:03:06.455 Connected to database 'mythconverg' at host: localhost
2010-01-09 20:03:06.455 Closing DB connection named 'DBManager0'
2010-01-09 20:03:06.472 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-09 20:03:06.473 DPMS is active.
2010-01-09 20:03:06.475 Primary screen: 0.
2010-01-09 20:03:06.475 Connected to database 'mythconverg' at host: localhost
2010-01-09 20:03:06.476 Using screen 0, 1280x720 at 0,0
2010-01-09 20:03:06.501 MythUI Image Cache size set to 20971520 bytes
2010-01-09 20:03:06.502 Enabled verbose msgs:  important general
2010-01-09 20:03:06.506 Primary screen: 0.
2010-01-09 20:03:06.507 Using screen 0, 1280x720 at 0,0
2010-01-09 20:03:06.508 Using theme base resolution of 1280x720
2010-01-09 20:03:06.512 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-01-09 20:03:06.512 JoystickMenuThread Error: Joystick disabled - Failed to read /home/deemar/.mythtv/joystickmenurc
2010-01-09 20:03:06.630 Using the Qt painter
2010-01-09 20:03:06.783 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-01-09 20:03:06.788 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-01-09 20:03:06.850 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-09 20:03:06.850 Unable to load window 'backgroundwindow' from base
2010-01-09 20:03:06.855 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-09 20:03:06.856 New DB connection, total: 2
2010-01-09 20:03:06.856 Connected to database 'mythconverg' at host: localhost
2010-01-09 20:03:07.071 Desktop video mode: 1280x720 60.0024 Hz
2010-01-09 20:03:07.218 Registering Internal as a media playback plugin.
2010-01-09 20:03:07.219 No plugins directory /usr/lib/mythtv/plugins
2010-01-09 20:03:07.237 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.243 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.248 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.267 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.272 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.278 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.298 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.303 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.309 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.328 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.333 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.338 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.357 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.362 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.368 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 20:03:07.383 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-01-09 20:03:07.433 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-09 20:03:07.450 Found mainmenu.xml for theme 'Mythbuntu'
2010-01-09 20:03:08.180 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 20:03:08.181 Using protocol version 50
2010-01-09 20:03:10.584 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-09 20:03:10.585 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 20:03:10.585 Using protocol version 50
2010-01-09 20:03:10.642 Spawning LiveTV Recorder -- begin
2010-01-09 20:03:15.278 Spawning LiveTV Recorder -- end
2010-01-09 20:03:15.279 GetEntryAt(-1) failed.
2010-01-09 20:03:15.279 EntryToProgram(0@Wed Dec 31 17:00:00 1969) failed to get pginfo
2010-01-09 20:03:15.279 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-09 20:03:15.280 We have a RingBuffer
2010-01-09 20:03:15.330 TV Error: LiveTV not successfully started
2010-01-09 20:03:15.351 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-09 20:03:15.352 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-09 20:03:19.579 AudioPulseUtil: Resume Success
2010-01-09 20:03:19.580 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
```

---

### Post by Maheriano on 2010-01-11
Nobody?

---

### Post by nacho32 on 2010-01-11
said the same thing, try Kaffine I think it works pretty good as far as a TV tunner program for Linux, But still behind Windows when it comes to TV tuner 3rd party programs,

---

### Post by Maheriano on 2010-01-11
Sorry, it's a WinTV-HVR-1800, not a TVR. I checked the Hauppage website, they say any of their WinTV cards will work in MythTV. I tried Kaffeine but that didn't recognize the card.

---

### Post by HappyFeet on 2010-01-11
Last time I checked the 1800 is not natively supported.

Edit: after checking Hauppauge's website, it appears it is supported. But a friend of mine had this card and had no luck (I even tried for a while) getting it going. He now uses Vista. :(

Post the output of
```
lspci
```

---

### Post by ICMTM on 2010-01-12
I had the same problem.  The error message I was getting was something about the channel being set to start at "please add" so in the back end I went to 4. Input Connectors>Selected my input connector, and then chose a starting channel.  I hope this helps you as well.

---

### Post by singedwings on 2010-01-12
You are getting the "**2010-01-09 20:03:15.279 GetEntryAt(-1) failed**" in your terminal.

This is usually a permissions error. Have you changed the default storage directories in the backend? If you have myth probably does not have permission to write to the new directory.

---

### Post by Maheriano on 2010-01-12
> **HappyFeet said:**
> Last time I checked the 1800 is not natively supported.

Edit: after checking Hauppauge's website, it appears it is supported. But a friend of mine had this card and had no luck (I even tried for a while) getting it going. He now uses Vista. :(

Post the output of
```
lspci
```

```
deemar@Chugger:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f)
05:06.0 Serial controller: Lava Computer mfg Inc Lava DSerial-PCI Port A
05:06.1 Serial controller: Lava Computer mfg Inc Lava DSerial-PCI Port B
05:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
05:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

---

### Post by Maheriano on 2010-01-12
> **singedwings said:**
> You are getting the "**2010-01-09 20:03:15.279 GetEntryAt(-1) failed**" in your terminal.

This is usually a permissions error. Have you changed the default storage directories in the backend? If you have myth probably does not have permission to write to the new directory.

I just checked the storage directories and I know I haven't even entered that area of the setup before so they're still all set to their defaults. I never changed any of them.

Does this help you determine permissions?

```
deemar@Chugger:/var/lib/mythtv$ ls -l
total 36
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 banners
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 coverart
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 db_backups
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 fanart
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 livetv
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 recordings
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 screenshots
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 trailers
drwxrwsr-x 2 mythtv mythtv 4096 2010-01-12 21:09 videos

```

```
deemar@Chugger:/var/lib/mythtv$ id deemar
uid=1000(deemar) gid=1000(deemar) groups=1000(deemar),4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),124(mythtv)

```

---

### Post by Maheriano on 2010-01-17
Can anyone help?

---

### Post by sports.car.guy on 2010-01-17
Well there are a couple considerations with this card. Look at this page.

[http://www.linuxtv.org/wiki/index.php/Hauppauge](http://www.linuxtv.org/wiki/index.php/Hauppauge)

It all depends on which 1800 model you have for starters and it having support.

Refer to this page if it is a supported card:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

Here is an section from the page:

**Note**: I have spoken to support in the MythTV-users IRC channel and they say the driver support / MythTV combination just doesn't work, and that the driver author is aware of the issue. I really wanted analog capture to work (and I may try messing around with it) but the "official" word is that MythTV currently doesn't support this card for analog capturing... --[Jherm]("http://www.linuxtv.org/wiki/index.php?title=User:Jherm&action=edit&redlink=1") 00:20, 8 November 2009 (UTC) 
 ** Firmware**

 Download the firmware and all the files for cx23885 from [HVR-1800 Firmware]("http://steventoth.net/linux/hvr1800/") (it is also a good idea to keep checking for new firmware updates from this page). Run the .sh script and it will make two files v4l-cx23885-avcore-01.fw and v4l-cx23885-enc.fw. Copy these two files into /lib/firmware/ (not /lib/firmware/2.6.26-1-amd64 as stated by the script). 







Not only is the card not supported with MythTV if it is the version that is supported by Linux, you also need to have firmware too. I hope this helps you out.

---

### Post by friesgaard on 2010-01-17
I had the same problem with a Hauppauge 500mce pvr, the video card must be set up correctly in Mythbackend. 

Delete all cards, add a new with ivtv driver. 
try to run the frontend again

---

### Post by sports.car.guy on 2010-01-17
> **friesgaard said:**
> I had the same problem with a Hauppauge 500mce pvr, the video card must be set up correctly in Mythbackend. 

Delete all cards, add a new with ivtv driver. 
try to run the frontend again


It is not the same type of issue. Refer to my post prior to this one. It is a driver support issue that MythTV has with the card or it is a model not supported. Either way neither will work wirh MythTV at all.

---

### Post by Maheriano on 2010-01-22
> **sports.car.guy said:**
>  Download the firmware and all the files for cx23885 from [HVR-1800 Firmware]("http://steventoth.net/linux/hvr1800/") (it is also a good idea to keep checking for new firmware updates from this page). Run the .sh script and it will make two files v4l-cx23885-avcore-01.fw and v4l-cx23885-enc.fw. Copy these two files into /lib/firmware/ (not /lib/firmware/2.6.26-1-amd64 as stated by the script). 
You didn't fix my issue but you helped me figure out what's wrong. With this firmware download I was able to add my card as a DVB device instead of the previous TV devices and this allowed me to scan for channels on the ATSC frequency. So I realize now that the only inputs on the card that were being picked up were the TV/composite/S-video inputs and not the actual tuner itself. But this still doesn't help me because here in Canada we're still entirely NTSC and we won't have any ATSC channels until this summer.

---

