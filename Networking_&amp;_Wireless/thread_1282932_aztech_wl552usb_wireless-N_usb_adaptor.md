---
title: "aztech wl552usb wireless-N usb adaptor"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by engzks on 2009-10-04
i am using ubuntu 9.04 jaunty.

ubuntu seems to detect my card well using Ralink 802.11N wlan driver
but it cant detect my home wireless network (802.11G network).

> root@engzks-desktop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


when i check with another wireless usb adaptor (dlink 802.11b atmel)
i can see and connect to the network.

> root@engzks-desktop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 
                    ESSID:"whateverman"
                    Mode:Master
                    Channel=6
                    Encryption key: on
                    Signal level=35/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
          Cell 02 - Address: 
                    ESSID:"KW@Bitbit"
                    Mode:Master
                    Channel=11
                    Encryption key: on
                    Signal level=7/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s


what should i do to make the aztech card to detect the network?

---

### Post by chili555 on 2009-10-05
Does it make a difference if you:```
[COLOR="Red"]sudo[/COLOR] iwlist ra0 scan
```This is from *man iwlist*:> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.Obviously, if you have never scanned with ra0 before, you have no left-overs.

---

### Post by engzks on 2009-10-11
i am already using root.

i started with sudo -i before those commands

---

### Post by coffeeaddict22 on 2009-10-11
what's the output of ```
lshw -C network
```

---

### Post by ugutugut on 2010-05-05
Hi, I'm having the same problem with Aztech Wireless USB WL552USB, ie cannot detect the wireless network.

This is what I got when I issue command: lshw -c network

*-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:26:75:06:bb:7f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

and this is the result of command : iwconfig

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

can anybody help? thanks

---

### Post by ugutugut on 2010-05-05
Hi, it's me again, I can use my adaptor now.

Follow my curiosity, I search for the chip that used by WL552USB,
I found that it use chip RT2870, then I search about RT2870 and ubuntu.
I found the article about RT2870 behavior and Ubuntu, plus the solution to overcome it. 

The solution is to simply add the line

blacklist rt2800usb

in the file "/etc/modprobe.d/blacklist.conf"

Restart Ubuntu and viola! Its alive!

Thank you for the original poster - yousif

---

