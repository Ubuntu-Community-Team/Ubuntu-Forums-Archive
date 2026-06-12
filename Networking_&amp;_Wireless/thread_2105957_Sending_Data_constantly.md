---
title: "Sending Data constantly"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by vchapman on 2013-01-17
I have turned on the Systems Monitor. I have discovered that my computer is sending a constant stream of data to the router. This is occurring even when I don't think I have any programs sending to the Internet.

How do I find out what the source of this is and how do I stop it?

---

### Post by jonobr on 2013-01-17
Through a variety of tools


Find out whats running on your machine use the process command
[ps]("http://manpages.ubuntu.com/manpages/intrepid/man1/ps.1.html")

eg 
ps -A

View currently running process using the [top]("http://manpages.ubuntu.com/manpages/lucid/man1/top.1.html") command.

You could also use [netstat]("http://manpages.ubuntu.com/manpages/lucid/man8/netstat.8.html") to see what connections are being from your machine to external devices

If you want to go hardcore You could run tcpdump

```
tcpdump -v -i any 
```
and look at the actual packets

All of this will be done in a terminal window, 
You do need to know what your looking for and when you find a process or port your not familiar with, you can research that and find out what its doing.


The machine will always be sending packets here or there for some reason or other, but checking the above will ensure no problems

---

