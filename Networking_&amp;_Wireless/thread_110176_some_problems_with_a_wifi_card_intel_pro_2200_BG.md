---
title: "some problems with a wifi card intel pro 2200 BG"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by stardust.one on 2005-12-30
Hi every body

I have some problems to connect to internet with my network card Marvell yukon 8036 and my wifi card intel pro 2200 BG.

without wep, the card catch the signal but I cant surf:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

hyperion@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Hyperion"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:3E:50:90
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-35 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

sit0      no wireless extensions.

with wep, the card doesn't catch a signal

Modem------------>router Dlink 624+(wifi)-------------laptop toshiba M40 135

I have tested with a dhcp and with staticsIp 

so, I would like to install a new driver for a intel pro:ieee80211-1.1.6, ipw2200-fw-2.4, ipw2200-1.0.8 and wpa_supplicant-0.4.7.tar
here 's a log of installation:

hyperion@ubuntu:~$ cd ieee80211-1.1.6
hyperion@ubuntu:~/ieee80211-1.1.6$ chmod +x remove-old
hyperion@ubuntu:~/ieee80211-1.1.6$ sudo ./remove-old
+ '[' '' == '' ']'
++ uname -r
+ KERN=/lib/modules/2.6.12-9-386/build
+ echo /lib/modules/2.6.12-9-386/build
+ grep '/$'
+ KERN=/lib/modules/2.6.12-9-386/build/
+ do_check /lib/modules/2.6.12-9-386/build/
+ echo -e 'Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...\n'
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

++ find /lib/modules/2.6.12-9-386/build/ -type f -name 'ieee80211*'
+ FILES=
+ '[' -n '' ']'
+ egrep '^(CONFIG_IEEE80211.*)' /lib/modules/2.6.12-9-386/build//.config
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
+ ask_comment
+ true
+ read -p 'Above definitions found.  Comment out? [y], n '
Above definitions found.  Comment out? [y], n y
+ case ${REPLY} in
+ sed -i -e 's:^\(CONFIG_IEEE80211.*\):#\1:' /lib/modules/2.6.12-9-386/build//.config
+ sed -i -r -e 's:^(#(un)?def.*CONFIG_IEEE80211.*)hmm*\1*/:' /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h
+ return 0
+ return 0
hyperion@ubuntu:~/ieee80211-1.1.6$ make
/bin/sh: cc: command not found
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-9-386/build M=/home/hyperion/ieee80211-1.1.6 MODVERDIR=/home/hyperion/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4 : commande introuvable
make[1]: entrant dans le r&#195;&#169;pertoire &#194;&#171; /usr/src/linux-headers-2.6.12-9-386 &#194;&#187;
  CC [M]  /home/hyperion/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/hyperion/ieee80211-1.1.6/ieee80211_module.o] Erreur 127
make[1]: *** [_module_/home/hyperion/ieee80211-1.1.6] Erreur 2
make[1]: quittant le r&#195;&#169;pertoire &#194;&#171; /usr/src/linux-headers-2.6.12-9-386 &#194;&#187;
make: *** [modules] Erreur 2
hyperion@ubuntu:~/ieee80211-1.1.6$

I can't ton install a new driver because there 's no gcc 3.4 in the packages, I have a gcc4.0 and gcc 3.3 and the linux header installed

Please how to find it?  I cannot to connect to internet 

sorry for my english

Thank's

---

### Post by stardust.one on 2005-12-30
here's a log of installation of sklin98 for my network card:


hyperion@ubuntu:~$ sudo apt-get install make
Lecture des listes de paquets... Fait
Construction de l'arbre des d&#195;&#169;pendances... Fait
make est d&#195;&#169;j&#195;  la plus r&#195;&#169;cente version disponible.
0 mis &#195;  jour, 0 nouvellement install&#195;&#169;s, 0 &#195;  enlever et 0 non mis &#195;  jour.
hyperion@ubuntu:~$ sudo apt-get remove gcc-4.0
Lecture des listes de paquets... Fait
Construction de l'arbre des d&#195;&#169;pendances... Fait
Le paquet gcc-4.0 n'est pas install&#195;&#169;, et ne peut donc &#195;&#170;tre supprim&#195;&#169;
0 mis &#195;  jour, 0 nouvellement install&#195;&#169;s, 0 &#195;  enlever et 0 non mis &#195;  jour.
hyperion@ubuntu:~$ sudo ln -s linux-headers-2.6.12-9-386/ linux
ln: `linux': fichier existant.
hyperion@ubuntu:~$ cd /home/hyperion/Desktop/DriverInstall/
hyperion@ubuntu:~/Desktop/DriverInstall$ sudo ./install.sh


Installation script for sk98lin driver.
Version 8.28.1.3 (Sep-29-2005)
(C)Copyright 2003-2005 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation
2) generate patch
3) exit
Choose your favorite installation method: 1


Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel
module. This script will do this automatically per default.

Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y



Create tmp dir (/tmp/Sk98IbVdkSJoXccblAhJUNhec)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.12-9-386)                                  [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (not found)                                           [ failed ]
./install.sh: line 504: inst_failed: command not found
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (3.4.5) (Kernel:3.4.5 != gcc:729:)          [ failed ]  <----------
There is a version mismatch between the compiler that was used
to build the current running kernel and the compiler which you
intend to compile the kernel module with. In most of the cases,
this is no problem, but there are cases in which this compiler-
mismatch leads to unexpected system crashes

If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH system
variable:
    Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]
hyperion@ubuntu:~/Desktop/DriverInstall$

---

### Post by FingerPie on 2006-12-27
Hi,

I had a 2200 BG intel card that came with my Dell laptop.  Ubuntu installed a driver that worked, but would hang (lose all ability to connect to networks it could still see).  The real problem was with Windows (dual boot).  The massive intel driver DL'd from Dell's site never worked unless the AP was really close, even that would choke and stall as with Ubuntu.  

After a lot of wasted time, I bought an Atheros-based wifi card and got rid of the Intel.  Everything with Windows and "live boot" distros (like Ubuntu CD or SLAX) now works great and is very stable and fast.

I reasoned this:  What is my time worth per hour, if the Intel driver wasn't working properly in Windows, how would a wrapper ever work in Ubuntu?  You may consider a new card.

---

### Post by makushimu on 2006-12-27
:confused:  that is totally weird.. I have Intel Pro 2200BG myself and it was working fine for me before... K/Ubuntu would detect it right off the bat and with help of NetworkManager would allow me to connect to WiFi's flawlessly... About 2 weeks ago it started getting weird though - NM would scan networks, *see* them, but it wouldn't allow me to connect (still works totally fine under Win :( ) . I didnt really have time to dig that issue deeper (its holiday season after all =), but will try to look for more clues as soon as I get a chance.

EDIT: Some command outputs:

[uname -a]

> Linux Kubuntu 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

[lsmod]

> Module                  Size  Used by
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 406988  8
speedstep_centrino      9760  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0
dock                    8716  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
ipv6                  272288  8
nls_utf8                3200  1
ntfs                  112116  1
nls_iso8859_1           5248  1
nls_cp437               6912  1
vfat                   14720  1
fat                    56348  1 vfat
af_packet              24584  4
lp                     12964  0
pcmcia                 40380  0
snd_intel8x0           34844  1
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
ipw2200               115652  0
ieee80211              35272  1 ipw2200
tg3                   107652  0
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
ieee80211_crypt         7552  1 ieee80211
yenta_socket           28812  4
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   9152  0
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
joydev                 11200  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
usbhid                 45152  0
intel_agp              26012  1
agpgart                34888  2 fglrx,intel_agp
pcspkr                  4352  0
serio_raw               8452  0
psmouse                41352  0
evdev                  11392  3
irda                  214332  0
crc_ccitt               3200  1 irda
parport_pc             37796  1
parport                39496  2 lp,parport_pc
ext3                  142728  2
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_disk               18560  6
piix                   11780  1
generic                 6276  0
thermal                15624  0
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability


[ifconfig]

> eth0      Link encap:Ethernet  HWaddr 00:0F:1F:CD:70:90
          inet addr:192.168.14.8  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fecd:7090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3233039 (3.0 MiB)  TX bytes:202440 (197.6 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:16:6F:B7:16:D8
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:98792 (96.4 KiB)  TX bytes:1709 (1.6 KiB)
          Interrupt:5 Base address:0x6000 Memory:fafef000-fafeffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


[iwconfig]

> lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SoMeWiFi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:C4:64:B1:90
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=-70 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:16

eth0      no wireless extensions.

sit0      no wireless extensions.


[iwlist eth1 scan]

> eth1      Scan completed :
          Cell 01 - Address: 00:13:C4:64:B1:90
                    ESSID:"SoMeWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm
                    Extra: Last beacon: 1076ms ago


[dmesg| grep ipw]

> [17179591.060000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179591.060000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.060000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179591.964000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179592.176000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


[lspci|grep Net]

> 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


[cat /var/log/messages| grep ipw220]

> Dec 27 00:10:14 yupbook kernel: [17179588.956000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 00:10:14 kubuntu kernel: [17179588.956000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 00:10:14 kubuntu kernel: [17179588.956000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 00:10:14 kubuntu kernel: [17179588.984000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 00:10:14 kubuntu kernel: [17179589.612000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 06:26:40 kubuntu kernel: [17179588.760000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 06:26:40 kubuntu kernel: [17179588.760000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 06:26:40 kubuntu kernel: [17179588.760000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 06:26:40 kubuntu kernel: [17179589.708000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 06:26:40 kubuntu kernel: [17179589.936000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 06:37:59 kubuntu kernel: [17179587.972000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 06:37:59 kubuntu kernel: [17179587.972000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 06:37:59 kubuntu kernel: [17179587.972000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 06:37:59 kubuntu kernel: [17179588.408000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 06:37:59 kubuntu kernel: [17179588.684000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 09:34:40 kubuntu kernel: [17179589.036000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 09:34:40 kubuntu kernel: [17179589.036000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 09:34:40 kubuntu kernel: [17179589.036000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 09:34:40 kubuntu kernel: [17179589.592000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 09:34:40 kubuntu kernel: [17179589.784000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 10:28:26 kubuntu kernel: [17179589.556000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 10:28:26 kubuntu kernel: [17179589.556000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 10:28:26 kubuntu kernel: [17179589.556000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 10:28:26 kubuntu kernel: [17179589.736000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 10:28:26 kubuntu kernel: [17179590.020000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 11:58:56 kubuntu kernel: [17179588.416000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 11:58:56 kubuntu kernel: [17179588.416000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 11:58:56 kubuntu kernel: [17179588.416000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 11:58:56 kubuntu kernel: [17179589.220000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 11:58:56 kubuntu kernel: [17179589.436000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 27 14:33:50 kubuntu kernel: [17179591.060000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 27 14:33:50 kubuntu kernel: [17179591.060000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 27 14:33:50 kubuntu kernel: [17179591.060000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 27 14:33:50 kubuntu kernel: [17179591.964000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 27 14:33:50 kubuntu kernel: [17179592.176000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)



PS. Looking at last output,  im kinda worried by this *needs updating* thing... how bad is it?

---

