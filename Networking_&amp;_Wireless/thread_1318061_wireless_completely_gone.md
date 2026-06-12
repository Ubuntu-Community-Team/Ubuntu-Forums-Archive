---
title: "wireless completely gone"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by pleoni on 2009-11-07
hi,

I recently bought an eMachine E525 and installed Ubuntu on this. Like mentioned in many posts the wireless does not work.

I got it to work using the command
sudo ifconfig wlan0 up

but it dropped very often randomly but whenever I used the webcam with skype, it dropped after a very short period. This seemend like a rule, rather than a random event.

So, I was trying out several things to upgrade the driver, perhaps wicd, but nothing worked

by now i uninstalled wicd again.

i don't know when in the process this exactly happened, but my wireless is completely gone. 

The output of iwlist scan is
lo The interface does not support scanning
eth0 The interface does not support scanning

the command ifconfig also only gives eth0 and lo as output

The "NetworkManager" with the icon on the top of the desktop, where it used to have 2 checkboxes, one for enabling internet and one for wireless, now does no longer shows the wireless

lspci goes give a network card: Atheros AR9285

All help would be appreciated...

---

### Post by chili555 on 2009-11-07
Does your wireless reappear if you open a terminal and do:```
sudo modprobe ath9k
iwconfig
```If so, we can force your system to load *ath9k* on boot.

---

### Post by pleoni on 2009-11-07
> **chili555 said:**
> Does your wireless reappear if you open a terminal and do:```
sudo modprobe ath9k
iwconfig
```If so, we can force your system to load *ath9k* on boot.

its back indeed now... finally. how do i force it to load on boot?

but now there is still the problem of the wireless connection dropping so fast, especially if I use Skype/video

---

### Post by chili555 on 2009-11-07
> how do i force it to load on boot?Please do:```
sudo gedit /etc/modules
```Add a single line:```
ath9k
```Proofread, save and close gedit. Substitute your favorite text editor, nano, kate, vim, etc., if you do not have gedit.> there is still the problem of the wireless connection dropping so fastWhat kind of signal strength do you have? Find out with:```
iwconfig
```You will see something like:> eth1      IEEE 802.11g  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:2A:D7:29   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=85/100[/COLOR]
          --- snip ---
I have trouble staying connected much below 40/100. Does your router enable you to increase the signal strength?

You might play with MTU. If your connection is DSL, your MTU should be 1492, instead of 1500, the default. Change it with:```
sudo ifconfig wlan0 mtu 1492
```If this helps, we can make it permanent.

Post back and let us know.

---

### Post by pleoni on 2009-11-08
iwconfig output
```
root@pleoni-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sunray"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E8:34:FA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Isn't this strange that my link quality is something/70 rather than out of 100? i tried running it a couple of times; now is was 44/70

> **chili555 said:**
> Does your router enable you to increase the signal strength?

no it doesnt. I have a crappy router, a US robotics, really old ADSL router

> **chili555 said:**
> You might play with MTU. If your connection is DSL, your MTU should be 1492, instead of 1500, the default. Change it with:```
sudo ifconfig wlan0 mtu 1492
```If this helps, we can make it permanent.
The output of [:code]ifconfig[/quote] is indeed 1500 MTU:

```

root@pleoni-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:24:32:b1  
          inet6 addr: fe80::226:22ff:fe24:32b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21800631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627032 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:270428669 (270.4 MB)  TX bytes:289086600 (289.0 MB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11646 (11.6 KB)  TX bytes:11646 (11.6 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:2c:da:fb  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe2c:dafb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419989 (419.9 KB)  TX bytes:135183 (135.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 0C-60-76-2C-DA-FB-32-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'll try to see if I can stay online now with this new setting. Thank so much for your help

---

### Post by DJ . on 2009-11-08
Hello, I have the same problem, but my router has a wep password on it. Can you help?

---

### Post by pleoni on 2009-11-08
If I restart my PC, the connection is perfect:

```
wlan0     IEEE 802.11bgn  ESSID:"Sunray"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E8:34:FA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by DJ . on 2009-11-08
> **pleoni said:**
> If I restart my PC, the connection is perfect:

```
wlan0     IEEE 802.11bgn  ESSID:"Sunray"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:C0:49:E8:34:FA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Glad it works 4 you :)
Unfortunately, I am still working on mine.

---

### Post by pleoni on 2009-11-09
> **DJ . said:**
> Glad it works 4 you :)
Unfortunately, I am still working on mine.


qwll only after a restart, then the quality goes down again

---