### Post by vchapman on 2013-01-17
Here is the output from the first command:

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:07 ksoftirqd/0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 cpuset
    9 ?        00:00:00 khelper
   10 ?        00:00:00 kdevtmpfs
   11 ?        00:00:00 netns
   12 ?        00:00:00 sync_supers
   13 ?        00:00:00 bdi-default
   14 ?        00:00:00 kintegrityd
   15 ?        00:00:00 kblockd
   16 ?        00:00:00 ata_sff
   17 ?        00:00:00 khubd
   18 ?        00:00:00 md
   21 ?        00:00:00 khungtaskd
   22 ?        00:00:00 kswapd0
   23 ?        00:00:00 ksmd
   24 ?        00:00:00 khugepaged
   25 ?        00:00:00 fsnotify_mark
   26 ?        00:00:00 ecryptfs-kthrea
   27 ?        00:00:00 crypto
   35 ?        00:00:00 kthrotld
   37 ?        00:00:00 scsi_eh_0
   38 ?        00:00:00 scsi_eh_1
   61 ?        00:00:00 devfreq_wq
   71 ?        00:00:00 scsi_eh_2
   73 ?        00:00:00 usb-storage
  228 ?        00:00:00 jbd2/sda5-8
  229 ?        00:00:00 ext4-dio-unwrit
  316 ?        00:00:00 upstart-udev-br
  319 ?        00:00:00 udevd
  540 ?        00:00:00 mount.ntfs
  566 ?        00:00:00 mount.ntfs
  575 ?        00:00:00 cfg80211
  576 ?        00:00:00 kpsmoused
  587 ?        00:00:00 mount.ntfs
  618 ?        00:00:00 mount.ntfs
  661 ?        00:00:00 udevd
  673 ?        00:00:00 udevd
  756 ?        00:00:00 flush-8:0
  761 ?        00:00:00 ttm_swap
  792 ?        00:00:01 dbus-daemon
  831 ?        00:00:00 bluetoothd
  845 ?        00:00:01 rsyslogd
  861 ?        00:00:00 krfcommd
  872 ?        00:00:00 smbd
  873 ?        00:00:00 avahi-daemon
  874 ?        00:00:00 avahi-daemon
  884 ?        00:00:00 modem-manager
  890 ?        00:00:00 smbd
  895 ?        00:00:01 NetworkManager
  896 ?        00:00:00 cupsd
  904 ?        00:00:00 polkitd
  910 ?        00:00:00 colord
  917 ?        00:00:00 upstart-socket-
  923 ?        00:00:01 wpa_supplicant
  979 tty4     00:00:00 getty
  986 tty5     00:00:00 getty
  999 tty2     00:00:00 getty
 1001 tty3     00:00:00 getty
 1006 tty6     00:00:00 getty
 1019 ?        00:00:00 acpid
 1022 ?        00:00:00 cron
 1023 ?        00:00:00 atd
 1025 ?        00:00:00 winbindd
 1029 ?        00:00:00 winbindd
 1032 ?        00:00:00 whoopsie
 1033 ?        00:00:00 lightdm
 1075 tty7     00:12:08 Xorg
 1196 ?        00:00:00 lightdm
 1223 ?        00:00:00 accounts-daemon
 1285 tty1     00:00:00 getty
 1322 ?        00:00:00 nmbd
 1348 ?        00:00:00 console-kit-dae
 1423 ?        00:00:00 gnome-session
 1459 ?        00:00:00 ssh-agent
 1462 ?        00:00:00 dbus-launch
 1463 ?        00:00:06 dbus-daemon
 1472 ?        00:00:03 gnome-settings-
 1474 ?        00:00:00 gnome-keyring-d
 1484 ?        00:00:00 upowerd
 1540 ?        00:00:00 gvfsd
 1550 ?        00:00:00 gvfs-fuse-daemo
 1630 ?        00:01:04 metacity
 1634 ?        00:00:00 gconfd-2
 1643 ?        00:09:02 pulseaudio
 1645 ?        00:00:00 rtkit-daemon
 1646 ?        00:00:05 unity-2d-panel
 1647 ?        00:00:29 unity-2d-shell
 1657 ?        00:00:00 gconf-helper
 1695 ?        00:00:03 nautilus
 1701 ?        00:00:00 gnome-fallback-
 1702 ?        00:00:00 bluetooth-apple
 1716 ?        00:00:02 nm-applet
 1717 ?        00:00:00 polkit-gnome-au
 1720 ?        00:00:03 udisks-daemon
 1721 ?        00:00:00 udisks-daemon
 1728 ?        00:00:04 bamfdaemon
 1757 ?        00:00:01 gvfs-gdu-volume
 1778 ?        00:00:00 gvfs-gphoto2-vo
 1780 ?        00:00:01 gvfs-afc-volume
 1783 ?        00:00:09 unity-panel-ser
 1788 ?        00:00:00 indicator-sound
 1792 ?        00:00:00 indicator-print
 1794 ?        00:00:00 indicator-sessi
 1810 ?        00:00:00 indicator-appli
 1829 ?        00:00:00 gvfsd-trash
 1839 ?        00:00:00 geoclue-master
 1841 ?        00:00:00 ubuntu-geoip-pr
 1843 ?        00:00:00 dconf-service
 1849 ?        00:00:00 indicator-messa
 1851 ?        00:00:00 indicator-datet
 1875 ?        00:00:00 gvfsd-burn
 1886 ?        00:00:00 gdu-notificatio
 1904 ?        00:00:00 gvfsd-metadata
 1911 ?        00:00:03 hud-service
 1912 ?        00:00:00 telepathy-indic
 1931 ?        00:00:01 unity-applicati
 1933 ?        00:00:00 unity-files-dae
 1935 ?        00:00:00 unity-music-dae
 1937 ?        00:00:00 unity-lens-vide
 1944 ?        00:00:00 mission-control
 1970 ?        00:00:00 goa-daemon
 1972 ?        00:00:00 zeitgeist-daemo
 1980 ?        00:00:00 zeitgeist-fts
 1984 ?        00:00:00 zeitgeist-datah
 1985 ?        00:00:00 cat
 2009 ?        00:00:00 gnome-screensav
 2012 ?        00:00:00 unity-musicstor
 2027 ?        00:00:01 unity-scope-vid
 2043 ?        00:17:20 gnome-system-mo
 2067 ?        00:00:03 ubuntuone-syncd
 2101 ?        00:00:01 update-notifier
 2134 ?        00:00:00 deja-dup-monito
 2904 ?        00:00:01 notify-osd
 3226 ?        00:00:01 kworker/0:0
 3394 ?        00:00:00 kworker/0:2
 3411 ?        00:00:00 kworker/u:1
 3419 ?        00:00:00 kworker/u:2
 3431 ?        00:00:00 dnsmasq
 3496 ?        00:00:04 gnome-terminal
 3505 ?        00:00:00 gnome-pty-helpe
 3506 pts/0    00:00:00 bash
 3561 ?        00:00:00 kworker/0:1
 3563 ?        00:00:00 kworker/u:0
 3566 ?        00:00:00 winbindd
 3582 pts/0    00:00:00 ps

Is one of these processes causing my problem?

---

