---
title: "Hauppage WinTV pvr 150 no /dev/video0"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by wexx on 2007-04-02
Ok I know this might seem redundant, I wouldn't call myself a noob with linux.  I followed a ton of guides on how to install mythTV, tvTime, etc.  I have in all about 3 different apps, and vlc which is pretty much the best thing since sliced bread.  

Problem is this.  I have gone many tutorials guides wikis etc and can't ever get to the end of one of them successfully.  It is always at the part mplayer /dev/video0 .

the reason is that I don't have /dev/video0 nor do i have /dev/ivtv0

I have a Win TV pvr 150 Hauppage card.  It is pretty much brand new and I know it works.  I have to boot into my windows box in order to watch tv at school.  I could really use help here.  I tried modprobing the ivtv drivers i am up to date.  I once upon a time had dev/video0 but a ubuntu kernel update or possibly after a reboot took it away.  

Here is my dmesg:

[17179593.592000] ivtv:  ==================== START INIT IVTV ====================
[17179593.592000] ivtv:  version 0.7.4 (tagged release) loading
[17179593.592000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179593.592000] ivtv:  In case of problems please include the debug info between
[17179593.592000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179593.592000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179593.592000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179593.592000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 22 (level, low) -> IRQ 66
[17179593.608000] usbcore: registered new driver hiddev
[17179593.644000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /class/input/input2
[17179593.644000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:1d.1-1
[17179593.644000] usbcore: registered new driver usbhid
[17179593.644000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.672000] tveeprom 0-0050: Hauppauge model 26132, rev F1B2, serial# 9900479
[17179593.672000] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[17179593.672000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179593.672000] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[17179593.672000] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[17179593.672000] tveeprom 0-0050: has no radio, has IR remote
[17179593.784000] nvidia: module license 'NVIDIA' taints kernel.
[17179594.036000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC602
[17179594.036000] usbcore: registered new driver usblp
[17179594.036000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179594.068000] usbcore: registered new driver libusual
[17179594.072000] ts: Compaq touchscreen protocol output
[17179594.124000] Initializing USB Mass Storage driver...
[17179594.124000] scsi6 : SCSI emulation for USB Mass Storage devices
[17179594.124000] usbcore: registered new driver usb-storage
[17179594.124000] USB Mass Storage support registered.
[17179594.124000] usb-storage: device found at 3
[17179594.124000] usb-storage: waiting for device to settle before scanning
[17179594.148000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179594.384000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17179595.480000] skge eth0: Link is up at 10 Mbps, half duplex, flow control none
[17179597.608000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179597.696000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179598.372000] ivtv0: retry: file loaded was not v4l-cx2341x-enc.fw (expected size 376836, got 262144)
[17179598.376000] ivtv0: retry: file loaded was not v4l-cx2341x-enc.fw (expected size 376836, got 262144)
[17179598.380000] ivtv0: retry: file loaded was not v4l-cx2341x-enc.fw (expected size 376836, got 262144)
[17179598.380000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw (must be 376836 bytes)
[17179598.380000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179598.380000] ivtv0 warning: failed loading encoder firmware
[17179598.380000] ivtv0 warning: Error loading firmware -3!
[17179598.380000] ivtv0: Error -3 initializing firmware.
[17179598.380000] ivtv0: Error -12 on initialization
[17179598.380000] ivtv: probe of 0000:05:01.0 failed with error -12
[17179598.380000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179598.380000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179598.380000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[17179598.380000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 21 (level, low) -> IRQ 58
[17179598.400000] NET: Registered protocol family 10
[17179598.400000] lo: Disabled Privacy Extensions
[17179598.400000] IPv6 over IPv4 tunneling driver
[17179598.408000] ivtv:  ====================  END INIT IVTV  ====================





If you need any other information from me let me know I will gladly supply you with it.  I'm just so close and need the extra help from some of you Ubuntu veterans :)

---

### Post by superm1 on 2007-04-02
It sounds as though your firmware is improperly installed, or you have an old version of it.

Which guide(s) have you followed?

This is the one that is the supported method in edgy:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

What is your version of the ivtv packages?
```
dpkg -l | grep ivtv
```

---

### Post by wexx on 2007-04-02
OMG thanks for a response I have been trying to resolve this issue with tv in linux for almost 2 months.  Pretty much since Christmas time.  Thanks lots ahead of time even if your advice doesn't work.

Yeah I actually used a guide like that it might have been that particular one around my first couple attempts.  It was one to do mythTV which is my ultimate goal on this PC.  I will surely check it out again and see if I see anything I haven't done.  In the mean time here is the dpkg

```

ii  ivtv-firmware                              1.18.21.22254                        firmware for use with the ivtv kernel driver
ii  ivtv-modules-2.6.17-10-generic             0.7.0-2+2.6.17.1-10.34               ivtv Linux kernel module (0.6 branch)
ii  ivtv-modules-2.6.17-11-generic             0.7.4-0ubuntu0ivtv1+2.6.17.1-11.35   ivtv Linux kernel module (0.7 branch)
ii  ivtv-source                                0.7.4-0ubuntu0ivtv1                  source for ivtv drivers (0.7 branch)
ii  ivtv-utils                                 0.7.4-0ubuntu0ivtv1                  utilities for use with the ivtv kernel driver
ii  libvideo-ivtv-perl                         0.13-3                               Perl extension for using V4l2 in the ivtv perl scripts

```

---

### Post by superm1 on 2007-04-03
Okay, you have a very old version of the firmware.  The versioning scheme has since then changed.  I hadn't anticipated anyone having this old of firmware when trying to use the driver.

Assuming that you have the ivtv repository added to ivtv, you should be able to 

```
sudo apt-get remove --purge ivtv-firmware
```

followed by

```
sudo apt-get install ivtv-firmware.
```

It appears the ivtv site is down momentarily, however.  I'm attaching the firmware that is normally hosted there (I maintain that repository)
Purge your other version and install this with dpkg
```
sudo dpkg -i ivtv-firmware*
```

---

### Post by wexx on 2007-04-03
Cool, thanks for the help I'm going to take a look at that solution tonight while I am working on some concurrency homework.  I will let you know how it goes. Hopefully it really is just my firmware being outdated.  I could have sworn that I saw an IVTV firmware update come through synaptic though.  Was I imagining things again?  If that is the case could I also have a problem with updates taking place correctly? 

I don't need my computer snowballing to a death :-/

---

### Post by superm1 on 2007-04-03
It's possible that you aren't crazy and the update showed up, but that it wasn't able to download due to ivtv's website being down.  It appears to still be down though.  I sent axel an email, but haven't heard back as of yet.  I'm fairly confident that once you install this version of the firmware however, things will be fine.

---

### Post by wexx on 2007-04-04
Ok, I tried out the steps and code you laid out for me.  Followed them even tried them twice to make sure it wasn't me.  I did the first code snippet followed by the second downloaded that .deb file then cd to the directory it was in and ran the last command.  Noticed I had no dev/video0.  I then went on the walk through of the installation that you linked to me.  Started that right after the part where you start downloading the ivtv drivers from ivtvdriver.org went through and got completely to the end with still no dev/video0, I heard rumor that i should also look for an ivtv0 but that wasn't existent either.  

since you said my packages were out of date I took the liberty of doing another 
```

dpkg -l |grep ivtv

```

compared the two and they still are identical.  I guess I must not be following your steps right.  I also downloaded your file and opened it with the auto installer to make sure it was getting in there.  Still nothing.:confused:

---

### Post by superm1 on 2007-04-04
Okay,

The site that hosts this deb is back up, so do it this way.  Make sure that you have this line in your /etc/apt/sources.list.
```
deb http://dl.ivtvdriver.org/ubuntu edgy all
```
Now considering your on a desktop install, i'll walk you through the GUI method of doing this.
Open up synaptic.  Search for ivtv.  You should see entries for ivtv-source, ivtv-utils, and ivtv-firmware.  What you will need to do is right click ivtv-firmware and choose to "Completely Remove" it.  Apply this step.  Now click the button to reload the package lists.  Search for ivtv again, and you should see a different version of ivtv-firmware available to you.  Go ahead and install it.

Now this version and all versions hosted on this repository will require you to accept a license.  If you haven't done this previously, you will get a popup like the one I am attaching (license_agreement.png).

You can make sure you have the right version installed now by searching ivtv once more.  You should see this listed (see attachment version_installed.png)

---

### Post by wexx on 2007-04-04
Hey i have my video0 back.  Thanks.  I did the test to see what was going on and if it found everything ok.

```

mplayer /dev/video0

``` 

got a window with a bunch of static in there.

I tried to open the capture device with vlc and i made sure it said the capture device was at /dev/video0 and I didn't see anything but static.  I don't know if its on the wrong channel or what. I do have the remote it would be very handy to have that working.  But I will be happy with just having tv ability and being able to change the channel through an application.  If you know of a really good tutorial for myth tv or tvtime (currently just gives me a blue screen).  LIke i said as long as i have tv with an easy way to change the channel besides doing it from a command prompt i'd be fairly happy I know the remote has to do with lirc modules being loaded. 

Yay for progress:)

---

### Post by superm1 on 2007-04-04
Tvtime isn't supported.

As for mythtv,
[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV) 
are the ubuntu guides.

---

### Post by wexx on 2007-04-05
Thanks.  I took a look at that guide and started following the steps to getting the front-end desktop set up .  I read the start page as well and I thought that would be the best solution for me.  However, I don't exactly know what comes with mythTV.  No matter what you get front-end or back-end you still get the ability to pause, rewind, record, live TV right?  

Anyway I went through the install listed on this page

[https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop)

and made it to the last command and when I starteded the frontend i got a bunch of errors and then the frontend asking me to choose a language and such.  Below are some screenshot of the choose language thing I'm getting and also what is coming up in my terminal when I run the command 
```

mythfrontend

```

What the errors look like it seems to repeat a bunch of times with the same thing this is just about half of it.  Then it starts the choose language part.
```

 mythfrontend
2007-04-05 17:15:28.793 Using runtime prefix = /usr
2007-04-05 17:15:28.822 Gnome-Screensaver support enabled
2007-04-05 17:15:28.823 DPMS is active.
2007-04-05 17:15:28.953 New DB connection, total: 1
2007-04-05 17:15:28.981 Unable to connect to database!
2007-04-05 17:15:28.981 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.036 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.093 Unable to connect to database!
2007-04-05 17:15:29.093 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.149 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.205 Database not open while trying to load setting: GuiVidModeResolution
2007-04-05 17:15:29.206 Unable to connect to database!
2007-04-05 17:15:29.206 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.262 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.314 Database not open while trying to load setting: GuiVidModeWidth
2007-04-05 17:15:29.314 Unable to connect to database!
2007-04-05 17:15:29.314 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.367 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.419 Database not open while trying to load setting: GuiVidModeHeight
2007-04-05 17:15:29.420 Unable to connect to database!
2007-04-05 17:15:29.420 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

```

once I finish by clicking the button nothing happens and i get this message in my terminal
```

2007-04-05 17:21:46.519 Failed to init MythContext, exiting.
wexx@blackbox:~$ 

```

---

### Post by superm1 on 2007-04-05
> **wexx said:**
> Thanks.  I took a look at that guide and started following the steps to getting the front-end desktop set up .  I read the start page as well and I thought that would be the best solution for me.  However, I don't exactly know what comes with mythTV.  No matter what you get front-end or back-end you still get the ability to pause, rewind, record, live TV right?  

Anyway I went through the install listed on this page

[https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop)

and made it to the last command and when I starteded the frontend i got a bunch of errors and then the frontend asking me to choose a language and such.  Below are some screenshot of the choose language thing I'm getting and also what is coming up in my terminal when I run the command 
```

mythfrontend

```What the errors look like it seems to repeat a bunch of times with the same thing this is just about half of it.  Then it starts the choose language part.
```

 mythfrontend
2007-04-05 17:15:28.793 Using runtime prefix = /usr
2007-04-05 17:15:28.822 Gnome-Screensaver support enabled
2007-04-05 17:15:28.823 DPMS is active.
2007-04-05 17:15:28.953 New DB connection, total: 1
2007-04-05 17:15:28.981 Unable to connect to database!
2007-04-05 17:15:28.981 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.036 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.093 Unable to connect to database!
2007-04-05 17:15:29.093 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.149 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.205 Database not open while trying to load setting: GuiVidModeResolution
2007-04-05 17:15:29.206 Unable to connect to database!
2007-04-05 17:15:29.206 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.262 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.314 Database not open while trying to load setting: GuiVidModeWidth
2007-04-05 17:15:29.314 Unable to connect to database!
2007-04-05 17:15:29.314 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.367 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.419 Database not open while trying to load setting: GuiVidModeHeight
2007-04-05 17:15:29.420 Unable to connect to database!
2007-04-05 17:15:29.420 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

```once I finish by clicking the button nothing happens and i get this message in my terminal
```

2007-04-05 17:21:46.519 Failed to init MythContext, exiting.
wexx@blackbox:~$ 

```
Hi Wexx,

It appears you are mixing up which passwords are supposed to be placed here.  Provided you didn't change any passwords for mysql settings during installation and you properly added yourself to the mythtv group, the defaults were acceptable.

Double check that you can read /etc/mythtv/mysql.txt.
If so, then remove your ~/.mythtv directory and start the frontend again.  Just hit okay at the password screen and things should move along smoothly (hopefully :))

---

### Post by superm1 on 2007-04-05
> **wexx said:**
> Thanks.  I took a look at that guide and started following the steps to getting the front-end desktop set up .  I read the start page as well and I thought that would be the best solution for me.  However, I don't exactly know what comes with mythTV.  No matter what you get front-end or back-end you still get the ability to pause, rewind, record, live TV right?  

Anyway I went through the install listed on this page

[https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop)

and made it to the last command and when I starteded the frontend i got a bunch of errors and then the frontend asking me to choose a language and such.  Below are some screenshot of the choose language thing I'm getting and also what is coming up in my terminal when I run the command 
```

mythfrontend

```What the errors look like it seems to repeat a bunch of times with the same thing this is just about half of it.  Then it starts the choose language part.
```

 mythfrontend
2007-04-05 17:15:28.793 Using runtime prefix = /usr
2007-04-05 17:15:28.822 Gnome-Screensaver support enabled
2007-04-05 17:15:28.823 DPMS is active.
2007-04-05 17:15:28.953 New DB connection, total: 1
2007-04-05 17:15:28.981 Unable to connect to database!
2007-04-05 17:15:28.981 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.036 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.093 Unable to connect to database!
2007-04-05 17:15:29.093 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.149 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.205 Database not open while trying to load setting: GuiVidModeResolution
2007-04-05 17:15:29.206 Unable to connect to database!
2007-04-05 17:15:29.206 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.262 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.314 Database not open while trying to load setting: GuiVidModeWidth
2007-04-05 17:15:29.314 Unable to connect to database!
2007-04-05 17:15:29.314 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-05 17:15:29.367 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-05 17:15:29.419 Database not open while trying to load setting: GuiVidModeHeight
2007-04-05 17:15:29.420 Unable to connect to database!
2007-04-05 17:15:29.420 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'wexx'@'localhost' (using password: YES)

```once I finish by clicking the button nothing happens and i get this message in my terminal
```

2007-04-05 17:21:46.519 Failed to init MythContext, exiting.
wexx@blackbox:~$ 

```
Wexx,

An even larger issuer here - you need to follow one of the pages that sets up a backend along with a frontend.  You need both for a first myth machine in a network.
This would be good for you: [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

---

### Post by wexx on 2007-05-08
Wow, thanks Superm1 i finally have tv in linux.  I officially dont really have a need for windows anymore.  Tv works along with the channel guide recording etc.  I know it has been awhile since my last post but I wanted to wrap this up and tell anyone else who might have read this that I successfuly fixed the problem and all works well.. All there is to do now is to get the remote working that comes with the 150 pvr.  Well that and figuring out how to resize the window in an easier fashion rather than typing in the numbers every time in the appearances section.


Once again THANKS :-D 


Time to relax and watch some good old mind rotting tele :popcorn:

---

### Post by Loafy on 2007-09-29
Just thought that I'd add my $.02 on the PVR-150 and no /dev/video0 issue.

I had the same problem with no /dev/video0 on 2.6.17-12-generic but found it worked fine on  2.6.17-11-generic. After much searching I found superm1's guide to ivtv on Edgy: [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy) 

this worked great for me and is now a bookmark on my system.  thanks superm1 !

---

