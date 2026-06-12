---
title: "[SOLVED] updated mythbuntu theme crash"
date: 2008-04-11
forum: Mythbuntu
---

### Post by ppww on 2008-04-11
Using 8.04 beta amd64 + updates, the latest update to mythtv-theme-mythbuntu (0.20080208ubuntu1) causes the frontend to crash badly.

Symptom: Starting frontend shows a gray "prescaling" dialog, followed by a blue background, clock display, and nothing else (no menu text or icon).  Coredump at first keypress.  Frontend log shows:

2008-04-10 01:33:31.782 Unable to parse themeinfo.xml for glass-wide
2008-04-10 01:33:31.783 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-10 01:34:06.769 Received a remote 'Clear Cache' request
2008-04-10 01:34:06.800 Primary screen 0.
2008-04-10 01:34:06.801 Using screen 0, 1280x720 at 0,0
2008-04-10 01:34:06.811 Switching to square mode (Mythbuntu)
2008-04-10 01:34:16.574 Specified base font 'medium' does not exist for font clock
2008-04-10 01:34:16.574 Specified base font 'medium' does not exist for font small
2008-04-10 01:34:16.574 Specified base font 'medium' does not exist for font medium
2008-04-10 01:34:16.574 Specified base font 'medium' does not exist for font large
2008-04-10 01:34:16.576 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-10 01:34:16.690 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-10 01:34:17.834 MythThemedMenuPrivate: Must have room for at least 1 column of buttons

Resolved with: "apt-get uninstall mythtv-theme-mythbuntu".  On next startup, G.A.N.T. is used by default, and I can then change to my preferred theme (Mythbuntu-7.10).  I reinstalled mythtv-theme-mythbuntu and no longer get the crash behavior, unless I select that theme.

---

### Post by silverdulcet on 2008-04-11
I experienced the exact same problem. Appreciate you posting a work around for this!

---

### Post by superm1 on 2008-04-12
Hmm interesting that you folks are hitting this crash.  I have yet to reproduce locally...

Can you please file a bug against the theme, and include this information (run locally of course)

$ apt-cache policy mythtv-theme-mythbuntu
mythtv-theme-mythbuntu:
  Installed: 0.20080409
  Candidate: 0.20080409
  Version table:
 *** 0.20080409 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status

---

### Post by superm1 on 2008-04-12
Also, ANYONE else experiencing this, please add some additional information.  Any *theme* causing crashes is urgent to get fixed.  Especially when it's the "Default" theme.

I'm suspecting that it's a matter of the cached theme (in ~/.mythtv) not matching the actual theme.  This would make sense since the theme "did" change.

If that is indeed the case, can someone experiencing this, try to remove the cached theme in ~/.mythtv/themecache and restart myth?

---

### Post by Kazriko on 2008-04-12
I haven't experienced this exact issue, but I have run into another theme related glitch upgrading from 7.10 to 8.04beta with mythtv. I used the GANT theme before. Now after upgrading both Mythtv-setup and mythtvfrontend crash in this manner:

[email]kaz@teela:~/.myth[/email]tv$ sudo mythtv-setup.real
2008-04-12 00:30:32.034 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-12 00:30:32.046 XScreenSaver support enabled
2008-04-12 00:30:32.047 DPMS is disabled.
2008-04-12 00:30:32.048 Empty LocalHostName.
2008-04-12 00:30:32.048 Using localhost value of teela
2008-04-12 00:30:32.082 New DB connection, total: 1
2008-04-12 00:30:32.092 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-12 00:30:32.095 Closing DB connection named 'DBManager0'
2008-04-12 00:30:32.098 Primary screen 0.
2008-04-12 00:30:32.099 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-12 00:30:32.102 Using screen 0, 1920x1080 at 0,0
2008-04-12 00:30:32.115 New DB connection, total: 2
2008-04-12 00:30:32.116 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-12 00:30:32.118 Current Schema Version: 1214
2008-04-12 00:30:32.134 Primary screen 0.
2008-04-12 00:30:32.134 Using screen 0, 1920x1080 at 0,0
2008-04-12 00:30:32.136 Switching to square mode (G.A.N.T)
Segmentation fault (core dumped)

It's not likely to be the same issue however, but it is an annoyance in the upgrade.

---

### Post by Kazriko on 2008-04-12
Also, I've removed the cache in that folder. it gives the same results before and after.
Never mind, it appears that rebooting fixes this problem.

---