### Post by chadk5utc on 2013-01-17
in terminal the top command will show which process is using the most memory and the command iftop will show if there are any active connections and the data they are sending. I think top is installed by default but I think youll have to install iftop.

---

### Post by jonobr on 2013-01-17
top is on there already,
nothing unusual in ps,
check the other commands I gave you including top.

nestat will show you connections made to remote machines,
you should be able to see if whats going on is normal or not

---

### Post by vchapman on 2013-01-18
> **jonobr said:**
> 


nestat will show you connections made to remote machines,
you should be able to see if whats going on is normal or not

Here is a dump from netstat ... something is running wild, but I don't have the expertise to know what it is.


Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 Ubuntu-Vic.local:44525  In-the-basement.lo:5000 ESTABLISHED
tcp        0      0 Ubuntu-Vic.local:40009  kwaimuk.canonical:https ESTABLISHED
tcp        0      0 Ubuntu-Vic.local:34821  Apple-TV.local:5000     ESTABLISHED
tcp   433664  57920 Ubuntu-Vic.local:59753  Victors-AirPort-Exp:x11 ESTABLISHED
tcp        0      0 Ubuntu-Vic.local:44524  In-the-basement.lo:5000 ESTABLISHED
tcp        1      0 Ubuntu-Vic.local:41665  mulberry.canonical:http CLOSE_WAIT 
tcp        0      0 Ubuntu-Vic.local:44526  In-the-basement.lo:5000 ESTABLISHED
tcp   498136 314216 Ubuntu-Vic.local:49379  In-the-basement.loc:x11 ESTABLISHED
tcp        0      0 Ubuntu-Vic.local:55170  Victors-AirPort-Ex:5000 ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    9095     /var/run/wpa_supplicant/wlan0
unix  13     [ ]         DGRAM                    8932     /dev/log
unix  2      [ ]         STREAM     CONNECTED     256276   
unix  3      [ ]         STREAM     CONNECTED     235561   /home/victor/.pulse/64a501b1408633288f8fda6900000005-runtime/native
unix  3      [ ]         STREAM     CONNECTED     235560   
unix  3      [ ]         STREAM     CONNECTED     134940   
unix  3      [ ]         STREAM     CONNECTED     134939   
unix  3      [ ]         STREAM     CONNECTED     134724   @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     134723   
unix  3      [ ]         STREAM     CONNECTED     134722   @/tmp/.ICE-unix/1294
unix  3      [ ]         STREAM     CONNECTED     134721   
unix  3      [ ]         STREAM     CONNECTED     134710   @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     134709   
unix  3      [ ]         STREAM     CONNECTED     134702   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     134701   
unix  3      [ ]         STREAM     CONNECTED     134700   @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     134699   
unix  3      [ ]         STREAM     CONNECTED     95709    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     95708    
unix  3      [ ]         STREAM     CONNECTED     79685    
unix  3      [ ]         STREAM     CONNECTED     79684    
unix  3      [ ]         STREAM     CONNECTED     79681    
unix  3      [ ]         STREAM     CONNECTED     79680    
unix  3      [ ]         STREAM     CONNECTED     24190    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     24189    
unix  3      [ ]         STREAM     CONNECTED     24186    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     24185    
unix  3      [ ]         STREAM     CONNECTED     24184    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     24183    
unix  3      [ ]         STREAM     CONNECTED     16605    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16604    
unix  3      [ ]         STREAM     CONNECTED     16020    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16019    
unix  3      [ ]         STREAM     CONNECTED     16012    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     16011    
unix  3      [ ]         STREAM     CONNECTED     16003    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16002    
unix  3      [ ]         STREAM     CONNECTED     16001    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     16000    
unix  3      [ ]         STREAM     CONNECTED     13700    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13699    
unix  3      [ ]         STREAM     CONNECTED     13582    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13581    
unix  3      [ ]         STREAM     CONNECTED     13418    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13417    
unix  2      [ ]         STREAM                   13388    
unix  3      [ ]         STREAM     CONNECTED     13387    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13386    
unix  3      [ ]         STREAM     CONNECTED     13383    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13382    
unix  3      [ ]         STREAM     CONNECTED     13385    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13381    
unix  3      [ ]         STREAM     CONNECTED     13300    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13299    
unix  3      [ ]         STREAM     CONNECTED     13083    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13082    
unix  3      [ ]         STREAM     CONNECTED     13079    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13078    
unix  3      [ ]         STREAM     CONNECTED     13071    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13070    
unix  3      [ ]         STREAM     CONNECTED     13069    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13068    
unix  3      [ ]         STREAM     CONNECTED     13067    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13066    
unix  3      [ ]         STREAM     CONNECTED     13063    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13062    
unix  3      [ ]         STREAM     CONNECTED     13059    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13058    
unix  3      [ ]         STREAM     CONNECTED     13057    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     13056    
unix  3      [ ]         STREAM     CONNECTED     12998    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12997    
unix  3      [ ]         STREAM     CONNECTED     12996    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12995    
unix  3      [ ]         STREAM     CONNECTED     12992    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12991    
unix  3      [ ]         STREAM     CONNECTED     12988    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12987    
unix  3      [ ]         STREAM     CONNECTED     12977    
unix  3      [ ]         STREAM     CONNECTED     12976    
unix  3      [ ]         STREAM     CONNECTED     12970    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12969    
unix  3      [ ]         STREAM     CONNECTED     12967    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12966    
unix  3      [ ]         STREAM     CONNECTED     12965    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12964    
unix  3      [ ]         STREAM     CONNECTED     12936    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12935    
unix  3      [ ]         STREAM     CONNECTED     12934    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12933    
unix  2      [ ]         DGRAM                    12930    
unix  3      [ ]         STREAM     CONNECTED     12922    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12921    
unix  3      [ ]         STREAM     CONNECTED     12920    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12919    
unix  3      [ ]         STREAM     CONNECTED     12908    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12907    
unix  3      [ ]         STREAM     CONNECTED     12909    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12906    
unix  3      [ ]         STREAM     CONNECTED     12901    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12900    
unix  3      [ ]         STREAM     CONNECTED     12855    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12854    
unix  3      [ ]         STREAM     CONNECTED     12853    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12851    
unix  3      [ ]         STREAM     CONNECTED     12849    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12823    
unix  3      [ ]         STREAM     CONNECTED     12793    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12792    
unix  3      [ ]         STREAM     CONNECTED     12791    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12788    
unix  3      [ ]         STREAM     CONNECTED     12742    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12741    
unix  3      [ ]         STREAM     CONNECTED     12740    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12730    
unix  3      [ ]         STREAM     CONNECTED     12615    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12614    
unix  3      [ ]         STREAM     CONNECTED     12611    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12609    
unix  3      [ ]         STREAM     CONNECTED     12608    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12607    
unix  3      [ ]         STREAM     CONNECTED     12558    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12557    
unix  3      [ ]         STREAM     CONNECTED     12554    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12553    
unix  3      [ ]         STREAM     CONNECTED     12426    @/dbus-vfs-daemon/socket-fLELKH9w
unix  3      [ ]         STREAM     CONNECTED     12425    
unix  3      [ ]         STREAM     CONNECTED     12424    @/dbus-vfs-daemon/socket-a6FVykzJ
unix  3      [ ]         STREAM     CONNECTED     12423    
unix  3      [ ]         STREAM     CONNECTED     12394    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12393    
unix  3      [ ]         STREAM     CONNECTED     12320    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12319    
unix  3      [ ]         STREAM     CONNECTED     12310    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12309    
unix  3      [ ]         STREAM     CONNECTED     12308    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12307    
unix  3      [ ]         STREAM     CONNECTED     12305    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12304    
unix  3      [ ]         STREAM     CONNECTED     12267    @/dbus-vfs-daemon/socket-wDe4P6YM
unix  3      [ ]         STREAM     CONNECTED     12266    
unix  3      [ ]         STREAM     CONNECTED     12265    @/dbus-vfs-daemon/socket-RuptzsiI
unix  3      [ ]         STREAM     CONNECTED     12264    
unix  3      [ ]         STREAM     CONNECTED     12260    @/dbus-vfs-daemon/socket-PDHfLS3g
unix  3      [ ]         STREAM     CONNECTED     12259    
unix  3      [ ]         STREAM     CONNECTED     12261    @/dbus-vfs-daemon/socket-RGxgfTBK
unix  3      [ ]         STREAM     CONNECTED     12258    
unix  3      [ ]         STREAM     CONNECTED     12253    @/tmp/.ICE-unix/1294
unix  3      [ ]         STREAM     CONNECTED     12252    
unix  3      [ ]         STREAM     CONNECTED     12240    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12239    
unix  3      [ ]         STREAM     CONNECTED     12238    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12237    
unix  3      [ ]         STREAM     CONNECTED     12226    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12222    
unix  3      [ ]         STREAM     CONNECTED     12223    /tmp/keyring-mwPYs9/pkcs11
unix  3      [ ]         STREAM     CONNECTED     12221    
unix  3      [ ]         STREAM     CONNECTED     12189    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12188    
unix  3      [ ]         STREAM     CONNECTED     12186    @/dbus-vfs-daemon/socket-CNNmthQb
unix  3      [ ]         STREAM     CONNECTED     12185    
unix  3      [ ]         STREAM     CONNECTED     12187    @/dbus-vfs-daemon/socket-sieoxf3q
unix  3      [ ]         STREAM     CONNECTED     12184    
unix  3      [ ]         STREAM     CONNECTED     12181    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12180    
unix  3      [ ]         STREAM     CONNECTED     12173    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12172    
unix  3      [ ]         STREAM     CONNECTED     12171    /home/victor/.pulse/64a501b1408633288f8fda6900000005-runtime/native
unix  3      [ ]         STREAM     CONNECTED     12170    
unix  3      [ ]         STREAM     CONNECTED     12106    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12105    
unix  3      [ ]         STREAM     CONNECTED     12104    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12103    
unix  3      [ ]         STREAM     CONNECTED     12102    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12101    
unix  3      [ ]         STREAM     CONNECTED     12095    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12094    
unix  3      [ ]         STREAM     CONNECTED     12091    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12090    
unix  3      [ ]         STREAM     CONNECTED     12071    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12070    
unix  3      [ ]         STREAM     CONNECTED     12068    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12067    
unix  3      [ ]         STREAM     CONNECTED     12064    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12063    
unix  3      [ ]         STREAM     CONNECTED     12060    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12057    
unix  3      [ ]         STREAM     CONNECTED     12046    @/dbus-vfs-daemon/socket-pLMzuVZX
unix  3      [ ]         STREAM     CONNECTED     12045    
unix  3      [ ]         STREAM     CONNECTED     12047    @/dbus-vfs-daemon/socket-CrGBbGMg
unix  3      [ ]         STREAM     CONNECTED     12044    
unix  3      [ ]         STREAM     CONNECTED     12011    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12010    
unix  3      [ ]         STREAM     CONNECTED     12005    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     12004    
unix  3      [ ]         STREAM     CONNECTED     12002    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11998    
unix  3      [ ]         STREAM     CONNECTED     11979    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11978    
unix  3      [ ]         STREAM     CONNECTED     11970    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11969    
unix  3      [ ]         STREAM     CONNECTED     11967    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11965    
unix  3      [ ]         STREAM     CONNECTED     11925    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11924    
unix  3      [ ]         STREAM     CONNECTED     11914    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11913    
unix  3      [ ]         STREAM     CONNECTED     11912    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11911    
unix  3      [ ]         STREAM     CONNECTED     11910    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11908    
unix  3      [ ]         STREAM     CONNECTED     11909    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11907    
unix  3      [ ]         STREAM     CONNECTED     11902    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11901    
unix  3      [ ]         STREAM     CONNECTED     11893    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11892    
unix  3      [ ]         STREAM     CONNECTED     11887    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11886    
unix  3      [ ]         STREAM     CONNECTED     11881    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11878    
unix  3      [ ]         STREAM     CONNECTED     11875    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11874    
unix  3      [ ]         STREAM     CONNECTED     11864    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11862    
unix  3      [ ]         STREAM     CONNECTED     11856    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11855    
unix  3      [ ]         STREAM     CONNECTED     11850    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11849    
unix  3      [ ]         STREAM     CONNECTED     11829    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11828    
unix  3      [ ]         STREAM     CONNECTED     11827    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11826    
unix  3      [ ]         STREAM     CONNECTED     11825    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11824    
unix  3      [ ]         STREAM     CONNECTED     11823    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11822    
unix  3      [ ]         STREAM     CONNECTED     11819    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11818    
unix  3      [ ]         STREAM     CONNECTED     11813    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11812    
unix  3      [ ]         STREAM     CONNECTED     11811    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11810    
unix  3      [ ]         STREAM     CONNECTED     11801    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11800    
unix  3      [ ]         STREAM     CONNECTED     11799    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11796    
unix  3      [ ]         STREAM     CONNECTED     11789    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11788    
unix  3      [ ]         STREAM     CONNECTED     11775    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11774    
unix  3      [ ]         STREAM     CONNECTED     11758    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11757    
unix  3      [ ]         STREAM     CONNECTED     11756    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11755    
unix  3      [ ]         STREAM     CONNECTED     11754    @/tmp/dbus-DjFEVqAYwT
unix  3      [ ]         STREAM     CONNECTED     11753    
unix  2      [ ]         DGRAM                    11750    
unix  3      [ ]         STREAM     CONNECTED     11746    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11745    
unix  3      [ ]         STREAM     CONNECTED     11743    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11742

