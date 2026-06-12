---
title: "no live tv or replay on live cd"
date: 2009-09-06
forum: Mythbuntu
---

### Post by benlyboy on 2009-09-06
I'm in the middle of building my first mythbox. I am still getting the parts together that I intend to use for my system. so I have put together a system using an old pc I had laying around here use as a test rig, and it's working great. 

My question is this, last night I decided to us the live CD as another front end on another pc.
I changed the ip address and set up a password for the backend, then tryed it. At first it seemed work. i can see my tv guide and even the programs that have been recorded. when you highlight one of these programs you can even see it playing in the little window at the bottom of the screen. I can even set up a recording and it will record.

But if I click on a recording to watch it I get a message that tells me something like "the file of this recording can not be found" . and if I try to watch live tv I just get a blue screen (if I take a look at the backend system info why watching tv it shows one tuner being watched.

any ideas ?

---

### Post by williammanda on 2009-09-06
Check the ip addresses for the master backend and the slave backend on both the backends and the frontends. Make sure to use the ip address and not the default "localhost".
Thanks

---

### Post by benlyboy on 2009-09-06
ok I'm new to all this so bare with me. 
I have changed both ip address on the mythbox backend, but are you saying that you have to do this to the live cd as well?
I didn't think it had a backend...?

---

### Post by williammanda on 2009-09-06
Yes check the frontend using the live cd. The frontend has to know the master backend ip address.
Thanks

---

### Post by benlyboy on 2009-09-06
OH ok yes, I know it Knows where the back end is. As I said I can see my guide and all my recording. It.s just I can't play them.
I can even see them playing in the little screen on the page where the recordings are listed. I can also set up a recording, and can later watch it on the main frontend.

The only thing I cant do is watch tv or recordings.

To me it seems funny that it says it can't find a file that it has to have found, to have played on the little screen at the bottom of the recording list page.

---

### Post by sawbuck on 2009-09-12
Briefly, I have a frontend/backend setup with Mythbuntu 9.04 that I have a sample recording on and a networked box setup with Mythbuntu 9.04 live CD inserted.  I have been able to connect to the FE/BE box using the Live CD and can watch Live TV which is actually quite good.  Hwever, when I try to watch the sample recording on th FE box itt goes thriugh the same sort of screens I would on the FE/BE box right up to the point of watching then it shows the error message below.


The error says:

[Title of recording shows up fine]

"The file for this recording can not be found"

I can actually see the animated thumbnail video playing fine - just no file access when I hit enter, arrow or any selecting key..

I.ve searched through the posts here but haven't found a solution.  Any ideas?

---

### Post by sawbuck on 2009-09-12
> **benlyboy said:**
> OH ok yes, I know it Knows where the back end is. As I said I can see my guide and all my recording. It.s just I can't play them.
I can even see them playing in the little screen on the page where the recordings are listed. I can also set up a recording, and can later watch it on the main frontend.

The only thing I cant do is watch tv or recordings.

To me it seems funny that it says it can't find a file that it has to have found, to have played on the little screen at the bottom of the recording list page.

Hi - Looks like a similar problem that I see.  Didn't see this post in my original search so I posted a similar complaint.  I can watch Live TV, fine and as you state, see all the info for my sample recording but although the thumbnail plays fine I get the same error message that it "can not find the file for he recording".  Sumpin' ain't right....  However, on the frontend/Backend all is well.

If you find a lolution please post.  I'll do likewise here.

---

### Post by benlyboy on 2009-09-12
ok if I find an answer I will let you know ...

I am wondering if it might be some kinda hardware incompatibility I need to try the live disk on another system some time.

---

### Post by tgm4883 on 2009-09-12
#1 problem when asking for help. Forgetting the logs. I can take a random stab in the dark, but trust me, logs will get me much closer.

Run mythbuntu-log-grabber and either paste them here, or paste the link from pastebin

---

### Post by sawbuck on 2009-09-12
Well if was an easy fix.  I spent a lot more time looking for similar issues and fouind one when I searched on the exact error phrase "The file for this recording can not be found".  A poster had said both boxes needed to be in teh same "Time Zone".  Makes sense but I didn't even look at that when the Live CD for Mythbuntu 9.04 opened on the desktop.  But setting "Time and Date" from the Applications->System menu on the Live CD I was able to see the recordings normally.

---

### Post by sawbuck on 2009-09-12
> **tgm4883 said:**
> #1 problem when asking for help. Forgetting the logs. I can take a random stab in the dark, but trust me, logs will get me much closer.

Run mythbuntu-log-grabber and either paste them here, or paste the link from pastebin

Sorry about no logs.  I'm really new to linux and forum processes but expect to learn.  Frankly, never polled a log but will start doing that.  

Thanks for putting my post in its proper place....

---

### Post by skskarda on 2009-09-12
I am having the same problem.  I am an experienced ubuntu user.  I recently updated my frontend.  I have the exact same problem.  Frontend can see the recordings, play thumbnails, but when I go to play I get the file for the recording can not be found.

Log from mythfrontend:

> 2009-09-12 19:16:26.300 ProgramInfo, Error: GetPlaybackURL: '1091_20090912070000.mpg' should be local, but it can not be found.
2009-09-12 19:16:26.301 PlaybackBox::play(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/steve-desktop/1091_20090912070000.mpg file not found
2009-09-12 19:16:29.748 ProgramInfo, Error: GetPlaybackURL: '1145_20090912063000.mpg' should be local, but it can not be found.
2009-09-12 19:16:29.749 PlaybackBox::play(): Error, /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/steve-desktop/1145_20090912063000.mpg file not found
2009-09-12 19:16:29.756 ProgramInfo, Error: GetPlaybackURL: '1145_20090912063000.mpg' should be local, but it can not be found.
2009-09-12 19:16:29.756 Unable to find image file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/steve-desktop/1145_20090912063000.mpg.png
2009-09-12 19:16:29.756 Connecting to backend server: 192.168.0.165:6543 (try 1 of 5)
2009-09-12 19:16:29.760 Using protocol version 40


I updated the backend afterwards to see if it was a version problem.  Still no go.  I tried the time zone thing even thout that seemed hokey but mine are set to the same.

---

### Post by tgm4883 on 2009-09-12
> **skskarda said:**
> I am having the same problem.  I am an experienced ubuntu user.  I recently updated my frontend.  I have the exact same problem.  Frontend can see the recordings, play thumbnails, but when I go to play I get the file for the recording can not be found.

Log from mythfrontend:



I updated the backend afterwards to see if it was a version problem.  Still no go.  I tried the time zone thing even thout that seemed hokey but mine are set to the same.

Post logs from mythbuntu-log-grabber

---

### Post by skskarda on 2009-09-12
sorry.  I am just running mythtv on normal ubuntu, not mythbuntu.  I don't know what log grabber is or how to run it.  I can google and figure it out.  In meantime here is my backend log

2009-09-12 19:57:25.295 MainServer::HandleAnnounce Playback
2009-09-12 19:57:25.338 adding: steve-desktop as a client (events: 0)
2009-09-12 19:57:25.339 MainServer::HandleAnnounce FileTransfer
2009-09-12 19:57:25.340 adding: steve-desktop as a remote file transfer
2009-09-12 19:57:25.646 MainServer::HandleAnnounce Playback
2009-09-12 19:57:25.670 adding: steve-desktop as a client (events: 0)
2009-09-12 19:57:25.672 MainServer::HandleAnnounce FileTransfer
2009-09-12 19:57:25.674 adding: steve-desktop as a remote file transfer
2009-09-12 19:57:29.040 ProgramInfo, Error: GetPlaybackURL: '1165_20090629100000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.043 ProgramInfo, Error: GetPlaybackURL: '1162_20090706100000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.050 ProgramInfo, Error: GetPlaybackURL: '1165_20090812020000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.054 ProgramInfo, Error: GetPlaybackURL: '1165_20090819020000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.064 ProgramInfo, Error: GetPlaybackURL: '1165_20090902020000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.067 ProgramInfo, Error: GetPlaybackURL: '1121_20090902200000.mpg' should be local, but it can not be found.
2009-09-12 19:57:29.192 MainServer::HandleAnnounce Playback
2009-09-12 19:57:29.192 adding: steve-desktop as a client (events: 0)
2009-09-12 19:57:29.195 MainServer::HandleAnnounce FileTransfer
2009-09-12 19:57:29.198 adding: steve-desktop as a remote file transfer
2009-09-12 19:57:30.778 MainServer::HandleAnnounce Monitor
2009-09-12 19:57:30.779 adding: steve-desktop as a client (events: 0)
2009-09-12 19:57:34.603 Using runtime prefix = /usr
2009-09-12 19:57:34.679 Empty LocalHostName.
2009-09-12 19:57:34.682 Using localhost value of steve-desktop
2009-09-12 19:57:35.337 New DB connection, total: 1
2009-09-12 19:57:35.429 Connected to database 'mythconverg' at host: localhost
2009-09-12 19:57:35.431 Closing DB connection named 'DBManager0'
2009-09-12 19:57:35.432 Deleting UPnP client...


Strange thing is that I can play this file if I am on the backed.

---

### Post by skskarda on 2009-09-12
2009-09-12 19:57:34.679 Empty LocalHostName.

Could this be the problem?  I noted a few other threads that talked about setting the host-name.

---

### Post by skskarda on 2009-09-12
> **skskarda said:**
> 2009-09-12 19:57:34.679 Empty LocalHostName.

Could this be the problem?  I noted a few other threads that talked about setting the host-name.

Solved!   I had my hostname set to the same for both my backend and frontend.  Dumb dumb dumb.

Anyway for newbies. The command 'hostname' will tell you the name of your host.

[http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)

> Debian based systems use the file /etc/hostname to read the hostname of the system at boot time and set it up using the init script /etc/init.d/hostname.sh

/etc/hostname
server

So on a Debian based system we can edit the file /etc/hostname and change the name of the system and then run:

/etc/init.d/hostname.sh start

to make the change active. The hostname saved in this file (/etc/hostname) will be preserved on system reboot (and will be set using the same script we used hostname.sh).

I just changed what was in /etc/hostnames from steve-desktop (my hostname in both places) to steve-frontend.  Executed the command /etc/init.d/hostname.sh start

Happiness.

---

### Post by benlyboy on 2009-09-13
ok I have a question

wouldn't you have to reboot to set the new host name?
If this is the case wouldn't any change to file on a live cd  be lost on reboot? 
So does this mean you have to change the backend to match the front?

sorry if this seem dim of me but kinda new to this:D

---

### Post by benlyboy on 2009-09-13
oh here is the log from the live cd 


```
==> /var/log/Xorg.0.log <==
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 325 x 260
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Generic Explorer Mouse: Found 5 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SNY", prod id 7536

==> /home/ubuntu/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4410): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4410): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4538): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4538): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[4570]: starting up
xfce4-settings-helper is already running
** (nm-applet:4578): DEBUG: applet_common_device_state_changed

MCS->Xfconf settings migration complete

/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4617): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4617): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4631): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4631): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (update-notifier:4581): DEBUG: crashreport_check

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
mythtv: could not connect to socket
mythtv: No such file or directory

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  124K  245M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  144K  245M   1% /dev
tmpfs                 245M     0  245M   0% /dev/shm
rootfs                245M   27M  219M  11% /
/dev/sr0              615M  615M     0 100% /cdrom
/dev/loop0            542M  542M     0 100% /rofs
tmpfs                 245M   12K  245M   1% /tmp

==> uname -a <==
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
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
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=[REMOVED] latency=64 mingnt=255 module=e1000 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by tgm4883 on 2009-09-13
> **benlyboy said:**
> oh here is the log from the live cd 


```
==> /var/log/Xorg.0.log <==
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) intel(0): Setting screen physical size to 325 x 260
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Generic Explorer Mouse: Found 5 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SNY", prod id 7536
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SNY", prod id 7536

==> /home/ubuntu/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4410): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4410): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4538): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4538): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[4570]: starting up
xfce4-settings-helper is already running
** (nm-applet:4578): DEBUG: applet_common_device_state_changed

