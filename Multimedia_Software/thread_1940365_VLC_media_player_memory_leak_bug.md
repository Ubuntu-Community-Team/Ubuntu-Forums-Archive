---
title: "VLC media player memory leak bug"
date: 2012-03-13
forum: Multimedia Software
---

### Post by livin4th on 2012-03-13
Hello,
               I started having this problem for a while now.  every now and then my vlc freezes in the middle and after that the whole  system freezes till I kill it using the power button since the system  is totally dead. This is annoying since I loose all my open applications  and  have to restart them again.

I decided to write a short  script which captures the dmesg output every now and them and finally I  got a trace of what was happening when it freezes. heres the output.

> 
[ 6513.465086] 59257 total pagecache pages
[ 6513.465092] 0 pages in swap cache
[ 6513.465098] Swap cache stats: add 0, delete 0, find 0/0
[ 6513.465102] Free swap  = 0kB
[ 6513.465107] Total swap = 0kB
[ 6513.475633] 521821 pages RAM
[ 6513.475640] 294511 pages HighMem
[ 6513.475643] 9130 pages reserved
[ 6513.475649] 37393 pages shared
[ 6513.475655] 473758 pages non-shared
[ 6513.475659] [ pid ]   uid     tgid total_vm      rss cpu oom_adj oom_score_adj     name
[ 6513.475679] [  289]     0    289      603       37   0       0             0                     upstart-udev-br
[ 6513.475689] [  299]     0    299      720      200   0     -17         -1000               udevd
[ 6513.475699] [  416]     0    416      719      179   0     -17         -1000               udevd
[ 6513.475711] [  417]     0    417      719      179   1     -17         -1000               udevd
[ 6513.475720] [  467]   101  467     7124      149   0       0             0                   rsyslogd
[ 6513.475771] [  473]   102  473      892      275   0       0             0 dbus-daemon
[ 6513.475781] [  495]   104   495      754       60   0       0             0 avahi-daemon
[ 6513.475793] [  496]   104   496      754       55   1       0             0 avahi-daemon
[ 6513.475802] [  502]     0   502     6374      252   0       0             0 NetworkManager
[ 6513.475812] [  524]     0   524     1165      156   0       0             0 modem-manager
[ 6513.475825] [  528]     0   528     5836      252   0       0             0 polkitd
[ 6513.475834] [  594]     0   594     1293       66   0       0             0 wpa_supplicant
[ 6513.475844] [  632]     0   632      603       55   0       0             0 upstart-socket-
[ 6513.475853] [  713]     0   713      468       36   0       0             0 getty
[ 6513.475865] [  719]     0   719      468       35   0       0             0 getty
[ 6513.475875] [  728]     0   728      468       36   0       0             0 getty
[ 6513.475884] [  729]     0   729      468       36   0       0             0 getty
[ 6513.475894] [  732]     0   732      468       36   0       0             0 getty
[ 6513.475906] [  744]     0   744      466       58   1       0             0 acpid
[ 6513.475916] [  749]     0   749      567       51   1       0             0 cron
[ 6513.475925] [  750]     0   750      533       31   1       0             0 atd
[ 6513.475935] [  762]     0   762      789       51   1       0             0 irqbalance
[ 6513.475947] [  837]     0   837     4506      201   0       0             0 gdm-binary
[ 6513.475957] [  849]     0   849     6826      229   0       0             0 console-kit-dae
[ 6513.475967] [  983]     0   983      638       87   0       0             0 dhclient
[ 6513.475980] [  990]     0   990     2070      123   1       0             0 vpnagentd
[ 6513.475989] [ 1076]     0  1076     1698      193   0       0             0 cupsd
[ 6513.476025] [ 1134]     0  1134      468       36   0       0             0 getty
[ 6513.476037] [ 1229]     0  1229     4180      214   0       0             0 upowerd
[ 6513.476047] [ 1244]   109  1244     4722       74   0       0             0 rtkit-daemon
[ 6513.476056] [ 1320]     0  1320     3482      152   0       0             0 accounts-daemon
[ 6513.476066] [ 1427]  1000  1427    73648     2868   1       0             0 pulseaudio
[ 6513.476078] [ 1439]  1000  1439     5453      161   1       0             0 gconf-helper
[ 6513.476088] [ 1451]     0  1451     5593      226   0       0             0 udisks-daemon
[ 6513.476098] [ 1452]     0  1452     1391       67   1       0             0 udisks-daemon
[ 6513.476111] [ 1486]  1000  1486    13636      387   1       0             0 e-calendar-fact
[ 6513.476120] [ 1661]     0  1661     4964      246   0       0             0 gdm-simple-slav
[ 6513.476130] [ 1663]     0  1663    29169     7955   0       0             0 Xorg
[ 6513.476143] [ 1704]     0  1704     4600      215   1       0             0 gdm-session-wor
[ 6513.476153] [ 1726]  1000  1726    10671      138   1       0             0 gnome-keyring-d
[ 6513.476162] [ 1745]  1000  1745     9085      403   0       0             0 gnome-session
[ 6513.476172] [ 1779]  1000  1779      842       48   1       0             0 ssh-agent
[ 6513.476184] [ 1782]  1000  1782      864       54   1       0             0 dbus-launch
[ 6513.476193] [ 1783]  1000  1783     1119      299   0       0             0 dbus-daemon
[ 6513.476203] [ 1788]  1000  1788     2428      552   1       0             0 gconfd-2
[ 6513.476215] [ 1800]  1000  1800    43778      998   1       0             0 gnome-settings-
[ 6513.476225] [ 1803]  1000  1803     1908      107   0       0             0 gvfsd
[ 6513.476234] [ 1808]  1000  1808     7744      153   0       0             0 gvfs-fuse-daemo
[ 6513.476244] [ 1812]  1000  1812    18104     1505   1       0             0 compiz
[ 6513.476256] [ 1825]  1000  1825      857       57   0       0             0 syndaemon
[ 6513.476266] [ 1827]  1000  1827     2251      184   1       0             0 gvfs-gdu-volume
[ 6513.476276] [ 1829]  1000  1829    34446     2615   1       0             0 nautilus
[ 6513.476288] [ 1831]  1000  1831     2128      137   0       0             0 gvfs-gphoto2-vo
[ 6513.476297] [ 1833]  1000  1833     4551      106   0       0             0 gvfs-afc-volume
[ 6513.476307] [ 1835]  1000  1835    37646      847   0       0             0 nm-applet
[ 6513.476316] [ 1836]  1000  1836    27041     1344   0       0             0 gnome-panel
[ 6513.476329] [ 1837]  1000  1837     6583      308   0       0             0 polkit-gnome-au
[ 6513.476339] [ 1839]  1000  1839    12561      523   0       0             0 zeitgeist-datah
[ 6513.476348] [ 1841]  1000  1841    13375      391   1       0             0 gnome-power-man
[ 6513.476361] [ 1842]  1000  1842    11049      343   0       0             0 bluetooth-apple
[ 6513.476371] [ 1843]  1000  1843     9779      523   1       0             0 evolution-alarm
[ 6513.476381] [ 1850]  1000  1850    14419     8194   1       0             0 zeitgeist-daemo
[ 6513.476393] [ 1852]  1000  1852      978       12   0       0             0 cat
[ 6513.476403] [ 1871]  1000  1871     2028      131   1       0             0 gvfsd-trash
[ 6513.476413] [ 1877]  1000  1877    13636      388   0       0             0 e-calendar-fact
[ 6513.476426] [ 1883]  1000  1883    21129      632   0       0             0 notify-osd
[ 6513.476435] [ 1888]  1000  1888      478       29   0       0             0 sh
[ 6513.476445] [ 1889]  1000  1889     9596      643   0       0             0 unity-window-de
[ 6513.476455] [ 1901]  1000  1901     8540      162   0       0             0 bonobo-activati
[ 6513.476467] [ 1908]  1000  1908    23752      892   1       0             0 wnck-applet
[ 6513.476477] [ 1911]  1000  1911    41700     1363   1       0             0 clock-applet
[ 6513.476486] [ 1913]  1000  1913    22539      523   1       0             0 notification-ar
[ 6513.476499] [ 1916]  1000  1916     1941      141   0       0             0 gvfsd-burn
[ 6513.476508] [ 1924]  1000  1924     6769      348   0       0             0 gnome-screensav
[ 6513.476518] [ 1949]  1000  1949     1931      161   0       0             0 gvfsd-metadata
[ 6513.476527] [ 1951]  1000  1951   160756    49870   0       0             0 firefox
[ 6513.476539] [ 1961]  1000  1961     4883      337   1       0             0 gdu-notificatio
[ 6513.476549] [ 1980]  1000  1980     8390     1947   0       0             0 applet.py
[ 6513.476559] [ 1990]  1000  1990    18123     5108   1       0             0 ubuntuone-syncd
[ 6513.476571] [ 2011]  1000  2011    67081     9925   1       0             0 plugin-containe
[ 6513.476581] [ 2023]  1000  2023    15782      760   1       0             0 plugin-containe
[ 6513.476591] [ 2026]  1000  2026    16904     2188   1       0             0 GoogleTalkPlugi
[ 6513.476600] [ 2038]  1000  2038    23593      690   0       0             0 update-notifier
[ 6513.476613] [ 2052]     0  2052     3680     1034   1       0             0 system-service-
[ 6513.476622] [ 2104]  1000  2104    84024     9876   1       0             0 chromium-browse
[ 6513.476632] [ 2107]  1000  2107    18225      689   1       0             0 chromium-browse
[ 6513.476644] [ 2109]  1000  2109    19349      738   0       0             0 chromium-browse
[ 6513.476654] [ 2135]  1000  2135    50139    16233   0       0             0 chromium-browse
[ 6513.476665] [ 2370]  1000  2370   326979   291438   1       0             0 vlc
[ 6513.476677] [ 2408]  1000  2408      478       42   0       0             0 xdg-screensaver
[ 6513.476687] [ 2416]  1000  2416      478       40   1       0             0 xdg-screensaver
[ 6513.476696] [ 2420]  1000  2420     1543       30   0       0             0 xprop
[ 6513.476709] [ 2988]  1000  2988    88322    13686   1       0             0 skype
[ 6513.476719] [ 3136]  1000  3136      973       27   0       0             0 sleep
[ 6513.476727] Out of memory: Kill process 2370 (vlc) score 568 or sacrifice child
[ 6513.476742] Killed process 2370 (vlc) total-vm:1307916kB, anon-rss:1119740kB, file-rss:46012kB
sorry the output looks so messy..the formatted output is in the attached file.

basically I found out that vlc caused a memory problem and it had to be killed. The worst part was that vlc for in pause mode for the last half hour. I haven't installed any new libraries recently or have I updated the system. I am using 11.04 ubuntu. can anyone suggest me what to do now?

Thanks,
Livin

---

### Post by synaptix on 2012-03-13
[http://wiki.videolan.org/Report_bugs](http://wiki.videolan.org/Report_bugs)

---