---

### Post by dodo3773 on 2013-01-18
What is the output of this command?:

```

ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $1}' && ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $2}'

```

Also please use code tags. It makes it easier to read your output.

---

### Post by vchapman on 2013-01-18
> **dodo3773 said:**
> What is the output of this command?:

```

ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $1}' && ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $2}'

```

Also please use code tags. It makes it easier to read your output.

```


:~$ ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $1}' && ps -o cmd= -p $(lsof -i -n -P | sed 1d | awk '{print $2}' | uniq) | awk '{print $2}'
/usr/bin/pulseaudio
/usr/lib/ubuntu-geoip/ubuntu-geoip-provider
/usr/bin/python
/usr/lib/chromium-browser/chromium-browser
/usr/lib/chromium-browser/chromium-browser
--start

/usr/lib/ubuntuone-client/ubuntuone-syncdaemon

--type=plugin



```

---

### Post by dodo3773 on 2013-01-18
Looks like you have a few things sending data (or just waiting with an established connection(which will send a little data)) like ubuntuone and chromium. I am assuming chromium is so you can post here to the forums though. Also, from your previous output there is I am guessing an appletv on your network? May be a network service running connecting to it like network discovery (avahi or similar). Try disabling ubuntuone and any additional network services you don't need / use and see if that helps.

