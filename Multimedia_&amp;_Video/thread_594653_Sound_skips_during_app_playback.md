---
title: "Sound skips during app playback"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by devosion on 2007-10-28
This occurs during mp3 and cd playback so far. I tried to listen to music via an internet source and the skipping was significantly less, but still occurred when Firefox was tabbed through at times. The problem itself may be inherent within my video card because my sound card was originally not detected properly, and still is not. I am using an Audigy Value that is detected as an Audigy LS. Originally I had no sound after performing an update on Feisty Fawn, but I purged and reinstalled all alsa components then installed asoundconf-gtk and everything worked again. I have yet to swap the sound card out but it is on my to-do list with this computer eventually. Until then any help would great. I am using a comp with Feisty Fawn a Pentium D, 2gigs of ram, and an ATI X1950 Pro, with the fix applied. Here is a copy of my current ps aux, which is pretty program light as of the moment. MP3 codecs have been installed.

Also if it is of any concern I also experience 'mini-freezes' on large amounts of app usage and small amounts of app usage. The mouse will usually freeze up for seconds or halves there of. 
[LEFT]
         1  0.1  0.0   2912  1844 ?        Ss   03:25   0:01 /sbin/init
         2  0.0  0.0      0     0 ?        S    03:25   0:00 [migration/0]
         3  0.0  0.0      0     0 ?        SN   03:25   0:00 [ksoftirqd/0]
         4  0.0  0.0      0     0 ?        S    03:25   0:00 [watchdog/0]
        5  0.0  0.0      0     0 ?        S    03:25   0:00 [migration/1]
        6  0.0  0.0      0     0 ?        SN   03:25   0:00 [ksoftirqd/1]
        7  0.0  0.0      0     0 ?        S    03:25   0:00 [watchdog/1]
        8  0.0  0.0      0     0 ?        S<   03:25   0:00 [events/0]
      9  0.0  0.0      0     0 ?        S<   03:25   0:00 [events/1]
       10  0.0  0.0      0     0 ?        S<   03:25   0:00 [khelper]
        11  0.0  0.0      0     0 ?        S<   03:25   0:00 [kthread]
        35  0.0  0.0      0     0 ?        S<   03:25   0:00 [kblockd/0]
      36  0.0  0.0      0     0 ?        S<   03:25   0:00 [kblockd/1]
        37 78.5  0.0      0     0 ?        R<   03:25  12:03 [kacpid]
       38 20.9  0.0      0     0 ?        S<   03:25   3:12 [kacpi_notify]
       138  0.0  0.0      0     0 ?        S<   03:25   0:00 [kseriod]
       165  0.0  0.0      0     0 ?        S    03:25   0:00 [pdflush]
       166  0.0  0.0      0     0 ?        S    03:25   0:00 [pdflush]
      167  0.0  0.0      0     0 ?        S<   03:25   0:00 [kswapd0]
       168  0.0  0.0      0     0 ?        S<   03:25   0:00 [aio/0]
       169  0.0  0.0      0     0 ?        S<   03:25   0:00 [aio/1]
       802  0.0  0.0      0     0 ?        S    03:25   0:00 [kirqd]
      2069  0.0  0.0      0     0 ?        S<   03:25   0:00 [ksuspend_usbd]
     2072  0.0  0.0      0     0 ?        S<   03:25   0:00 [khubd]
     2085  0.0  0.0      0     0 ?        S<   03:25   0:00 [ata/0]
      2086  0.0  0.0      0     0 ?        S<   03:25   0:00 [ata/1]
      2087  0.0  0.0      0     0 ?        S<   03:25   0:00 [ata_aux]
      2092  0.0  0.0      0     0 ?        S<   03:25   0:00 [scsi_eh_0]
      2093  0.0  0.0      0     0 ?        S<   03:25   0:00 [scsi_eh_1]
      2102  0.0  0.0      0     0 ?        S<   03:25   0:00 [khpsbpkt]
     2149  0.0  0.0      0     0 ?        S<   03:25   0:00 [scsi_eh_2]
      2150  0.0  0.0      0     0 ?        S<   03:25   0:00 [scsi_eh_3]
      2165  0.0  0.0      0     0 ?        S<   03:25   0:00 [knodemgrd_0]
      2316  0.0  0.0      0     0 ?        S<   03:25   0:00 [kjournald]
      2515  0.0  0.0   2872  1216 ?        S<s  03:25   0:00 /sbin/udevd --d
      3544  0.0  0.0      0     0 ?        S<   03:25   0:00 [kpsmoused]
      3678  0.0  0.0      0     0 ?        S<   03:25   0:00 [hda_codec]
      4011  0.0  0.0      0     0 ?        S<   03:25   0:00 [kjournald]
      4013  0.0  0.0      0     0 ?        S<   03:25   0:00 [kjournald]
      4219  0.0  0.0      0     0 ?        S    03:25   0:00 [wrap_wq]
     4220  0.0  0.0      0     0 ?        S    03:25   0:00 [ntos_wq]
     4221  0.0  0.0      0     0 ?        S    03:25   0:00 [ndis_wq]
     4260  0.0  0.0      0     0 ?        S<   03:25   0:00 [windisdrvr]
      4261  0.0  0.0      0     0 ?        S<   03:25   0:00 [windisdrvr]
      4415  0.0  0.0   1652   512 tty4     Ss+  03:25   0:00 /sbin/getty 384
      4416  0.0  0.0   1652   508 tty5     Ss+  03:25   0:00 /sbin/getty 384
      4420  0.0  0.0   1652   512 tty2     Ss+  03:25   0:00 /sbin/getty 384
      4421  0.0  0.0   1648   508 tty3     Ss+  03:25   0:00 /sbin/getty 384
      4422  0.0  0.0   1648   508 tty1     Ss+  03:25   0:00 /sbin/getty 384
      4423  0.0  0.0   1652   512 tty6     Ss+  03:25   0:00 /sbin/getty 384
      4686  0.0  0.0   2256  1172 ?        Ss   03:25   0:00 /usr/sbin/acpid
      4797  0.0  0.0   1704   664 ?        Ss   03:25   0:00 /sbin/syslogd
      4851  0.0  0.0   1792   520 ?        Ss   03:25   0:00 /bin/dd bs 1 if
      4853  0.0  0.0   2428  1376 ?        Ss   03:25   0:00 /sbin/klogd -P
       4874  0.0  0.0   2848  1088 ?        Ss   03:25   0:00 /usr/bin/dbus-d
       4890  0.3  0.4  10792  9100 ?        Ss   03:25   0:03 /usr/sbin/hald
      4891  0.0  0.0   2876  1024 ?        S    03:25   0:00 hald-runner
       4897  0.0  0.0   2104   888 ?        S    03:25   0:00 hald-addon-acpi
      4898  0.0  0.0   2936  1092 ?        S    03:25   0:00 /usr/lib/hal/ha
       4905  0.0  0.0   2104   904 ?        S    03:25   0:00 hald-addon-keyb
       4914  0.0  0.0   2104   900 ?        S    03:25   0:00 hald-addon-keyb
       4917  0.0  0.0   2104   900 ?        S    03:25   0:00 hald-addon-keyb
       4931  0.0  0.0   2100   960 ?        S    03:25   0:00 hald-addon-stor
      4945  0.2  0.0   1944   844 ?        Ss   03:25   0:02 /usr/sbin/dhcdb
      4960  0.0  0.1  29744  2132 ?        Ssl  03:25   0:00 /usr/sbin/Netwo
     4978  0.0  0.0   2668  1368 ?        Ss   03:25   0:00 avahi-daemon: r
     4979  0.0  0.0   2668   460 ?        Ss   03:25   0:00 avahi-daemon: c
      4995  0.0  0.0   3060  1264 ?        Ss   03:25   0:00 /usr/sbin/Netwo
      5008  0.0  0.0   2872   804 ?        Ss   03:25   0:00 /usr/bin/system
      5009  0.0  0.0   2716  1220 ?        S    03:25   0:00 dbus-daemon --s
      5060  0.0  0.0  12216  1412 ?        Ss   03:25   0:00 /usr/sbin/gdm
      5063  0.0  0.1  12576  2392 ?        S    03:25   0:00 /usr/sbin/gdm
      5066  3.5  1.8  52304 38512 tty7     SLs+ 03:25   0:31 /usr/X11R6/bin/
      5132  0.0  0.0   6416   832 ?        Ss   03:25   0:00 /usr/sbin/hpiod
     5153  0.0  0.2  10056  4992 ?        S    03:25   0:00 python /usr/sbi
      5223  0.0  0.0      0     0 ?        S<   03:25   0:00 [kondemand/0]
      5224  0.0  0.0      0     0 ?        S<   03:25   0:00 [kondemand/1]
      5263  0.0  0.0   2700  1000 ?        Ss   03:25   0:00 /usr/sbin/hcid
      5283  0.0  0.0      0     0 ?        S<   03:25   0:00 [krfcommd]
    5318  0.0  0.0   1912   424 ?        Ss   03:25   0:00 /usr/sbin/atd
      5332  0.0  0.0   2280   892 ?        Ss   03:25   0:00 /usr/sbin/cron
  5435  0.0  0.5  30044 10968 ?        Ssl  03:25   0:00 x-session-manag
  5475  0.0  0.0   4256   528 ?        Ss   03:25   0:00 /usr/bin/ssh-ag
  5478  0.0  0.0   2664   636 ?        S    03:25   0:00 /usr/bin/dbus-l
  5479  0.0  0.0   2848  1036 ?        Ss   03:25   0:00 /usr/bin/dbus-d
  5481  0.0  0.2   6600  4168 ?        S    03:25   0:00 /usr/lib/libgco
  5484  0.0  0.0   2760  1068 ?        S    03:25   0:00 /usr/bin/gnome-
  5486  0.1  0.4  29500  9860 ?        Sl   03:25   0:00 /usr/lib/contro
  5497  0.0  0.0   1716   484 ?        Ss   03:25   0:00 /bin/sh -c /usr
  5498  0.0  0.1   4824  3024 ?        S    03:25   0:00 /usr/bin/esd -t
  5504  0.0  0.4  15312  8312 ?        S    03:25   0:00 /usr/bin/metaci
  5507  0.3  1.0  42944 21164 ?        S    03:25   0:02 gnome-panel --s
  5510  0.1  0.8  74716 17476 ?        S    03:25   0:01 nautilus --no-d
  5516  0.0  0.1  39620  3164 ?        Ssl  03:25   0:00 /usr/lib/bonobo
  5519  0.0  0.1   8476  3496 ?        S    03:25   0:00 /usr/lib/gnome-
  5520  0.0  0.2  18820  4788 ?        Ss   03:25   0:00 gnome-volume-ma
  5525  0.0  0.5  31100 11884 ?        S    03:25   0:00 update-notifier
  5534  0.0  0.4  26804  9336 ?        Sl   03:25   0:00 /usr/lib/evolut
       5561  0.0  0.0   1900   760 ?        S<s  03:25   0:00 avahi-autoipd: 
      5562  0.0  0.0   1688   352 ?        S<s  03:25   0:00 avahi-autoipd: 
  5565  0.1  0.5  30796 12000 ?        S    03:25   0:01 nm-applet --sm-
  5570  0.0  0.3  39932  8128 ?        S    03:25   0:00 gnome-cups-icon
  5572  0.0  0.4  61496  8712 ?        S    03:25   0:00 /usr/lib/gnome-
  5573  0.1  0.2  28636  5780 ?        Ss   03:25   0:01 gnome-power-man
  5589  0.0  0.0   2456   880 ?        S    03:25   0:00 /usr/lib/nautil
 5633  0.4  0.5  32328 12288 ?        S    03:26   0:03 /usr/lib/gnome-
  5637  0.0  0.5  28252 10700 ?        S    03:26   0:00 /usr/lib/notifi
     5647  0.0  0.0   2448   776 ?        S<s  03:26   0:00 dhclient3 -pf /
  5668  0.1  0.1  15896  2296 ?        Ss   03:26   0:01 gnome-screensav
      5682  0.0  0.0   3784  1448 ?        S    03:26   0:00 /sbin/wpa_suppl
      5684  0.0  0.0   2452  1212 ?        S    03:26   0:00 /sbin/dhclient
  5758 11.3  4.0 213492 84768 ?        Sl   03:26   1:32 /usr/lib/firefo
  5854  0.1  0.7  54640 16056 ?        Sl   03:28   0:00 gnome-terminal
  5857  0.0  0.0   2460   736 ?        S    03:28   0:00 gnome-pty-helpe
  5858  0.0  0.1   5584  3108 pts/0    Ss   03:28   0:00 bash
    6028  0.0  0.0   4688  1840 ?        SNs  03:30   0:00 /usr/sbin/cupsd
  6254  0.0  0.0   1716   476 ?        S    03:33   0:00 /bin/sh -c soun
  6255  2.1  1.0  97528 21932 ?        Sl   03:33   0:08 sound-juicer -d
  6441  0.0  0.0   2560   992 pts/0    R+   03:40   0:00 ps aux[/LEFT]

---

### Post by devosion on 2007-10-28
bump, please help

---

