---
title: "help with package"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by aidanh on 2007-01-31
need help installin the gst-plugins-0.8.8 package

cant undastand how tto do it..

linux noob..

---

### Post by taurus on 2007-01-31
Are you talking about the gstreamer plugins?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by aidanh on 2007-01-31
yes i am ! got the thing i need just really hard to install / undastand how to do it.. 

any easy instructions how to do it?

thnaks aidan

---

### Post by taurus on 2007-01-31
Did you get an error message when you tried to install it?  What happens if you run that command from the link from a terminal?

---

### Post by aidanh on 2007-01-31
i dont how to run it??

and what link ?? from terminal????

also should i bother getting w32codecs as well and where to get them if i should??


aidanh

---

### Post by taurus on 2007-01-31
Why don't you install automatix2 and use it to install everything regarding to multimedia stuff.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by aidanh on 2007-01-31
hmm cant find the download page for that?? and cant install gstermer etheri

---

### Post by taurus on 2007-01-31
It says "Installation" on the left hand side.

[http://www.getautomatix.com](http://www.getautomatix.com).

Otherwise, here's a directly link.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by aidanh on 2007-01-31
will that let me instal the thing i want to get mp3's to play??

---

### Post by aidanh on 2007-01-31
ok figured out how to install the gst-pluggin thing...

but i dont think it worked heres what it came up with:

aidan@ubuntu:~$ sudo apt-get install gst-plugins-0.8.8
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
aidan@ubuntu:~$

---

### Post by taurus on 2007-01-31
Do you have synaptic running while you are running that command from a terminal?  What's the output of this command from a terminal then?

```
ps -A
```
And yes, automatix will install all the multimedia stuff on your machine for you.  Just pick from the menu what you want to install and what you don't want to install.

---

### Post by aidanh on 2007-01-31
no idea still how to get automatix???? using 5.10 ubuntu...


aidan@ubuntu:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
   64 ?        00:00:00 kblockd/0
   93 ?        00:00:00 aio/0
   92 ?        00:00:01 kswapd0
  678 ?        00:00:00 kseriod
 1814 ?        00:00:00 khubd
 2900 ?        00:00:01 kjournald
 3035 ?        00:00:00 udevd
 4464 ?        00:00:00 kjournald
 4963 ?        00:00:00 kgameportd
 5986 ?        00:00:00 acpid
 6001 ?        00:00:00 syslogd
 6018 ?        00:00:00 dd
 6020 ?        00:00:00 klogd
 6033 ?        00:00:00 dbus-daemon
 6046 ?        00:00:00 hald
 6051 ?        00:00:00 hald-addon-acpi
 6060 ?        00:00:03 hald-addon-stor
 6437 ?        00:00:00 gdm
 6442 ?        00:00:00 gdm
 6519 ?        00:22:52 Xorg
 6548 ?        00:00:01 cupsd
 6578 ?        00:00:00 hpiod
 6598 ?        00:00:00 python
 6784 ?        00:00:00 hcid
 6790 ?        00:00:00 sdpd
 6800 ?        00:00:00 krfcommd
 6832 ?        00:00:00 atd
 6845 ?        00:00:00 cron
 6881 tty1     00:00:00 getty
 6882 tty2     00:00:00 getty
 6883 tty3     00:00:00 getty
 6884 tty4     00:00:00 getty
 6885 tty5     00:00:00 getty
 6886 tty6     00:00:00 getty
 6907 ?        00:00:03 x-session-manag
 6945 ?        00:00:00 ssh-agent
 6948 ?        00:00:00 dbus-launch
 6949 ?        00:00:00 dbus-daemon
 6951 ?        00:00:03 gconfd-2
 6980 ?        00:00:00 gnome-keyring-d
 6982 ?        00:00:06 esd
 6986 ?        00:00:00 bonobo-activati
 6988 ?        00:00:14 gnome-settings-
 6991 ?        00:00:06 gam_server
 7027 ?        00:02:52 metacity
 7032 ?        00:00:33 gnome-panel
 7034 ?        00:01:05 nautilus
 7036 ?        00:00:02 gnome-volume-ma
 7040 ?        00:01:10 wnck-applet
 7044 ?        00:00:04 update-notifier
 7047 ?        00:00:00 gnome-vfs-daemo
 7049 ?        00:00:05 gnome-cups-icon
 7051 ?        00:00:04 trashapplet
 7053 ?        00:00:13 gnome-netstatus
 7055 ?        00:00:01 notification-da
 7069 ?        00:00:00 mapping-daemon
 7182 ?        00:00:00 dhclient3
 7888 ?        00:00:01 eog
 8120 ?        00:00:04 clock-applet
 8140 ?        00:00:02 evolution-excha
 8143 ?        00:00:00 evolution-data-
 8399 ?        00:00:02 xscreensaver
 8648 ?        00:00:01 eog
 8798 ?        00:00:00 pdflush
 9086 ?        00:40:03 firefox-bin
10358 ?        00:00:00 gnome-pty-helpe
10743 ?        00:00:00 gksudo
10746 ?        00:00:00 sudo <defunct>
10748 ?        00:00:00 sudo
10846 ?        00:00:00 gnome-pty-helpe
11267 ?        00:00:00 pdflush
11499 ?        00:00:00 gnome-pty-helpe
11735 ?        00:00:05 file-roller
11978 ?        00:00:16 xchat
12620 ?        00:00:00 gnome-pty-helpe
12694 ?        00:00:01 file-roller
12783 ?        00:00:00 gnome-pty-helpe
13196 ?        00:00:00 gnome-terminal
13201 ?        00:00:00 gnome-pty-helpe
13202 pts/0    00:00:00 bash
13212 pts/0    00:00:00 ps

---

### Post by aidanh on 2007-01-31
bump!!!

---

