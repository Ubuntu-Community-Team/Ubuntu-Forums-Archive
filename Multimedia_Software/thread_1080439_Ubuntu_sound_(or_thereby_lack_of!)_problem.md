---
title: "Ubuntu sound (or thereby lack of!) problem"
date: 2009-02-25
forum: Multimedia Software
---

### Post by beak02 on 2009-02-25
Hi

I've been messing about with media players on ubuntu 8.10 and i've stumbled apon a slight problem.  My sound has stopped working.  I rebooted and it worked fine but halfway through a track Amorak said:

"Cannot start audio; the device is busy
xine parameter"

I've been looking for a way to uninstall xine but i can't find one and it isn't in the application manager.

Any help would be much appreciated

Luke

---

### Post by opscure on 2009-02-25
To remove xine:
```
sudo apt-get remove xine
```

To check if xine is actually causing your problem:
```
ps aux|grep xine
```
if xine is listed along with the grep process then:
```
sudo killall xine
```
and see if your audio comes back to life.

---

### Post by beak02 on 2009-02-25
No Luck

The apt-get remove claims that xine isn't installed but I can quite clearly see (and run) it from the applications menu.

ps aux|grep xine returns
"7472  0.0  0.0   3240   792 pts/0    R+   19:23   0:00 grep xine"

and the killall claims that no 'xine' processes are running

If I'm wrong about xine being the problem (which is quite possible as I have minimal linux experience) does anyone know of anything else that will prevent the sound from working?

Thanks in advance

Luke

---

### Post by opscure on 2009-02-25
xine is not running according to your process listing, only the grep process that is searching for xine.  So, we can rule that out.  

Have you checked your logs in /var/log/?

Did you see any errors listed in dmesg or /var/log/messages?

We are going to need more information about what is going on when the audio stops... are you running other programs when this occurs?  Are you using youtube or any other web-based technology that may be interfering with the audio?  

You can get us a bit more info from /proc/ as well.  The easiest way to do this is to open alsamixer and hit the f2 key.  This will give you card information and help the community look for possible solutions.

If you do a 
```
ps aux>pslist.txt
```
it will output your process list to a file called pslist.txt.  Do this when the audio stops working so we can see what processes running.

---

### Post by beak02 on 2009-02-25
Right then:

I couldn't see any errors in dmesg