### Post by jtalley on 2008-04-12
I was experiencing the problem in the first post. I saw the background from my pre-upgrade theme with no menu items, just the date and time. I removed the cached theme directory as suggested and started mythfrontend. I see the new theme now and everything seems to work.

Thanks.

---

### Post by suffice on 2008-04-12
I had the same problem...thanks a bunch..been drivin me crazy for a few days....

---

### Post by superm1 on 2008-04-12
FYI, new theme uploaded this morning.

it provides these three themes:

/usr/share/mythtv/themes/Mythbuntu-7.10
/usr/share/mythtv/themes/Mythbuntu-8.04-wide
/usr/share/mythtv/themes/Mythbuntu-8.04

If it detects you are coming around from an upgraded theme, it will make a symlink:
/usr/share/mythtv/themes/Mythbuntu -> /usr/share/mythtv/themes/Mythbuntu-7.10

If you already removed the cache once to work around this, you might need to one more time.  This is a more "permanent" solution though, and also folks won't be "forced" into the new 8.04 theme if they dont want to.

---

### Post by ppww on 2008-04-19
Just wanted to confirm that the 20080412 update fixed the problem.  I am certain that it was cache-related, as superm1 suspected.  I am happily using the new Mythbuntu-wide theme, (though I haven't yet figured out how it differs from ProjectGrayhem-wide).

---

### Post by superm1 on 2008-04-19
> **ppww said:**
> Just wanted to confirm that the 20080412 update fixed the problem.  I am certain that it was cache-related, as superm1 suspected.  I am happily using the new Mythbuntu-wide theme, (though I haven't yet figured out how it differs from ProjectGrayhem-wide).
very minute differences :)

---

### Post by belgofac on 2008-07-15
For days I have been trying to get Mythbuntu running but I get stuck.
Here´s the frontend log:

tarting mythfrontend.real..
2008-07-15 23:21:35.173 New DB connection, total: 2
2008-07-15 23:21:35.174 Connected to database 'mythconverg' at host: localhost
2008-07-15 23:21:35.178 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-15 23:21:35.178 Enabled verbose msgs:  important general
2008-07-15 23:21:35.726 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-07-15 23:21:36.239 Connecting to lcd server: localhost:6545 (try 2 of 10)
2008-07-15 23:21:39.216 No theme dir: /home/willem/.mythtv/themes/Iulius
2008-07-15 23:21:39.219 Primary screen 0.
2008-07-15 23:21:39.220 Using screen 0, 1920x1200 at 0,0
2008-07-15 23:21:39.223 No theme dir: /home/willem/.mythtv/themes/Iulius
2008-07-15 23:21:39.225 Switching to square mode (Iulius)
2008-07-15 23:21:39.372 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-15 23:21:39.373 lirc_init failed for mythtv, see preceding messages
2008-07-15 23:21:39.373 JoystickMenuClient Error: Joystick disabled - Failed to read /home/willem/.mythtv/joystickmenurc
2008-07-15 23:22:13.475 Loading from: /usr/share/mythtv/themes/Iulius/base.xml
2008-07-15 23:22:13.709 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-15 23:22:13.923 Registering Internal as a media playback plugin.
2008-07-15 23:22:14.345 Failed to run 'cdrecord --scanbus'
2008-07-15 23:22:14.349 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-07-15 23:22:14.353 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-07-15 23:22:14.464 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-07-15 23:22:14.634 No theme dir: /home/willem/.mythtv/themes/Iulius
2008-07-15 23:22:21.723 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-15 23:22:21.725 Using protocol version 40
2008-07-15 23:22:21.738 TV: Attempting to change from None to WatchingLiveTV
2008-07-15 23:22:21.740 Using protocol version 40
2008-07-15 23:22:23.097 DPMS Deactivated 
2008-07-15 23:22:23.105 New DB connection, total: 3
2008-07-15 23:22:23.106 Connected to database 'mythconverg' at host: localhost
2008-07-15 23:22:23.178 NVP: Disabling Audio, params(-1,2,44100)

Any idea´s?

---

### Post by superm1 on 2008-07-15
You are using Iulius for your theme.  If there are problems with that, it's a different bug.  Start out by rm -rf ~/.mythtv to clean up your cache.

---

### Post by belgofac on 2008-07-16
I solved my problem:

1. set the recoding path back to default.
2. For some reason the ATI Xorg-fglxr driver was installed.  Unistalled and only left Xorg installed.  Everything started working.:)

---

