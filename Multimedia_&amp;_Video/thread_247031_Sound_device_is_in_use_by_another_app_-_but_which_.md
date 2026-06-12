---
title: "Sound device is in use by another app - but which one??"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by motin on 2006-08-30
The general sound has suddenly stopped working. XMMS looks like it is playing, but there is no sound. And I have NOT only muted the main channel... 

It happened from an update to the next basically, and all I tried since it stopped working was this tip: [http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME) but it did not help. 

Here are the error-outputs of some different apps:

Jack:
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

XMMS:
Failed to open audio device (/dev/dsp): Enhet eller resurs upptagen (Device busy...)

But now I cannot figure out which app is hogging the device!

Here is my ps aux: 

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1568   532 ?        S    09:53   0:01 init [2]
root         2  0.0  0.0      0     0 ?        S    09:53   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   09:53   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    09:53   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   09:53   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   09:53   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   09:53   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   09:53   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   09:53   0:00 [kacpid]
root       130  0.0  0.0      0     0 ?        S    09:53   0:00 [pdflush]
root       131  0.0  0.0      0     0 ?        S    09:53   0:00 [pdflush]
root       133  0.0  0.0      0     0 ?        S<   09:53   0:00 [aio/0]
root       132  0.0  0.0      0     0 ?        S    09:53   0:00 [kswapd0]
root       724  0.0  0.0      0     0 ?        S<   09:53   0:00 [kseriod]
root      1869  0.0  0.0      0     0 ?        S<   09:54   0:00 [khubd]
root      1879  0.0  0.0      0     0 ?        S    09:54   0:00 [khpsbpkt]
root      1909  0.0  0.0      0     0 ?        S    09:54   0:00 [knodemgrd_0]
root      2098  0.0  0.0      0     0 ?        S    09:54   0:00 [kjournald]
root      2388  0.0  0.0   2432   920 ?        S<s  09:54   0:00 /sbin/udevd --daemon
root      3207  0.0  0.0      0     0 ?        S    09:54   0:00 [shpchpd_event]
root      3364  0.0  0.0      0     0 ?        S    09:54   0:00 [pccardd]
root      3498  0.0  0.0      0     0 ?        S<   09:54   0:00 [ipw2200/0]
dhcp      3859  0.0  0.0   2336   572 ?        S<s  09:54   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhcroot      4329  0.0  0.0      0     0 ?        S    09:55   0:00 [kjournald]
root      4330  0.0  0.0      0     0 ?        S    09:55   0:00 [kjournald]
root      4332  0.0  0.0      0     0 ?        S    09:55   0:00 [kjournald]
root      4348  0.0  0.0      0     0 ?        S    09:55   0:00 [kjournald]
root      5070  0.0  0.1   2156  1196 ?        Ss   09:55   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5191  0.0  0.0   1680   496 ?        Ss   09:55   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5193  0.0  0.1   2400  1324 ?        Ss   09:55   0:00 /sbin/klogd -P /var/run/klogd/kmsg
104       5217  0.0  0.0   2192   896 ?        Ss   09:55   0:00 /usr/bin/dbus-daemon --system
119       5232  0.0  0.5   6988  5588 ?        Ss   09:55   0:01 /usr/sbin/hald
root      5233  0.0  0.0   2716   988 ?        S    09:55   0:00 hald-runner
119       5238  0.0  0.0   2008   796 ?        S    09:55   0:00 /usr/lib/hal/hald-addon-acpi
119       5292  0.0  0.0   2004   824 ?        S    09:55   0:00 /usr/lib/hal/hald-addon-keyboard
119       5304  0.0  0.0   2008   864 ?        S    09:55   0:00 /usr/lib/hal/hald-addon-storage
119       5305  0.0  0.0   2008   820 ?        S    09:55   0:00 /usr/lib/hal/hald-addon-storage
root      5329  0.0  0.0   1936   688 ?        Ss   09:55   0:00 /sbin/dhcdbd --system
root      5346  0.0  0.1   3928  1908 ?        Ss   09:55   0:00 /usr/sbin/NetworkManager --pid-file=/var/run/NetworkManager/Netroot      5360  0.0  0.1   2812  1064 ?        Ss   09:55   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file=/var/run/NetworkMroot      5386  0.0  0.1  10912  1800 ?        Ss   09:55   0:00 /usr/sbin/gdm
root      5387  0.0  0.2  11360  2604 ?        S    09:55   0:00 /usr/sbin/gdm
root      5390  4.3  3.6  46292 37732 tty7     Ss+  09:55   1:40 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolistehplip     5419  0.0  0.0  12868   920 ?        Ssl  09:55   0:00 /usr/sbin/hpiod
hplip     5445  0.0  0.4   9408  4672 ?        S    09:55   0:00 python /usr/sbin/hpssd
motin     5505  0.0  1.0  19932 10332 ?        Ss   09:55   0:00 /usr/bin/gnome-session
motin     5548  0.0  0.0   4332   692 ?        Ss   09:55   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usmotin     5551  0.0  0.0   2716   648 ?        S    09:55   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-sessionmotin     5552  0.0  0.0   2200   944 ?        Ss   09:55   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
motin     5554  0.0  0.4   6636  4148 ?        S    09:55   0:00 /usr/lib/libgconf2-4/gconfd-2 5
root      5556  0.0  2.4  27272 24816 ?        Ss   09:55   0:00 /usr/sbin/spamd --create-prefs --max-children 5 --helper-home-droot      5585  0.0  0.0   2080   192 ?        Ss   09:55   0:00 /usr/sbin/emifreqd
root      5598  0.0  2.2  27272 23268 ?        S    09:55   0:00 spamd child
root      5599  0.0  2.2  27272 23172 ?        S    09:55   0:00 spamd child
motin     5600  0.0  0.0   2344   728 ?        S    09:55   0:00 /usr/bin/gnome-keyring-daemon
motin     5602  0.0  0.3   6560  3128 ?        Ss   09:55   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activanobody    5603  0.0  0.0   3308   776 ?        Ss   09:55   0:00 /usr/lib/GNUstep/System/Tools/gdomap -I /var/run/gdomap.pid -p
root      5640  0.0  0.1   2356  1312 ?        S    09:55   0:00 /usr/sbin/hddtemp -d -l 0.0.0.0 -p 7634 -s | /dev/hda
root      6047  0.0  0.0   1556   264 ?        SNs  09:55   0:00 /usr/sbin/powernowd -q
motin     6064  0.0  1.0  40544 10988 ?        Sl   09:55   0:01 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iiroot      6067  0.0  0.1   5776  1380 ?        Ss   09:55   0:00 /usr/sbin/nmbd -D
motin     6070  0.0  0.4   6012  4580 ?        SL   09:55   0:00 /usr/bin/esd -nobeeps
motin     6076  0.0  0.0   2832   416 ?        Ss   09:55   0:00 /usr/bin/esd -nobeeps
root      6080  0.0  0.2   8536  2144 ?        Ss   09:55   0:00 /usr/sbin/smbd -D
root      6098  0.0  0.1   4760  1028 ?        Ss   09:55   0:00 /usr/sbin/sshd
root      6113  0.0  0.0   3428   920 ?        Ss   09:55   0:00 /usr/sbin/vsftpd
root      6118  0.0  0.0   8536   956 ?        S    09:55   0:00 /usr/sbin/smbd -D
proxy     6133  0.0  0.0   2496   672 ?        S    09:56   0:00 /usr/sbin/wwwoffled -c /etc/wwwoffle/wwwoffle.conf
root      6221  0.0  0.0   2212   792 ?        Ss   09:56   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      6286  0.0  0.2   8208  2096 ?        Ss   09:56   0:00 sendmail: MTA: accepting connections
motin     6301  0.3  0.9  16060  9984 ?        Ss   09:56   0:08 metacity --sm-save-file 1146190561-5865-673922067.ms
ntp       6318  0.0  0.3   3584  3584 ?        SLs  09:56   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 122:122
root      6334  0.0  0.0   1972   740 ?        Ss   09:56   0:00 hcid: processing events
root      6338  0.0  0.0   1616   456 ?        Ss   09:56   0:00 /usr/sbin/sdpd
root      6350  0.0  0.0      0     0 ?        S<   09:56   0:00 [krfcommd]
root      6363  0.0  0.0   1628   300 ?        Ss   09:56   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    6398  0.0  0.0   1800   396 ?        Ss   09:56   0:00 /usr/sbin/atd
root      6411  0.0  0.0   2116   836 ?        Ss   09:56   0:00 /usr/sbin/cron
motin     6434  0.1  1.7  79160 17460 ?        Ssl  09:56   0:02 nautilus --sm-config-prefix /nautilus-7FD2z4/ --sm-client-id 11motin     6436  0.4  1.9  41428 20484 ?        Ssl  09:56   0:09 gnome-panel --sm-config-prefix /gnome-panel-rpTrEt/ --sm-clientmotin     6447  0.0  0.5  17504  5400 ?        Ss   09:56   0:00 gnome-volume-manager --sm-config-prefix /gnome-volume-manager-Kmotin     6451  0.0  1.0  35356 10524 ?        S    09:56   0:01 /usr/lib/notification-daemon/notification-daemon
motin     6453  0.0  0.9  30444 10036 ?        Ss   09:56   0:00 nm-applet --sm-client-id 117f000101000114613684400000049700009
motin     6455  0.0  1.1  33016 11832 ?        Ss   09:56   0:01 update-notifier --sm-config-prefix /update-notifier-SRNxVi/ --smotin     6459  0.0  0.3   8808  3924 ?        Sl   09:56   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFImotin     6549  0.0  0.1   4208  1516 ?        S    09:56   0:00 xbindkeys
motin     6585  0.0  0.6  18512  6188 ?        Ss   09:56   0:00 gnome-power-manager --sm-config-prefix /gnome-power-manager-xSfmotin     6590  1.2  2.2  35600 23048 ?        S    09:56   0:28 python /usr/lib/gdesklets/gdesklets-daemon
root      6597  0.0  0.6  14432  6252 ?        S    09:56   0:00 /usr/bin/timidity -B2,8 -Os -iAD
root      6613  0.0  0.0   1560   492 tty1     Ss+  09:56   0:00 /sbin/getty 38400 tty1
root      6614  0.0  0.0   1560   492 tty2     Ss+  09:56   0:00 /sbin/getty 38400 tty2
root      6615  0.0  0.0   1564   492 tty3     Ss+  09:56   0:00 /sbin/getty 38400 tty3
root      6616  0.0  0.0   1564   492 tty4     Ss+  09:56   0:00 /sbin/getty 38400 tty4
root      6617  0.0  0.0   1560   492 tty5     Ss+  09:56   0:00 /sbin/getty 38400 tty5
root      6618  0.0  0.0   1560   492 tty6     Ss+  09:56   0:00 /sbin/getty 38400 tty6
motin     6633  0.0  0.0   2284   800 ?        S    09:56   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
motin     6656  0.0  0.2  14772  2832 ?        Ss   09:56   0:01 gnome-screensaver
motin     6661  0.0  1.0  65664 10692 ?        Sl   09:56   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNmotin     6672  0.0  1.0  19556 10372 ?        S    09:56   0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIIDmotin     6674  0.0  1.5  36380 15428 ?        S    09:56   0:00 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iidmotin     6676  0.0  1.2  36980 12400 ?        S    09:56   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOmotin     6678  0.0  1.1  33216 11708 ?        S    09:56   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:motin     6680  0.3  0.7  17724  7864 ?        S    09:56   0:07 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAmotin     6682  0.0  0.8  30056  8604 ?        S    09:56   0:00 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-motin     6710  4.3  6.4 143644 66372 ?        Sl   09:57   1:36 /usr/lib/firefox/firefox-bin -a firefox
cupsys    7106  0.0  0.1   4196  1888 ?        SNs  10:01   0:00 /usr/sbin/cupsd
motin     7728  0.0  0.4  11924  5120 ?        S    10:07   0:00 gksu /usr/sbin/synaptic
root      7729  0.0  0.0   2472  1012 ?        Ss   10:07   0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/sbin/synroot      7754  0.0  0.0      0     0 ?        S<   10:07   0:00 [kacpid-work-0]
root      7755  0.0  0.0      0     0 ?        S<   10:07   0:00 [kacpid-work-1]
root      7756  0.0  0.0      0     0 ?        S<   10:07   0:00 [kacpid-work-2]
syslog    7858  0.0  0.0   1768   700 ?        SNs  10:07   0:00 /sbin/syslogd -u syslog
motin     8094  0.0  0.1   4176  1672 ?        S    10:11   0:00 /bin/sh /usr/lib/openoffice/program/soffice file:///home/motin/motin     8107  1.0  6.9 186064 71536 ?        Sl   10:11   0:13 /usr/lib/openoffice/program/soffice.bin file:///home/motin/Docsmotin     8283  0.3  1.3  32816 13936 ?        Sl   10:18   0:03 gnome-terminal
motin     8284  0.0  0.0   2284   680 ?        S    10:18   0:00 gnome-pty-helper
motin     8285  0.0  0.1   4472  2044 pts/0    Ss+  10:18   0:00 bash
motin     8530  0.0  0.2   4472  2052 pts/1    Ss   10:26   0:00 bash
motin     8759  0.0  0.0   2396  1016 pts/1    R+   10:34   0:00 ps aux

```

Could you please help me with this one?

PS I have been fiddling around a lot in an effort to get Jack and MIDI working in the past few months in case it is a likely cause to this from the minute to next sound disappearence

---