My sound card data from alsamixer is as follows
0 [HDMI  HDA-Intel
1 [VT82xx  HDA - Intel
2 [default USB-Audio - USB20 Camera
3 [ SAA7134 - SAA7134

the pslist is very very long, but here it is:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3056  1900 ?        Ss   21:12   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   21:12   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   21:12   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   21:12   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:12   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   21:12   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   21:12   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   21:12   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   21:12   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S<   21:12   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S<   21:12   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S<   21:12   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S<   21:12   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S<   21:12   0:00 [watchdog/3]
root        15  1.0  0.0      0     0 ?        S<   21:12   0:16 [events/0]
root        16  0.0  0.0      0     0 ?        S<   21:12   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S<   21:12   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S<   21:12   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S<   21:12   0:00 [khelper]
root        61  0.0  0.0      0     0 ?        S<   21:12   0:00 [kintegrityd/0]
root        62  0.0  0.0      0     0 ?        S<   21:12   0:00 [kintegrityd/1]
root        63  0.0  0.0      0     0 ?        S<   21:12   0:00 [kintegrityd/2]
root        64  0.0  0.0      0     0 ?        S<   21:12   0:00 [kintegrityd/3]
root        66  0.0  0.0      0     0 ?        S<   21:12   0:00 [kblockd/0]
root        67  0.0  0.0      0     0 ?        S<   21:12   0:00 [kblockd/1]
root        68  0.0  0.0      0     0 ?        S<   21:12   0:00 [kblockd/2]
root        69  0.0  0.0      0     0 ?        S<   21:12   0:00 [kblockd/3]
root        71  0.0  0.0      0     0 ?        S<   21:12   0:00 [kacpid]
root        72  0.0  0.0      0     0 ?        S<   21:12   0:00 [kacpi_notify]
root       157  0.0  0.0      0     0 ?        S<   21:12   0:00 [cqueue]
root       161  0.0  0.0      0     0 ?        S<   21:12   0:00 [kseriod]
root       215  0.0  0.0      0     0 ?        S    21:12   0:00 [pdflush]
root       216  0.0  0.0      0     0 ?        S    21:12   0:00 [pdflush]
root       217  0.0  0.0      0     0 ?        S<   21:12   0:00 [kswapd0]
root       259  0.0  0.0      0     0 ?        S<   21:12   0:00 [aio/0]
root       260  0.0  0.0      0     0 ?        S<   21:12   0:00 [aio/1]
root       261  0.0  0.0      0     0 ?        S<   21:12   0:00 [aio/2]
root       262  0.0  0.0      0     0 ?        S<   21:12   0:00 [aio/3]
root      1389  0.0  0.0      0     0 ?        S<   21:12   0:00 [ksuspend_usbd]
root      1395  0.0  0.0      0     0 ?        S<   21:12   0:00 [khubd]
root      1481  0.0  0.0      0     0 ?        S<   21:12   0:00 [ata/0]
root      1482  0.0  0.0      0     0 ?        S<   21:12   0:00 [ata/1]
root      1483  0.0  0.0      0     0 ?        S<   21:12   0:00 [ata/2]
root      1484  0.0  0.0      0     0 ?        S<   21:12   0:00 [ata/3]
root      1485  0.0  0.0      0     0 ?        S<   21:12   0:00 [ata_aux]
root      2184  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_0]
root      2186  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_1]
root      2209  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_2]
root      2210  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_3]
root      2394  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_4]
root      2395  0.0  0.0      0     0 ?        S<   21:12   0:00 [usb-storage]
root      2407  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_5]
root      2408  0.0  0.0      0     0 ?        S<   21:12   0:00 [usb-storage]
root      2410  0.0  0.0      0     0 ?        S<   21:12   0:00 [scsi_eh_6]
root      2411  0.0  0.0      0     0 ?        S<   21:12   0:00 [usb-storage]
root      2642  0.0  0.0   2536  1012 ?        S<s  21:12   0:00 /sbin/udevd --daemon
root      3194  0.0  0.0      0     0 ?        S<   21:13   0:00 [pegasus]
root      3333  0.0  0.0      0     0 ?        S<   21:13   0:00 [btaddconn]
root      3334  0.0  0.0      0     0 ?        S<   21:13   0:00 [btdelconn]
root      4321  0.0  0.0      0     0 ?        S<   21:13   0:00 [saa7133[0]]
root      5033  0.0  0.0   1780   528 tty4     Ss+  21:13   0:00 /sbin/getty 38400 tty4
root      5034  0.0  0.0   1780   524 tty5     Ss+  21:13   0:00 /sbin/getty 38400 tty5
root      5037  0.0  0.0   1780   524 tty2     Ss+  21:13   0:00 /sbin/getty 38400 tty2
root      5040  0.0  0.0   1780   520 tty3     Ss+  21:13   0:00 /sbin/getty 38400 tty3
root      5041  0.0  0.0   1780   528 tty6     Ss+  21:13   0:00 /sbin/getty 38400 tty6
root      5254  0.0  0.0   2308  1236 ?        Ss   21:13   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5298  0.0  0.0      0     0 ?        S<   21:13   0:00 [kondemand/0]
root      5299  0.0  0.0      0     0 ?        S<   21:13   0:00 [kondemand/1]
root      5300  0.0  0.0      0     0 ?        S<   21:13   0:00 [kondemand/2]
root      5301  0.0  0.0      0     0 ?        S<   21:13   0:00 [kondemand/3]
syslog    5405  0.0  0.0   2012   684 ?        Ss   21:13   0:00 /sbin/syslogd -u syslog
root      5458  0.0  0.0   1940   544 ?        S    21:13   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5460  0.0  0.1   3908  2680 ?        Ss   21:13   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5483  0.0  0.0   3148  1368 ?        Ss   21:13   0:00 /bin/dbus-daemon --system
avahi     5505  0.0  0.0   2888  1488 ?        Ss   21:13   0:00 avahi-daemon: running [lbarnes-desktop.local]
avahi     5506  0.0  0.0   2888   496 ?        Ss   21:13   0:00 avahi-daemon: chroot helper
root      5544  0.0  0.0   4244  1676 ?        Ss   21:13   0:00 /usr/sbin/atieventsd
root      5576  0.0  0.1   6428  2460 ?        Ss   21:13   0:00 /usr/sbin/cupsd
root      5731  0.0  0.0   9216  1432 ?        Ss   21:13   0:00 /usr/sbin/winbindd
root      5753  0.0  0.0   9216  1136 ?        S    21:13   0:00 /usr/sbin/winbindd
111       5754  0.0  0.2   6624  4684 ?        Ss   21:13   0:00 /usr/sbin/hald
root      5757  0.0  0.1  17480  2584 ?        Ssl  21:13   0:00 /usr/sbin/console-kit-daemon
root      5758  0.0  0.0   3364  1152 ?        S    21:13   0:00 hald-runner
root      5839  0.0  0.0   3436  1056 ?        S    21:13   0:00 hald-addon-input: Listening on /dev/input/event5 /dev/input/event6 /dev/input/event4 /dev/input/event2 /dev/input/event3 /dev/input/event1
111       5848  0.0  0.0   2296   896 ?        S    21:13   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5854  0.0  0.0   3440  1060 ?        S    21:13   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5857  0.0  0.0   3440  1056 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      5877  0.0  0.0   3440  1060 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      5880  0.0  0.0   3440  1060 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root      5883  0.0  0.0   3440  1060 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root      5886  0.0  0.0   3440  1060 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
root      5889  0.0  0.0   3440  1052 ?        S    21:13   0:00 hald-addon-storage: polling /dev/sdg (every 2 sec)
root      5947  0.0  0.0   3564  1828 ?        SLs  21:13   0:00 /usr/sbin/bluetoothd
root      5991  0.0  0.0      0     0 ?        S<   21:13   0:00 [krfcommd]
root      6014  0.0  0.1  14632  2480 ?        Ssl  21:13   0:00 /usr/sbin/NetworkManager
root      6022  0.0  0.0   4244  1324 ?        S    21:13   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      6025  0.0  0.1   6772  2964 ?        S    21:13   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      6052  0.0  0.0  14272  1792 ?        Ss   21:13   0:00 /usr/sbin/gdm
root      6055  0.0  0.1  14820  3268 ?        S    21:13   0:00 /usr/sbin/gdm
root      6060  5.4  4.6 113428 97124 tty7     Ss+  21:13   1:21 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      6076  0.0  0.0   4336  1148 ?        Ss   21:13   0:00 /usr/bin/system-tools-backends
daemon    6124  0.0  0.0   2068   460 ?        Ss   21:13   0:00 /usr/sbin/atd
root      6152  0.0  0.0   3412  1028 ?        Ss   21:13   0:00 /usr/sbin/cron
root      6172  0.0  4.6 113428 97124 tty7     S+   21:13   0:00 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      6246  0.0  0.0   1780   528 tty1     Ss+  21:13   0:00 /sbin/getty 38400 tty1
root      6249  0.0  0.0   2252   952 ?        S    21:13   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/run/dhclient-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
lbarnes   6412  0.0  0.1  14716  2180 ?        S    21:23   0:00 /usr/bin/gnome-keyring-daemon -d --login
lbarnes   6422  0.0  0.3  26224  7140 ?        Ssl  21:23   0:00 x-session-manager
lbarnes   6480  0.0  0.0   3124   684 ?        S    21:23   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
lbarnes   6481  0.0  0.0   3036  1284 ?        Ss   21:23   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
lbarnes   6492  0.0  0.2   8192  5192 ?        S    21:23   0:00 /usr/lib/libgconf2-4/gconfd-2
lbarnes   6498  0.0  0.3  19212  7524 ?        Ss   21:23   0:00 /usr/bin/seahorse-agent --execute x-session-manager
lbarnes   6502  0.0  0.1   5564  2176 ?        S    21:23   0:00 /usr/lib/gvfs/gvfsd
lbarnes   6508  0.0  0.1  37528  2084 ?        Ssl  21:23   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/lbarnes/.gvfs
lbarnes   6515  0.0  0.1  13952  3664 ?        S    21:23   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
lbarnes   6518  0.1  1.0  60840 21700 ?        Ssl  21:23   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
lbarnes   6520  0.3  0.2  13772  4588 ?        S    21:23   0:02 /usr/lib/at-spi/at-spi-registryd
lbarnes   6522  0.0  0.1  41720  3568 ?        Ssl  21:23   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=13
lbarnes   6529  0.0  0.0   1844   552 ?        S    21:23   0:00 /bin/sh /usr/bin/compiz
lbarnes   6579  0.2  0.1  22024  3412 ?        Ss   21:23   0:02 gnome-screensaver
lbarnes   6607  0.5  0.6  22100 14448 ?        S    21:23   0:05 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering core ccp
lbarnes   6608  0.0  0.0   1844   488 ?        Ss   21:23   0:00 /bin/sh -c /usr/bin/compiz-decorator
lbarnes   6609  0.0  0.0   1844   524 ?        S    21:23   0:00 /bin/sh /usr/bin/compiz-decorator
lbarnes   6611  0.1  0.6  22448 13492 ?        S    21:23   0:01 /usr/bin/gtk-window-decorator
lbarnes   6612  0.5  1.1  38448 22972 ?        S    21:23   0:04 gnome-panel
lbarnes   6614  0.7  1.8  80800 37800 ?        S    21:23   0:06 nautilus --no-desktop --browser
lbarnes   6621  0.0  0.1  14384  3192 ?        Sl   21:23   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
lbarnes   6623  0.0  0.1   5800  2324 ?        S    21:23   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
lbarnes   6629  0.0  0.1  15032  2784 ?        S    21:23   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
lbarnes   6632  0.0  0.5  24060 11340 ?        S    21:23   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=22
lbarnes   6641  0.0  0.1   5564  2220 ?        S    21:23   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
lbarnes   6670  0.0  0.7  27644 15044 ?        S    21:23   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=23
lbarnes   6675  0.0  0.8  46188 17056 ?        Sl   21:23   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=30
lbarnes   6690  0.0  0.5  32572 10488 ?        SNl  21:23   0:00 trackerd
lbarnes   6691  0.0  0.7  28392 16032 ?        S    21:23   0:00 update-notifier
lbarnes   6693  0.0  0.5  57908 11256 ?        Sl   21:23   0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
lbarnes   6694  0.0  0.0   1844   496 ?        S    21:23   0:00 /bin/sh /usr/bin/blueproximity
lbarnes   6695  0.0  0.5  20448 10504 ?        S    21:23   0:00 bluetooth-applet
lbarnes   6696  0.8  0.9  39076 20436 ?        Sl   21:23   0:07 python /usr/share/blueproximity/proximity.py
lbarnes   6702  0.0  0.6  23792 12696 ?        S    21:23   0:00 nm-applet --sm-disable
lbarnes   6707  0.0  0.7  27508 14572 ?        S    21:23   0:00 python /usr/share/system-config-printer/applet.py
lbarnes   6708  0.0  0.3  17484  7096 ?        S    21:23   0:00 tracker-applet
lbarnes   6709  0.0  0.4  24924  9340 ?        Ss   21:23   0:00 gnome-power-manager
lbarnes   6713  0.0  0.7  25152 14916 ?        S    21:23   0:00 /usr/lib/notification-daemon/notification-daemon
lbarnes   6717  0.0  0.3  61576  7428 ?        Sl   21:23   0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=30
lbarnes   6723  0.0  0.5  34344 10696 ?        Sl   21:23   0:00 /usr/lib/evolution/2.24/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=31
lbarnes   6958  0.4  1.0  40568 21564 ?        S    21:26   0:03 gedit file:///var/log/dmesg.0
root      7051  0.0  0.0   3900  1056 ?        Ss   21:27   0:00 /sbin/mount.ntfs-3g /dev/sda2 /media/Data Files -o rw,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8
root      7068  0.2  0.0   4196  1380 ?        Ss   21:27   0:01 /sbin/mount.ntfs-3g /dev/sda1 /media/disk -o rw,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8
lbarnes   7082  2.3  2.2 137132 45932 ?        Sl   21:27   0:14 amarokapp
lbarnes   7085  0.0  0.2  25444  5264 ?        Ss   21:27   0:00 kdeinit Running...                      
lbarnes   7088  0.0  0.1  25052  4056 ?        S    21:27   0:00 dcopserver [kdeinit] --nosid --suicide  
lbarnes   7091  0.0  0.2  25208  5792 ?        S    21:27   0:00 klauncher [kdeinit] --new-startup       
lbarnes   7093  0.0  0.3  26900  8252 ?        S    21:27   0:00 kded [kdeinit] --new-startup            
lbarnes   7107  0.0  0.2  25752  5372 ?        S    21:27   0:00 kio_file [kdeinit] file /tmp/ksocket-l  
lbarnes   7109  0.0  0.1   4088  2508 ?        S    21:27   0:00 ruby /usr/share/apps/amarok/scripts/score_default/score_default.rb
lbarnes   7449  0.0  0.2  19268  4316 ?        Sl   21:31   0:00 /usr/bin/alsamixergui
lbarnes   7644  0.3  1.2 101524 26000 ?        Sl   21:35   0:00 gnome-terminal
lbarnes   7649  0.0  0.0   2912   756 ?        S    21:35   0:00 gnome-pty-helper
lbarnes   7650  0.0  0.1   5840  3196 pts/0    Ss   21:35   0:00 bash
lbarnes   7794 22.3  3.9 218120 82360 ?        Sl   21:37   0:04 /usr/lib/firefox-3.0.6/firefox
lbarnes   7851  0.0  0.0   2744  1008 pts/0    R+   21:38   0:00 ps aux

It definatly seems to be a youtube thing.  I'll do some more experiments because it isn't instantly, I ran one video for 2mins whereas another crashed the sound system after 30 seconds.

Hope this helps!

Luke

---

### Post by markbuntu on 2009-02-25
If you are using amarok2, it is using phonon which needs the xine backend to work.

---

### Post by beak02 on 2009-02-28
Thanks everyone for your help, but simply re-installing Ubuntu fixed the problem.  Shows that the standard windows way of fixing anything works across operating systems!

Thanks anyway

Luke

---