MCS->Xfconf settings migration complete

/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4617): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4617): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/bin/mythbuntu-startup:57: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')

(mythbuntu-startup:4631): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-startup:4631): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (update-notifier:4581): DEBUG: crashreport_check

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
mythtv: could not connect to socket
mythtv: No such file or directory

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  124K  245M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  144K  245M   1% /dev
tmpfs                 245M     0  245M   0% /dev/shm
rootfs                245M   27M  219M  11% /
/dev/sr0              615M  615M     0 100% /cdrom
/dev/loop0            542M  542M     0 100% /rofs
tmpfs                 245M   12K  245M   1% /tmp

==> uname -a <==
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
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
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=[REMOVED] latency=64 mingnt=255 module=e1000 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Interesting that we don't get any mythtv logs, is there anything in /var/log/mythtv/

---

### Post by skskarda on 2009-09-14
> **benlyboy said:**
> ok I have a question

wouldn't you have to reboot to set the new host name?
If this is the case wouldn't any change to file on a live cd  be lost on reboot? 

The command '/etc/init.d/hostname.sh start' is what sets the host name on startup.  Executing it as root allows the hostname to change without rebooting.

I didn't really think about what that all means on a live CD.  It might be just easier to type 'hostname NEWHOSTNAME' if you want to change the hostname live.  That won't stick on reboot but if you are on a live cd, I guess it wouldn't matter.

