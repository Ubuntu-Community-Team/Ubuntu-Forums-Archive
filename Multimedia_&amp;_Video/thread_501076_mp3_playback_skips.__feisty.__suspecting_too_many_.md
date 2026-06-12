---
title: "mp3 playback skips.  feisty.  suspecting too many gstreamer codecs"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by kraymore on 2007-07-14
i am having some audio playback issues playing back mp3s on feisty.  

i have w32codecs installed from medibuntu

i also have all of feistys gsteamer codecs.  

i should definitely have enough resources

i do not have very many windows at all, just xchat, terminal, mozilla thunderbird, nicotine, nautilus, and totem..  it seems as if my computer doesn't have enough resources to play it however i should be ok on resources given what i have running.  when i installed my gsteamer codecs i had did an apt-get install gstreamer0.10-* i am wondering if that is what is effecting playback, how to remedy, or even another possible problem hanging up audio.  

its a 965G chipset motherboard, with pentium d 2.8ghz and 2 gigs of ram.  should be more than enough resources.  

thank you

i will paste my ps aux:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2908  1848 ?        Ss   16:31   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    16:31   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   16:31   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    16:31   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S    16:31   0:00 [migration/1]
root         6  0.0  0.0      0     0 ?        SN   16:31   0:00 [ksoftirqd/1]
root         7  0.0  0.0      0     0 ?        S    16:31   0:00 [watchdog/1]
root         8  0.0  0.0      0     0 ?        S<   16:31   0:00 [events/0]
root         9  0.0  0.0      0     0 ?        S<   16:31   0:00 [events/1]
root        10  0.0  0.0      0     0 ?        S<   16:31   0:00 [khelper]
root        11  0.0  0.0      0     0 ?        S<   16:31   0:00 [kthread]
root        35  0.0  0.0      0     0 ?        S<   16:31   0:00 [kblockd/0]
root        36  0.0  0.0      0     0 ?        S<   16:31   0:00 [kblockd/1]
root        37  0.0  0.0      0     0 ?        S<   16:31   0:00 [kacpid]
root        38  0.0  0.0      0     0 ?        S<   16:31   0:00 [kacpi_notify]
root       162  0.0  0.0      0     0 ?        S<   16:31   0:00 [kseriod]
root       189  0.0  0.0      0     0 ?        S    16:32   0:00 [pdflush]
root       190  0.0  0.0      0     0 ?        S    16:32   0:00 [pdflush]
root       191  0.0  0.0      0     0 ?        S<   16:32   0:00 [kswapd0]
root       192  0.0  0.0      0     0 ?        S<   16:32   0:00 [aio/0]
root       193  0.0  0.0      0     0 ?        S<   16:32   0:00 [aio/1]
root       828  0.0  0.0      0     0 ?        S    16:32   0:00 [kirqd]
root      2030  0.0  0.0      0     0 ?        S<   16:32   0:00 [ksuspend_usbd]
root      2031  0.0  0.0      0     0 ?        S<   16:32   0:00 [khubd]
root      2087  0.0  0.0      0     0 ?        S<   16:32   0:01 [ata/0]
root      2088  0.0  0.0      0     0 ?        S<   16:32   0:00 [ata/1]
root      2089  0.0  0.0      0     0 ?        S<   16:32   0:00 [ata_aux]
root      2226  0.0  0.0      0     0 ?        S<   16:32   0:02 [scsi_eh_0]
root      2227  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_1]
root      2228  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_2]
root      2229  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_3]
root      2258  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_4]
root      2259  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_5]
root      2316  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_6]
root      2317  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_7]
root      2420  0.0  0.0      0     0 ?        S<   16:32   0:00 [scsi_eh_8]
root      2421  0.0  0.0      0     0 ?        S<   16:32   0:00 [usb-storage]
root      2550  0.0  0.0      0     0 ?        S<   16:32   0:00 [kjournald]
root      2747  0.0  0.0   2884  1232 ?        S<s  16:32   0:00 /sbin/udevd --d
root      3894  0.0  0.0      0     0 ?        S<   16:32   0:00 [kpsmoused]
root      4043  0.0  0.0      0     0 ?        S<   16:32   0:00 [hda_codec]
root      4373  0.0  0.0      0     0 ?        S<   16:32   0:00 [kjournald]
root      4378  0.0  0.0   3628   912 ?        Ss   16:32   0:00 /sbin/mount.ntf
root      4382  0.0  0.0   3624   908 ?        Ss   16:32   0:00 /sbin/mount.ntf
root      4690  0.0  0.0   1652   512 tty4     Ss+  16:32   0:00 /sbin/getty 384
root      4691  0.0  0.0   1652   508 tty5     Ss+  16:32   0:00 /sbin/getty 384
root      4693  0.0  0.0   1648   508 tty2     Ss+  16:32   0:00 /sbin/getty 384
root      4695  0.0  0.0   1648   508 tty3     Ss+  16:32   0:00 /sbin/getty 384
root      4697  0.0  0.0   1652   512 tty1     Ss+  16:32   0:00 /sbin/getty 384
root      4698  0.0  0.0   1652   512 tty6     Ss+  16:32   0:00 /sbin/getty 384
root      4956  0.0  0.0   2256  1172 ?        Ss   16:32   0:00 /usr/sbin/acpid
root      5067  0.0  0.0   1700   640 ?        Ss   16:32   0:00 /sbin/syslogd
root      5122  0.0  0.0   1792   524 ?        Ss   16:32   0:00 /bin/dd bs 1 if
klog      5124  0.0  0.0   2424  1376 ?        Ss   16:32   0:00 /sbin/klogd -P
103       5145  0.0  0.0   2848  1048 ?        Ss   16:32   0:00 /usr/bin/dbus-d
107       5161  0.0  0.4  10780  9092 ?        Ss   16:32   0:02 /usr/sbin/hald
root      5162  0.0  0.0   2872  1028 ?        S    16:32   0:00 hald-runner
107       5168  0.0  0.0   2100   888 ?        S    16:32   0:00 hald-addon-acpi
root      5169  0.0  0.0   2928  1088 ?        S    16:32   0:00 /usr/lib/hal/ha
107       5176  0.0  0.0   2100   904 ?        S    16:32   0:00 hald-addon-keyb
107       5185  0.0  0.0   2096   896 ?        S    16:32   0:00 hald-addon-keyb
107       5188  0.0  0.0   2096   896 ?        S    16:32   0:00 hald-addon-keyb
107       5206  0.0  0.0   2100   908 ?        S    16:32   0:01 hald-addon-stor
root      5219  0.0  0.0   1936   696 ?        Ss   16:32   0:00 /usr/sbin/dhcdb
root      5234  0.0  0.0   4124  1864 ?        Ss   16:32   0:00 /usr/sbin/Netwo
avahi     5252  0.0  0.0   2668  1364 ?        Ss   16:32   0:00 avahi-daemon: r
avahi     5253  0.0  0.0   2668   464 ?        Ss   16:32   0:00 avahi-daemon: c
root      5266  0.0  0.0   3024  1144 ?        Ss   16:32   0:00 /usr/sbin/Netwo
root      5279  0.0  0.0   2864   800 ?        Ss   16:32   0:00 /usr/bin/system
root      5280  0.0  0.0   2716  1216 ?        S    16:32   0:00 dbus-daemon --s
root      5314  0.0  0.0  12216  1416 ?        Ss   16:32   0:00 /usr/sbin/gdm
root      5315  0.0  0.1  12576  2404 ?        S    16:32   0:00 /usr/sbin/gdm
root      5318  3.5  2.5  59840 52764 tty7     SLs+ 16:32   3:11 /usr/X11R6/bin/
cupsys    5363  0.0  0.0   4680  1956 ?        Ss   16:32   0:00 /usr/sbin/cupsd
root      5389  0.0  0.0   6412   836 ?        Ss   16:32   0:00 /usr/sbin/hpiod
hplip     5392  0.0  0.2   9988  4896 ?        S    16:32   0:00 python /usr/sbi
root      5465  0.0  0.0      0     0 ?        S<   16:32   0:02 [kondemand/0]
root      5466  0.0  0.0      0     0 ?        S<   16:32   0:02 [kondemand/1]
root      5506  0.0  0.0   2696  1000 ?        Ss   16:32   0:00 /usr/sbin/hcid
root      5526  0.0  0.0      0     0 ?        S<   16:32   0:00 [krfcommd]
daemon    5561  0.0  0.0   1908   420 ?        Ss   16:32   0:00 /usr/sbin/atd
root      5575  0.0  0.0   2284   900 ?        Ss   16:32   0:00 /usr/sbin/cron
avis      5676  0.0  0.5  30688 11548 ?        Ssl  16:32   0:00 /usr/bin/gnome-
avis      5717  0.0  0.0   4252   528 ?        Ss   16:32   0:00 /usr/bin/ssh-ag
avis      5720  0.0  0.0   2660   640 ?        S    16:32   0:00 /usr/bin/dbus-l
avis      5721  0.0  0.0   2848  1032 ?        Ss   16:32   0:00 /usr/bin/dbus-d
avis      5723  0.0  0.2   6720  4224 ?        S    16:32   0:00 /usr/lib/libgco
avis      5726  0.0  0.0   2752  1000 ?        S    16:32   0:00 /usr/bin/gnome-
avis      5728  0.0  0.4  29624 10092 ?        Sl   16:32   0:00 /usr/lib/contro
avis      5735  0.0  0.0   1716   480 ?        Ss   16:32   0:00 /bin/sh -c /usr
avis      5736  0.0  0.1   4960  3336 ?        S    16:32   0:00 /usr/bin/esd -t
avis      5740  0.0  0.0   1716   496 ?        S    16:32   0:00 /bin/sh /usr/bi
avis      5743  0.1  0.9  72976 19384 ?        S    16:32   0:05 gnome-panel --s
avis      5746  0.0  1.4 113444 29708 ?        S    16:32   0:03 nautilus --no-d
avis      5749  0.0  0.4  17332  9592 ?        S    16:32   0:01 gtk-window-deco
avis      5752  0.0  0.2  18820  4868 ?        Ss   16:32   0:00 gnome-volume-ma
avis      5754  0.7  1.4  32864 29088 ?        RL   16:32   0:42 /usr/bin/compiz
avis      5759  0.0  0.1  40684  3140 ?        Ssl  16:32   0:00 /usr/lib/bonobo
avis      5763  0.0  0.1   8460  3436 ?        S    16:32   0:00 /usr/lib/gnome-
avis      5767  0.0  1.2  81536 25672 ?        Sl   16:32   0:02 beagled /usr/li
avis      5771  0.0  0.5  51500 12216 ?        S    16:32   0:00 update-notifier
root      5774  0.1  0.0   4320  1672 ?        Ss   16:32   0:07 /sbin/mount.ntf
avis      5777  0.0  1.4  95260 30232 ?        Sl   16:32   0:01 beagle-search -
avis      5782  0.0  0.4  67884  9896 ?        Sl   16:32   0:00 /usr/lib/evolut
avis      5797  0.0  0.4  81704  8892 ?        S    16:32   0:00 /usr/lib/gnome-
avis      5798  0.0  0.5  49144 10556 ?        S    16:32   0:00 nm-applet --sm-
avis      5813  0.0  0.3  40056  8208 ?        S    16:32   0:00 gnome-cups-icon
avis      5814  0.0  0.2  51376  5960 ?        Ss   16:32   0:00 gnome-power-man
avis      5822  0.0  0.0   2456   888 ?        S    16:32   0:00 /usr/lib/nautil
avis      5826  0.0  0.4  36428  9476 ?        Sl   16:32   0:00 /usr/lib/evolut
avis      5842  0.0  0.3  66620  6408 ?        Sl   16:32   0:00 /usr/lib/evolut
avis      5846  0.0  0.6  52880 12800 ?        S    16:32   0:00 /usr/lib/gnome-
avis      5890  0.2  0.9  80328 20080 ?        Sl   16:33   0:16 xchat
avis      5897  0.0  0.2  16492  5608 ?        Ss   16:33   0:01 gnome-screensav
avis      6363  0.0  0.7  78324 16572 ?        Sl   16:47   0:00 gnome-terminal
avis      6368  0.0  0.0   2460   728 ?        S    16:47   0:00 gnome-pty-helpe
avis      6369  0.0  0.1   5648  3136 pts/0    Ss   16:47   0:00 bash
avis      6387  0.0  0.0   1712   516 ?        S    16:47   0:00 /bin/sh /usr/bi
avis      6391  0.0  0.0   1712   524 ?        S    16:47   0:00 /bin/sh /usr/li
avis      6395  0.0  1.5 100860 33060 ?        Sl   16:47   0:01 /usr/lib/mozill
avis      6531  2.1  1.5  94672 31156 ?        Sl   16:51   1:35 /usr/bin/python
avis      7963 99.3  1.6 162692 33344 ?        SLl  17:49  14:03 totem file:///m
avis      8195 22.0  7.8 297368 162384 ?       SLl  17:56   1:34 /usr/lib/firefo
avis      8210  0.0  0.0      0     0 ?        Z    17:56   0:00 [net] <defunct>
avis      8453  0.0  0.0   2564   992 pts/0    R+   18:03   0:00 ps aux

