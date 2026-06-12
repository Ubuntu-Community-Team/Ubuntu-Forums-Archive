---
title: "Problem with unity menus"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ACDias on 2011-04-03
Hi, I'm sorry but I've created [a thread in the wrong forum]("http://ubuntuforums.org/showthread.php?t=1720065"). But here's the problem I've found:

I've upgraded from 10.10 and I managed to mess up the unity environment. I hate the indicator applet menus, so I've uninstalled the package indicator-messages and now I can't see any menu or panel. I've installed it again using recovery but the Unity menu and the top panel didn't get back. 
:(

Can someone help me plz. Thanks.

---

### Post by garvinrick4 on 2011-04-03
Open a terminal and copy and paste this line of code:
```
gedit /var/log/apt/history.log
```copy and paste what you removed in log to your thread and installed today.

---

### Post by cor2y on 2011-04-03
As far as i can tell its something in the /home folder thats causing unity 3D to bork.
Solution is to create a desktop launcher of either gnome-terminal or unity itself and when you login click the launcher if its the gnome terminal type "unity --reset &" if its a launcher just pointing to unity , launch it and unity 3D will then work.

If  you cant create a launcher in the default ubuntu session, then switch to either unity 2D (if its installed) which will or or ubuntu classic.
To do this on the login screen, select your username and on the bottom panel select your session pick ubuntu classic.

---

### Post by ACDias on 2011-04-03
Here are the result of the history:

```

Start-Date: 2011-04-02  12:03:57
Upgrade: python-bugbuddy:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), gnome-power-manager:amd64 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), tomboy:amd64 (1.4.2-0ubuntu1, 1.4.2-0ubuntu2), python-evolution:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), python-cupshelpers:amd64 (1.2.3+20100723-0ubuntu8.1, 1.2.3+20100723-0ubuntu8.2), libc-bin:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), python-gnomedesktop:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libldap-2.4-2:amd64 (2.4.23-0ubuntu3.4, 2.4.23-0ubuntu3.5), libqt4-qt3support:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), sysvinit-utils:amd64 (2.87dsf-4ubuntu19, 2.87dsf-4ubuntu19.1), python-evince:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), gstreamer0.10-plugins-bad:amd64 (0.10.20-1ubuntu1, 0.10.20-1ubuntu1.1), system-config-printer-gnome:amd64 (1.2.3+20100723-0ubuntu8.1, 1.2.3+20100723-0ubuntu8.2), python-brasero:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libqt4-script:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-designer:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-network:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-dbus:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), python-totem-plparser:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), python-gnomekeyring:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libappindicator0.1-cil:amd64 (0.2.9-0ubuntu1, 0.2.9-0ubuntu1.1), libqt4-opengl:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libc6-i386:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), libqt4-sql-sqlite:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), update-manager:amd64 (0.142.22, 0.142.23), update-manager-core:amd64 (0.142.22, 0.142.23), libqt4-help:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), gdm:amd64 (2.30.5-0ubuntu4+langfixes~maverick1, 2.30.5-0ubuntu4.1+langfixes~maverick1), libqtcore4:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), system-config-printer-udev:amd64 (1.2.3+20100723-0ubuntu8.1, 1.2.3+20100723-0ubuntu8.2), w3m:amd64 (0.5.2-6, 0.5.2-6ubuntu1), gnome-terminal-data:amd64 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), python-rsvg:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libqt4-sql:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-svg:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), python-appindicator:amd64 (0.2.9-0ubuntu1, 0.2.9-0ubuntu1.1), libqt4-xml:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libappindicator1:amd64 (0.2.9-0ubuntu1, 0.2.9-0ubuntu1.1), libc6-dbg:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), libc6-dev:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), libqtgui4:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), python-mediaprofiles:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), python-gnomeapplet:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), python-wnck:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), python-metacity:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libqt4-sql-mysql:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), system-config-printer-common:amd64 (1.2.3+20100723-0ubuntu8.1, 1.2.3+20100723-0ubuntu8.2), sysv-rc:amd64 (2.87dsf-4ubuntu19, 2.87dsf-4ubuntu19.1), python-gnome2-desktop-dev:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libc-dev-bin:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), libc6:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), libc6-dev-i386:amd64 (2.12.1-0ubuntu10.2, 2.12.1-0ubuntu10.3), initscripts:amd64 (2.87dsf-4ubuntu19, 2.87dsf-4ubuntu19.1), indicator-application:amd64 (0.2.9-0ubuntu1, 0.2.9-0ubuntu1.1), python-gtop:amd64 (2.30.0-1ubuntu5, 2.30.0-1ubuntu5.1), libldap2-dev:amd64 (2.4.23-0ubuntu3.4, 2.4.23-0ubuntu3.5)
End-Date: 2011-04-02  12:06:43

Start-Date: 2011-04-02  17:35:30
Remove: nvtv:amd64 (0.4.7-7)
End-Date: 2011-04-02  17:35:54

Start-Date: 2011-04-02  17:41:50
Install: nvidia-current:amd64 (270.30-0ubuntu3), dkms:amd64 (2.1.1.2-5ubuntu1, automatic), nvidia-settings:amd64 (270.29-0ubuntu1, automatic)
End-Date: 2011-04-02  17:43:09

Start-Date: 2011-04-02  17:45:59
Install: libgl1-mesa-dri-experimental:amd64 (7.10.1-0ubuntu3)
End-Date: 2011-04-02  17:46:01

Start-Date: 2011-04-02  18:06:32
Commandline: apt-get --purge remove nvidia-glx* nvidia-settings
Purge: nvidia-settings:amd64 (270.29-0ubuntu1)
End-Date: 2011-04-02  18:06:45

Start-Date: 2011-04-02  18:18:17
Remove: nvidia-current:amd64 (270.30-0ubuntu3)
End-Date: 2011-04-02  18:19:15

Start-Date: 2011-04-02  18:20:30
Remove: libgl1-mesa-dri-experimental:amd64 (7.10.1-0ubuntu3)
End-Date: 2011-04-02  18:20:31

Start-Date: 2011-04-02  18:20:37
Install: nvidia-current:amd64 (270.30-0ubuntu3), nvidia-settings:amd64 (270.29-0ubuntu1, automatic)
End-Date: 2011-04-02  18:21:24

Start-Date: 2011-04-02  18:34:24
Remove: nvidia-current:amd64 (270.30-0ubuntu3)
End-Date: 2011-04-02  18:34:59

Start-Date: 2011-04-02  18:35:01
Remove: nvidia-settings:amd64 (270.29-0ubuntu1)
End-Date: 2011-04-02  18:35:04

Start-Date: 2011-04-02  18:35:25
Commandline: apt-get --purge remove xserver-xorg-video-nouveau
Purge: xserver-xorg-video-all:amd64 (7.6+4ubuntu1), xserver-xorg-video-nouveau:amd64 (0.0.16+git20110107+b795ca6e-0ubuntu6)
End-Date: 2011-04-02  18:35:28

Start-Date: 2011-04-02  18:53:20
Commandline: /usr/sbin/synaptic
Install: linux-source-2.6.38:amd64 (2.6.38-7.39)
End-Date: 2011-04-02  18:53:26

Start-Date: 2011-04-02  19:02:03
Install: nvidia-current:amd64 (270.30-0ubuntu3), nvidia-settings:amd64 (270.29-0ubuntu1, automatic)
End-Date: 2011-04-02  19:03:13

Start-Date: 2011-04-02  19:21:07
Commandline: /usr/sbin/synaptic
Purge: linux-image-2.6.35-27-generic:amd64 (2.6.35-27.48)
End-Date: 2011-04-02  19:21:41

Start-Date: 2011-04-02  20:00:42
Install: ubuntu-tweak:amd64 (0.5.11-1~natty1)
End-Date: 2011-04-02  20:01:16

Start-Date: 2011-04-02  20:09:44
Commandline: apt-get remove indicator-messages
Remove: indicator-messages:amd64 (0.3.92-0ubuntu3)
End-Date: 2011-04-02  20:09:46

Start-Date: 2011-04-02  20:14:55
Commandline: apt-get install indicator-messages
Install: indicator-messages:amd64 (0.3.92-0ubuntu3)
End-Date: 2011-04-02  20:15:06
```
When I use unity --reset I starts to work again... But will I have to put this command on the boot of the system? I think there's a problem with something I did :/

---

### Post by ACDias on 2011-04-03
I think its not starting when I login on the system. When I run unity --reset it writes on console that unity panel process not found.

---

### Post by cor2y on 2011-04-03
yeah i never got it to work as a startup app, i had to create a unity launcher, and everytime i logged in that was the first app i started up but i got fed up and so moved all my important files to temporary storage/backups like evolution, firefox etc excluding the hidden gnome file settings and reinstall 11.04 reformating my /home partition and them moving all the important stuff back 

And now unity 3D works for me with no crashes when i change something in compiz config settings manager, no crashes of any kind, the downside is i have to reconfigure all  my custom settings/keyboard shortcuts etc

---

### Post by ACDias on 2011-04-03
I think I'll do this too. But I'll wait for the stable release.

---