---

### Post by jonobr on 2013-01-18
Anything that says "established" is a connection from your device to another target

So, even when you think there is nothing going on there, there are active connections
As dodo3773 said Appletv is an obvious one, but there is one to your airport also ( Victors-AirPort-Ex:)
These things are most likely always open, passing packets and generally nothing to worry about.
 In-the-basement.lo also seems like another active connection , but the port 5000 is nothing I recognize, mind you I did see a post saying Yahoo messenger, but again, I dont think its tied to that.


@/tmp/dbus- and lots of it, seems to be another interesting thing, but doing a bit of research i notice [This]("https://bugs.freedesktop.org/show_bug.cgi?id=38656") post which is for solaris but  mentions
> it always leaves /tmp/dbus-XXX socket files.  Each time a user logs in it leaves one socket file for the "gdm" user and another for the user who just logged out.  

This is likely not an issue for Linux since abstract sockets are used in that environment.  However, it seems nicer to make D-Bus properly clean things up on shutdown like this. 

So again, Im not really sure there is something to be worried about here from your netstat connections.
There maybe something that is happening at other times that is causing huge traffic.
A good example would be network HP printers,
I mention this as I saw this myself.
Thing was always broadcasting and shouting, but again, its jsut the way that product worked.

---

### Post by vchapman on 2013-01-18
Well this is becoming more interesting all the time. I have had my suspicions that this is some how tied into rhythmbox. So I deleted all of the plugins that I could find. This did not fix the problem. However, when I went into the sound settings I discovered that my 2 Airport Expresses and my Apple TV on the network are considered to be output devices. 

I have no idea how this happened. How would you suggest that I remove these as sound output devices?

---

### Post by jonobr on 2013-01-18
Ok,

Im not a sound or Appletv expert.

All I know is when I try to play songs on my TV from my iphone using Airplay, it wont work unless I have itunes open.

When I saw how that worked, I figured that the Iphone is not playing songs on the TV but streaming to the TV from Itunes.
Wouldnt that be an output device in that case?

Again, totally outside my wheelhouse now

---

### Post by vchapman on 2013-01-18
> **vchapman said:**
> 
I have no idea how this happened. How would you suggest that I remove these as sound output devices?

I did figure out how to do this and .....


my problem went away.

Thank you for your help.

---

