---
title: "my computer is playing songs and I don't know why"
date: 2008-08-03
forum: Multimedia Software
---

### Post by pytheas22 on 2008-08-03
I hadn't had my speakers plugged in to my computer for a while because I lost the cable.  I found it again and plugged them in and am having a really strange problem.  Songs are playing constantly, one after another, and I have no idea what's playing them.  They're not music that I have on my hard drive; it sounds like a radio station or something.

My first thought was that it must be some website, but I did a "killall firefox" and the music keeps playing (I checked to make sure Firefox was really dead and it was).  I logged out of Gnome, which stopped it, but when I logged back in, the music started playing again within thirty seconds.  I have no media players open.

Is there a way to traceback the source of music?  I'm thinking that maybe alsa has some way to tell me which process is generating the music.  If anyone knows, I would really appreciate it, because I'd like to figure out what's going on here...besides being annoying (I don't particularly like the songs), it's a little disconcerting because there's a chance it could be a security issue.

Thanks in advance for any suggestions.

Also, in case anyone cares to take a look, here is my process list.  I couldn't find anything that could conceivably be related to the music, but maybe I missed something:
```

$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:04 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    9 ?        00:00:04 events/0
   11 ?        00:00:00 khelper
   44 ?        00:00:04 kblockd/0
   48 ?        00:00:00 kacpid
   49 ?        00:00:00 kacpi_notify
  131 ?        00:00:00 kseriod
  178 ?        00:00:00 pdflush
  179 ?        00:00:18 pdflush
  180 ?        00:00:00 kswapd0
  223 ?        00:00:00 aio/0
  651 ?        00:00:00 gconfd-2
  658 ?        00:00:00 gdm
  662 tty7     00:00:36 Xorg
  688 ?        00:00:00 gnome-session
  740 ?        00:00:00 ssh-agent
  747 ?        00:00:00 seahorse-agent
  754 ?        00:00:00 gnome-keyring-d
  757 ?        00:00:00 dbus-daemon
  758 ?        00:00:00 gnome-settings-
  762 ?        00:00:04 pulseaudio
  765 ?        00:00:00 gconf-helper
  780 ?        00:00:00 compiz
  783 ?        00:00:00 vino-server
  784 ?        00:00:02 gnome-panel
  787 ?        00:00:00 nautilus
  789 ?        00:00:00 gnome-screensav
  793 ?        00:00:00 gvfsd
  819 ?        00:00:00 gvfs-fuse-daemo
  854 ?        00:00:04 compiz.real
  858 ?        00:00:00 update-notifier
  862 ?        00:00:00 evolution-alarm
  864 ?        00:00:00 tracker-applet
  868 ?        00:00:28 trackerd
  870 ?        00:00:00 gvfsd-trash
  880 ?        00:00:00 nm-applet
  881 ?        00:00:00 python
  885 ?        00:00:00 gnome-volume-ma
  886 ?        00:00:00 gnome-power-man
  891 ?        00:00:00 multiload-apple
  893 ?        00:00:00 stickynotes_app
  906 ?        00:00:00 evolution-data-
  913 ?        00:00:00 mixer_applet2
  915 ?        00:00:00 gvfsd-burn
  919 ?        00:00:00 evolution-excha
  936 ?        00:00:00 sh
  937 ?        00:00:00 compiz-decorato
  939 ?        00:00:00 gtk-window-deco
  953 ?        00:00:29 firefox
  977 ?        00:01:15 npviewer.bin
  997 ?        00:00:00 evolution
 1060 ?        00:00:00 notification-da
 1069 ?        00:00:00 gnome-vfs-daemo
 1085 ?        00:00:00 gnome-terminal
 1087 ?        00:00:00 gnome-pty-helpe
 1088 pts/0    00:00:00 bash
 1105 pts/0    00:00:00 ps
 1478 ?        00:00:00 ksuspend_usbd
 1479 ?        00:00:00 khubd
 1522 ?        00:00:10 ata/0
 1536 ?        00:00:00 ata_aux
 2270 ?        00:00:11 scsi_eh_0
 2271 ?        00:00:00 scsi_eh_1
 2296 ?        00:00:09 scsi_eh_2
 2297 ?        00:00:00 scsi_eh_3
 2516 ?        00:00:00 reiserfs/0
 2808 ?        00:00:00 udevd
 3157 ?        00:00:00 kpsmoused
 3449 ?        00:00:00 kgameportd
 4851 tty4     00:00:00 getty
 4852 tty5     00:00:00 getty
 4856 tty2     00:00:00 login
 4857 tty3     00:00:00 login
 4858 tty6     00:00:00 getty
 5038 ?        00:00:00 acpid
 5075 ?        00:00:08 kondemand/0
 5153 ?        00:00:00 syslogd
 5213 ?        00:00:00 dd
 5215 ?        00:00:00 klogd
 5237 ?        00:00:29 dbus-daemon
 5253 ?        00:00:04 NetworkManager
 5267 ?        00:00:09 NetworkManagerD
 5280 ?        00:00:00 system-tools-ba
 5309 ?        00:00:00 sshd
 5339 ?        00:00:02 avahi-daemon
 5340 ?        00:00:00 avahi-daemon
 5391 ?        00:00:00 mysqld_safe
 5433 ?        00:00:52 mysqld
 5434 ?        00:00:00 logger
 5556 ?        00:00:00 cupsd
 5812 ?        00:00:00 exim4
 5872 ?        00:00:00 nmbd
 5874 ?        00:00:00 smbd
 5893 ?        00:00:00 smbd
 5996 ?        00:00:07 dhcdbd
 6015 ?        00:00:01 hald
 6018 ?        00:00:00 console-kit-dae
 6080 ?        00:00:00 hald-runner
 6097 ?        00:00:00 hald-addon-cpuf
 6098 ?        00:00:00 hald-addon-acpi
 6106 ?        00:00:04 hald-addon-inpu
 6116 ?        00:00:00 hald-addon-stor
 6124 ?        00:00:12 hald-addon-stor
 6127 ?        00:00:10 hald-addon-stor
 6147 ?        00:00:00 hcid
 6163 ?        00:00:00 btaddconn
 6164 ?        00:00:00 btdelconn
 6189 ?        00:00:00 bluetoothd-serv
 6201 ?        00:00:00 bluetoothd-serv
 6214 ?        00:00:00 krfcommd
 6239 ?        00:00:00 gdm
 6271 ?        00:00:32 ruby
 6310 ?        00:00:00 atd
 6317 ?        00:00:00 sh
 6319 ?        00:00:10 urlsnarf
 6328 ?        00:00:00 cron
 6407 ?        00:00:02 apache2
 6483 tty1     00:00:00 getty
 6486 ?        00:00:00 apache2
 6487 ?        00:00:00 apache2
 6488 ?        00:00:00 apache2
 6489 ?        00:00:00 apache2
 6490 ?        00:00:00 apache2
 6586 ?        00:00:00 bonobo-activati
 6924 ?        00:00:00 apache2
 7433 ?        00:00:00 apache2
18267 ?        00:00:00 apache2
18268 ?        00:00:00 apache2
18269 ?        00:00:00 apache2
19132 ?        00:00:00 SystemToolsBack
20805 ?        00:00:00 rvnamed
23577 tty2     00:00:00 bash
23823 tty2     00:00:00 startx
23841 tty2     00:00:00 xinit
23842 tty9     00:02:40 Xorg
23850 tty2     00:00:00 ck-launch-sessi
23874 ?        00:00:00 ssh-agent
23877 tty2     00:00:00 x-session-manag
23886 ?        00:00:00 seahorse-agent
23895 tty2     00:00:00 gnome-keyring-d
23898 ?        00:00:00 dbus-daemon
23899 tty2     00:00:00 gnome-settings-
23916 ?        00:00:01 gnome-screensav
23918 tty2     00:00:00 metacity
23921 ?        00:00:00 vino-server
23926 tty2     00:00:08 gnome-panel
23930 tty2     00:00:01 nautilus
23939 ?        00:00:00 gvfsd
23964 ?        00:00:39 multiload-apple
23966 ?        00:00:00 gvfsd-trash
23968 ?        00:00:00 stickynotes_app
23977 ?        00:00:00 mixer_applet2
24007 tty2     00:00:01 update-notifier
24014 tty2     00:00:00 tracker-applet
24016 tty2     00:00:00 trackerd
24020 tty2     00:00:38 nm-applet
24021 tty2     00:00:00 python
24023 ?        00:00:00 gnome-volume-ma
24025 ?        00:00:00 gvfsd-burn
24026 ?        00:00:00 gnome-power-man
24066 tty3     00:00:00 bash
24157 ?        00:00:00 dbus-daemon
24197 ?        00:00:00 gvfsd
24236 ?        00:00:00 gvfsd-trash
24273 tty3     00:00:00 trackerd
24285 ?        00:00:00 gvfsd-burn
24372 ?        00:00:16 notification-da
28081 ?        00:00:00 ossec-maild
28085 ?        00:00:00 ossec-execd
28089 ?        00:00:07 ossec-analysisd
28093 ?        00:00:00 ossec-logcollec
28097 ?        00:01:08 ossec-syscheckd
28101 ?        00:00:00 ossec-monitord
31443 ?        00:00:00 migration/1
31444 ?        00:00:00 ksoftirqd/1
31445 ?        00:00:00 watchdog/1
31446 ?        00:00:00 kondemand/1
31447 ?        00:00:00 reiserfs/1
31448 ?        00:00:00 ata/1
31449 ?        00:00:00 aio/1
31450 ?        00:00:00 kblockd/1
31451 ?        00:00:00 events/1
31751 ?        00:00:00 wpa_supplicant
31752 ?        00:00:00 dhclient
```

---

### Post by silkstone on 2008-08-03
Have you tried...

killall firefox
killall firefox-bin

Also kill npviewer.bin which (I think) is FF's flash player.

---

### Post by pytheas22 on 2008-08-03
Thanks for the suggestions.  Strangely the music stopped, but I have no idea why.  firefox and firefox-bin were both dead before, even as the music was playing, because "ps -e | grep firefox" returned nothing.  I didn't think to check npviewer.bin, but I assume that if Firefox is not running, npviewer must also be out, right?  If there's a way for it to keep running on its own even after Firefox is closed, however, then that could explain it--a website may have started playing the music and kept playing via npviewer even after I killed Firefox.

---

### Post by rudihawk on 2008-08-03
Maybe rhythmbox was streaming something from lastfm?

---