---

### Post by Anzan on 2007-07-27
I sometimes have this when Firefox is loading a new tab. But you don't list Firefox.

---

### Post by kraymore on 2007-07-28
no, this is within totem.  i suspect i may have damaged my motherboard by using a certain CIA2 hardware tweaker within the bios.  i did not suspect that such a tweaker would be implemented by gigabyte if it were to damage a stock the motherboard using all integrated peripherals.  i simply did not think when i did it.  

the system runs pretty well otherwise.  i have also attributed such occurances due to only 2GB of memory.  i could have sworn i had better results with that little ram on a earlier release of ubuntu.

---

### Post by kostkon on 2007-07-28
> **kraymore said:**
> no, this is within totem.  i suspect i may have damaged my motherboard by using a certain CIA2 hardware tweaker within the bios.  i did not suspect that such a tweaker would be implemented by gigabyte if it were to damage a stock the motherboard using all integrated peripherals.  i simply did not think when i did it.  

the system runs pretty well otherwise.  i have also attributed such occurrances due to only 2GB of memory.  i could have sworn i had better results with that little ram on a earlier release of ubuntu.

You are exaggerating here, 2GB not enough??!! I have opened more programs, also with music playing, and I have only 512MB, and everything was running just fine. Thus, I don't think the reason is that you are low on memory or other resources, the reason rests somewhere else. 

And I mean that something strange is happening, from your PS output I can see that your totem is eating 90% of your CPU time (!!!!) which is very very strange. I don't know what makes this to happen, though. Maybe a misconfiguration, maybe a sound card driver problem, maybe a hardware one?

---

