---
title: "Very unstable wifi connection after upgrade to 12.04 (Intel Ultimate-N 6300)"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by mejo on 2012-05-11
Hello,

after dist-upgrade from 11.10 to 12.04 (64bit), my wifi connection got very unstable, and keeps bugging me. Until the dist-upgrade, everything worked fine. My hardware is a ThinkPad T420 with a Intel Ultimate-N 630 wireless network controller.

In short words, the connection stops working at some random point, and I didn't figure out why yet. Unfortunately no log message seems to be printed to any log file at the time of lost connection. NetworkManager keeps telling me that the connection is alive, but neither ping to the router/switch nor DNS-lookup work anymore. Ifconfig still lists the IP-address, and iwconfig doesn't show anything suspicious either.

Nobody else in the same Wifi-network has similar problems - even though I've to admit that nobody else uses Ubuntu here.

I already searched the forum. Some people seem to discover similar issues after upgrade to Ubuntu 12.04, though I'm not sure whether they're the same - at least it's on different hardware:
[http://ubuntuforums.org/showthread.php?t=1975442](http://ubuntuforums.org/showthread.php?t=1975442)
[http://ubuntuforums.org/showthread.php?t=1958059](http://ubuntuforums.org/showthread.php?t=1958059)

Unfortunately I don't have any idea about how to futher debug this problem. As one can imagine, it's very annoying. After all it randomly breaks my network/internet connection. Any help is much appreciates :)

Regards,
 jonas

Below follows some information about WLAN and hardware. No differences between working and non-working WLAN-connection.

```
$ lspci -v -s 03:00.0
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

``````
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: ****::****:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:65942630 (65.9 MB)  TX bytes:8546658 (8.5 MB)

``````
$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"**********" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9248  Invalid misc:57   Missed beacon:0

```

---

### Post by chili555 on 2012-05-12
Please try a driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Does stability improve? If so, we can write a quick file and make it persistent.

---

### Post by mejo on 2012-05-12
Thanks for the hint. It seems to do the rick.

I guess that you're refering to a issue with iwlwifi in kernel 3.2 discussed here: [https://bugzilla.redhat.com/show_bug.cgi?id=785239](https://bugzilla.redhat.com/show_bug.cgi?id=785239)

I added the option '11n_disable=1' for module iwlwifi in /etc/modprobe.d. Since this change, I didn't discover unstable/broken wifi connection issues so far.

---

### Post by chili555 on 2012-05-12
> I guess that you're refering to a issue with iwlwifi in kernel 3.2 discussed here: [https://bugzilla.redhat.com/show_bug.cgi?id=785239](https://bugzilla.redhat.com/show_bug.cgi?id=785239)
.ko-rrect. A little insiders driver joke there. The bug has lasted longer than kernel 3.2xx; it also affected the predecessor iwlagn and 3.0xx. I wish Intel would crack this case; N is here to stay.

If you please, use thread tools at the top to Mark Solved. The searchers will appreciate it.

---

### Post by mejo on 2012-05-13
> **chili555 said:**
> If you please, use thread tools at the top to Mark Solved. The searchers will appreciate it.

Sure, will do this. But first, I'll wait a few more days and see whether the wifi issues really disappeared. Thanks again for your help.

---

### Post by mejo on 2012-05-14
> **mejo said:**
> Sure, will do this. But first, I'll wait a few more days and see whether the wifi issues really disappeared. Thanks again for your help.

After two days with the new module parameter, no wifi connection problems any longer. Marking the problem as solved.

---

### Post by b3d on 2012-07-18
> **chili555 said:**
> Please try a driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Does stability improve? If so, we can write a quick file and make it persistent.

This worked for me.  Thanks!

---

### Post by richwales on 2012-08-12
This is a workaround, but not a true solution to the underlying problem.  Still, having a reliable connection (even at a slower speed) is much better than a flaky connection (or no connection at all).

---

### Post by qgil on 2012-09-26
Just a note to say that the problem can be reproduced still today with latest Ubuntu stable and a Thinkpad T430, also with Intel Corporation Centrino Ultimate-N 6300 (rev 3e)

The bug report to watch and vote seems to be 

[Oneiric] [Regression] Intel Corporation Centrino Ultimate-N 6300 poor networking, packet loss and very slow Lenovo X201 and T500 laptops
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250)

And the ultimate source:

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2315](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2315)

---

### Post by cleopatra on 2012-12-07
> **chili555 said:**
> Please try a driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Does stability improve? If so, we can write a quick file and make it persistent.

I have the same problem, tried the two sudo and they did not help.

I also tried to add "the option '11n_disable=1' for module iwlwifi in /etc/modprobe.d.", but I don't even find the file, here is ls:

-rw-r--r-- 1 root root 2507 Feb 15  2012 alsa-base.conf
-rw-r--r-- 1 root root  325 Apr 13  2010 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Apr 13  2010 blacklist.conf
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Jan 28  2010 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Nov 13 11:25 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Apr 13  2010 blacklist-watchdog.conf
-rw-r--r-- 1 root root  127 Apr 22  2012 dkms.conf
-rw-r--r-- 1 root root   16 Jan  6  2010 libpisock9.conf
-rw-r--r-- 1 root root   30 May 18  2012 vmwgfx-fbdev.conf

could anyone help me? Do I need to check my hardware? better if I could just change config files...

---

### Post by mejo on 2012-12-07
> **cleopatra said:**
> I have the same problem, tried the two sudo and they did not help.

I also tried to add "the option '11n_disable=1' for module iwlwifi in /etc/modprobe.d.", but I don't even find the file, ...

You can write the option to whatever file you like inside /etc/modprobe.d/. The whole directory is sourced by modprobe. I for example added a file /etc/modprobe.d/thinkpad.conf with (among others) the entry:

```
# disable 11n functionality to stabilize wifi
options iwlwifi 11n_disable=1
```

> **cleopatra said:**
> could anyone help me? Do I need to check my hardware? better if I could just change config files...

If that doesn't help, then I've no glue either, sorry.

---

### Post by chili555 on 2012-12-07
> Do I need to check my hardware? Yes, please run and post:```
lspci -nn | grep 0280
```> but I don't even find the file,The idea is, if we determine you need the file, we create the file. If the parameter didn't help, I doubt the file will help. We'll probably need to dig deeper.

---

### Post by cleopatra on 2012-12-08
> **chili555 said:**
> Yes, please run and post:```
lspci -nn | grep 0280
```The idea is, if we determine you need the file, we create the file. If the parameter didn't help, I doubt the file will help. We'll probably need to dig deeper.

Hi chili and mejo!

here it is, seems to be a constant hardware config:

$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)

A WEIRD thing is that I only have this wifi problem at home. And at home, it sometimes works fast, sometimes really slow, sometimes seemingly stagnant...

Now the wifi at home is ok. So maybe I should run some command when it runs slow to diagnose?

---

### Post by chili555 on 2012-12-08
You don't have an Intel card, the subject of this thread. Please start a new thread and send me a PM if I don't catch it right away.> [COLOR="Red"]Atheros[/COLOR] Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e]

---

### Post by albahnsen on 2013-02-11
Hi,

I'm having the same issue. already try the proposed solution but it only works for some time.

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)

Thanks.

---

### Post by chili555 on 2013-02-11
> but it only works for some time.Meaning what? It stops working effectively after a reboot or after an hour??

---

### Post by albahnsen on 2013-02-12
> **chili555 said:**
> Meaning what? It stops working effectively after a reboot or after an hour??

About a month. but since last week or so start having problems again.

Thanks.

---

### Post by chili555 on 2013-02-12
> **albahnsen said:**
> About a month. but since last week or so start having problems again.

Thanks.Please change the file you created from this:```

options iwlwifi 11n_disable=1
```...to this:```
options iwlwifi 11n_disable=1 bt_coex_active=N
```Reboot and let it run for a while and let us have your report.

---

### Post by albahnsen on 2013-02-12
Thanks! I will let you know how it works.

---

### Post by albahnsen on 2013-02-17
> **chili555 said:**
> Please change the file you created from this:```

options iwlwifi 11n_disable=1
```...to this:```
options iwlwifi 11n_disable=1 bt_coex_active=N
```Reboot and let it run for a while and let us have your report.

Guys it work for 3 days, but today it starts being unstable again. Now is different than before, every time it disconnect then it reconnects after a minute, in the past it would not reconnect until I restart. 

thanks.

---

### Post by chili555 on 2013-02-17
Have you set IPv6 to 'Ignore' in Network Manager? Please see attached.

I'm not sure I have any further suggestions aside from looking around in the router to see if there are any unusual settings that you might disable. Since we know the *iwlwifi* driver doesn't work well with 802.11N, I might set the router to use B and G only and see if it helps.

---

### Post by albahnsen on 2013-02-17
I just change the ipv6 setting as you suggest, will let you know if that work. otherwise I will make the change in the router.

thanks.

---

### Post by Genitruc on 2013-03-18
Hi,

     I got a similar problem with a centrino advanced N-6205. On my home network with WPA encryption I had frequent disconnection even if the network manager was showing that I was connected. I had to disconnect and reconnect on the network to have the connection back but it could last only for while (few minutes to few hours). 

    I changed my router and it solved the problem. I kept the same SSID and encryption settings and it works, I have no more disconnections. The router I had was pretty old and I guess the protocol wasn't implemented correctly.....I shouldn't give pronostic, I'm no specialist at all. Anyway, it works now.

Genitruc

---

### Post by Imagine93 on 2013-11-13
This fixed my problems on my vaio pro 13 with a N-7260 network card

---