> **benlyboy said:**
> So does this mean you have to change the backend to match the front?

No, the opposite.  The frontend and backend must have different hostnames.

> **benlyboy said:**
> sorry if this seem dim of me but kinda new to this:D

No worries.  We all started out from the same place.  I knew less than you 3 years ago and I am still not nearly as smart as 75% of the people on this forum but  but Mythtv, Ubuntu, and these forums taught me a great deal.  

I don't know if this solved your problem or not.  You might have  completely different issue but maybe this will provide some clues.  Regardless, be sure to post back here on what you finally do to get it going so others that search for the same symptoms and come across this post have some idea what to do.  Or continue to post questions and hopefully someone smart than me can help you out.

---

### Post by skskarda on 2009-09-14
> **benlyboy said:**
> oh here is the log from the live cd 


That is not the correct log.  An easy way to get the log is to open a terminal and run frontend and backend each from their own terminal.  The log will print out on the terminal.  You can watch what it says when you come across the problem.  Copy and paste that in here.

Or like the other person suggested, look for the log in /var/log/mythtv/

If you see the line that I did:
2009-09-12 19:57:34.679 Empty LocalHostName.
then my solution may help.  If you don't you probably have something else going on.

---

### Post by benlyboy on 2009-09-16
Hi all
Well thanks all for your help. I got the live CD working last night, so I thought I would post what I did.

First up I have to admit that I kinda cheated in that I switched to another computer. The live TV  worked right off, so I'm thinking that the problem I was having with the blue screen was a video hardware problem. Maybe the live CD doesn't have the right driver for the hardware in my old Dell.

As for the problem playing recording I found the answer in this very post so thanks sawbuck. I read your post a few days back but somehow at the time thought it meant I had to make sure that the two systems had the same time. and this is not what you said at all, you said the same time zone not same time. When I set that it worked first time...I just about fell out of my seat...lol

If someone would like to give me there ideas on way the tv didn't work i would love to hear them.

Also why would the time zone make such a difference to watching recordings...?

well thanks again everyone for all the help:)

---

