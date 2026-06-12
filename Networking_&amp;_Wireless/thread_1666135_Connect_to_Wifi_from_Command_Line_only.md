---
title: "Connect to Wifi from Command Line only"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by acplusplusprogrammer on 2011-01-13
Hello everyone,
I want to connect to my wifi from command line (not the one you enter from ALT+CTRL+F1, BUT the one you enter from Recovery Mode).

When I go to Recovery Mode --> Switch to room command line with networking

IF

I use ethernet (eth0) I have no problems. And even if I plug the ethernet wire AFTER the login and then I run "sudo dhclient" I get the internet connection.

BUT IF

I want to connect to my wireless network it doesn't work.
I have tried with this (and many other) syntax:

sudo iwconfig wlan0 mode managed channel 6 key open <yourwepkeyhereifany> essid MyNet
sudo iwconfig wlan0 ap AA:BB:CC:DD:EE:22
sudo dhclient wlan0

BUT 

I get something like this (I cope/pasted the result from another website. But the result it's this one)

Listening on LPF/eth0/00:20:e0:5e:2d:73 
Sending on   LPF/eth0/00:20:e0:5e:2d:73 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 



NOW

I think there's some problem with Network Manager. Is it perhaps interfering? 

How do people connect to wireless using command line?

---

### Post by chili555 on 2011-01-13
I don't think Network Manager is started in recovery mode. Check with:```
ps aux | grep -i network
```I think your commands are a bit busy. For a WEP hex network, it ought to be as easy as:```
sudo iwconfig wlan0 key <yourwepkeyhereifany> 
sudo iwconfig wlan0 essid MyNet
sudo dhclient wlan0
```Your key is 10 or 26-character hex, correct?

---

### Post by acplusplusprogrammer on 2011-01-13
Hello,
first of all THANK YOU for answering.

First of all:

[SIZE=4]**ps aux | grep -i network**[/SIZE]
xxx@xxx:~$ ps aux | grep -i network
root       667  0.1  0.1   8884  3956 ?        Ss   16:49   0:00 NetworkManager
xxx       2065  0.0  0.0   4012   772 tty3     S+   16:51   0:00 grep --color=auto -i network



[SIZE=4]**As soon as I log in I get this:**[/SIZE]

_[some text]_

Listening on LPF/wlan0/00:22:fa:1b:37:86
Sending on   LPF/wlan0/00:22:fa:1b:37:86
Listening on LPF/eth0/00:23:5a:94:67:86
Sending on   LPF/eth0/00:23:5a:94:67:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
_[...many many tries]_
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

^Crc-sysinit start/running, process 1338
 * Starting mouse interface server gpm                                                                                                                              

_[some other text of checking stuff]_
Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
_[the shell prompt]_



[SIZE=4]**And if I try with your commands I get:**[/SIZE]

xxx@xxx:~$ sudo iwconfig wlan0 essid Alice-35566834
xxx@xxx:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:22:fa:1b:37:86
Sending on   LPF/wlan0/00:22:fa:1b:37:86
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
_[many many tries]_
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

^C
xxx@xxx:~$

----------------------------------------------------------------------------------------------------

I really want to connect to WiFi from command line :(

---

### Post by chili555 on 2011-01-13
> root 667 0.1 0.1 8884 3956 ? Ss 16:49 0:00 NetworkManagerI'm surprised; NM is running and, no doubt, interfering. Please try again with:```
sudo killall NetworkManager
```I hope it doesn't re-spawn, like some kind of killer Windows virus. Check:```
ps aux | grep -i network
```Retry the commands.

Of course, you could remove NM, populate /etc/network/interfaces, /etc/resolv.conf and thereafter connect on boot. No C++ required!

---

### Post by acplusplusprogrammer on 2011-01-13
Ok,
I tried to
[SIZE=4][B]
 sudo killall NetworkManager[/B][/SIZE]
xxx@xxx:~$ sudo killall NetworkManager
xxx@xxx:~$ ps aux | grep -i network
root      1927  6.0  0.1   8884  3932 ?        Ss   17:48   0:00 NetworkManager
xxx       1932  0.0  0.0   4008   776 tty1     S+   17:49   0:00 grep --color=auto -i network


BUT

still says that there's a NetworkManager. I also tried "sudo killall -g NetworkManager", but no change. It's still running.

I don't understand what you mean by saying "populate /etc/network/interfaces, /etc/resolv.conf" (I simply don't understand the word populate). 

resolv.conf
-----------------
# Generated by NetworkManager
domain homenet.telecomitalia.it
search homenet.telecomitalia.it
nameserver 192.168.1.1
-----------------

interfaces
-----------------
auto lo
iface lo inet loopback
-----------------


By the way, I don't want to uninstall the Network Manager, since I think it's quite handy when I use it from GUI. Anyhow I feel it's strange why ethernet works and wireless don't?
I also tried with "nmcli" but looks like there's no way to use it to connect. Like, if NetworkManager is running, is there a way to use it to connect?

---

### Post by chili555 on 2011-01-13
> I don't understand what you mean by saying "populate /etc/network/interfaces, /etc/resolv.conf" (I simply don't understand the word populate).It simply means fill in the correct items. It doesn't matter if you want to use Network Manager; you should use manual methods or NM but not both.

I have stated in this forum many times that it is very difficult and sometimes impossible to get connected with the command line if NM is installed and running. You now know it's also quite difficult and maybe impossible to keep NM from running. If you stop it, it re-spawns immediately.

You might try:```
sudo /etc/init.d/NetworkManager stop
```It may be called network-manager. Check to see if it re-spawns:```
ps aux | grep -i network
```

More later, after I boot into recovery mode to experiment.

---

### Post by chili555 on 2011-01-13
Please try booting into recovery mode, root shell *without* networking. Retry the commands. If it doesn't work, precede the commands with:```
sudo /etc/init.d/networking start
```

---

### Post by acplusplusprogrammer on 2011-01-15
Hi,
thank you for your answers, but still nothing happens. I'm giving up now since I'll be back at work since next week so no much free time.
By the way, even in Recovery mode without networking, network manager is still there.
[SIZE=4][B]
sudo /etc/init.d/networking start[/B][/SIZE]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting

[B][SIZE=4]
 start networking[/SIZE][/B]
networking stop/waiting


**[SIZE=4]xxx@xxx:~$ ps aux | grep -i network[/SIZE]**
root       681  0.0  0.1   8884  3956 ?        Ss   13:45   0:00 NetworkManager
root      1373  0.0  0.0   4012   772 tty1     R+   13:48   0:00 grep --color=auto -i network


and 
[SIZE=4]**ps -A**[/SIZE]
 PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 migration/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:00 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:00 kblockd/0
   22 ?        00:00:00 kblockd/1
   23 ?        00:00:00 kacpid
   24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata_aux
   27 ?        00:00:00 ata_sff/0
   28 ?        00:00:00 ata_sff/1
   29 ?        00:00:00 khubd
   30 ?        00:00:00 kseriod
   31 ?        00:00:00 kmmcd
   32 ?        00:00:00 khungtaskd
   33 ?        00:00:00 kswapd0
   34 ?        00:00:00 ksmd
   35 ?        00:00:00 aio/0
   36 ?        00:00:00 aio/1
   37 ?        00:00:00 ecryptfs-kthrea
   38 ?        00:00:00 crypto/0
   39 ?        00:00:00 crypto/1
   52 ?        00:00:00 kstriped
   53 ?        00:00:00 kmpathd/0
   54 ?        00:00:00 kmpathd/1
   55 ?        00:00:00 kmpath_handlerd
   56 ?        00:00:00 ksnapd
   57 ?        00:00:00 kondemand/0
   58 ?        00:00:00 kondemand/1
   59 ?        00:00:00 kconservative/0
   60 ?        00:00:00 kconservative/1
  396 ?        00:00:00 scsi_eh_0
  397 ?        00:00:00 scsi_eh_1
  398 ?        00:00:00 scsi_eh_2
  399 ?        00:00:00 scsi_eh_3
  400 ?        00:00:00 scsi_eh_4
  401 ?        00:00:00 scsi_eh_5
  417 ?        00:00:00 usbhid_resumer
  434 ?        00:00:00 jbd2/sda5-8
  435 ?        00:00:00 ext4-dio-unwrit
  436 ?        00:00:00 ext4-dio-unwrit
  437 ?        00:00:00 flush-1:0
  438 ?        00:00:00 flush-1:1
  439 ?        00:00:00 flush-1:2
  440 ?        00:00:00 flush-1:3
  441 ?        00:00:00 flush-1:4
  442 ?        00:00:00 flush-1:5
  443 ?        00:00:00 flush-1:6
  444 ?        00:00:00 flush-1:7
  445 ?        00:00:00 flush-1:8
  446 ?        00:00:00 flush-1:9
  447 ?        00:00:00 flush-1:10
  448 ?        00:00:00 flush-1:11
  449 ?        00:00:00 flush-1:12
  450 ?        00:00:00 flush-1:13
  451 ?        00:00:00 flush-1:14
  452 ?        00:00:00 flush-1:15
  453 ?        00:00:00 flush-8:0
  497 ?        00:00:00 upstart-udev-br
  500 ?        00:00:00 udevd
  652 ?        00:00:00 rsyslogd
  661 ?        00:00:00 dbus-daemon
  [B]676 ?        00:00:00 avahi-daemon
  677 ?        00:00:00 avahi-daemon
  681 ?        00:00:00 NetworkManager[/B]
  [B]683 ?        00:00:00 modem-manager
  686 ?        00:00:00 wpa_supplicant[/B]
  824 ?        00:00:00 udevd
  858 ?        00:00:00 kmemstick
  864 ?        00:00:00 udevd
  960 ?        00:00:00 kpsmoused
  985 ?        00:00:00 cfg80211
 1062 ?        00:00:00 nouveau/0
 1066 ?        00:00:00 nouveau/1
 1077 ?        00:00:00 i915
 1079 ?        00:00:00 iwlagn
 1115 ?        00:00:00 phy0
 1156 ?        00:00:00 ttm_swap
 1158 ?        00:00:00 kslowd000
 1159 ?        00:00:00 kslowd001
 1166 tty1     00:00:00 recovery-menu
 1231 ?        00:00:00 flush-7:0
 1232 ?        00:00:00 flush-7:1
 1233 ?        00:00:00 flush-7:2
 1234 ?        00:00:00 flush-7:3
 1235 ?        00:00:00 flush-7:4
 1236 ?        00:00:00 flush-7:5
 1237 ?        00:00:00 flush-7:6
 1238 ?        00:00:00 flush-7:7
 1258 ?        00:00:00 hd-audio0
 1293 ?        00:00:00 cupsd
 1302 tty1     00:00:00 root
 1305 tty1     00:00:00 bash
 1321 tty1     00:00:00 ps

---

