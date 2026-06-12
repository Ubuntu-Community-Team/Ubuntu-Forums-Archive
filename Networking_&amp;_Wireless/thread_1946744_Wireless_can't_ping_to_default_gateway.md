---
title: "Wireless can't ping to default gateway"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by bigpimpin1 on 2012-03-25
Hi,

After a year of Arch Linux, I decided to go back to xubuntu. It's working great. I'm having some strange kind of wireless problem though, which I can't seem to figure out for now. I can connect to the wireless network without a problem. However, sometimes I can't surf the web, and sometimes I can. My machine is set up for DHCP and always gets a correct IP address in the correct subnet with the correct default gateway. When I try to ping that gateway, I just get back no reply in some cases. In other cases, it's working without a problem.

1) Machine brand: Sony Vaio S12X9E
2) 
$ iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:"wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:35:3B:00:A5:3C   
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:681  Invalid misc:43   Missed beacon:0

```

3)
```

$ lsmod | grep 'iw'
iwlagn                314213  0 
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211

```

4)
```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:ea:dc:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=9.221.4.1 build 25532 ip=192.168.0.233 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:da400000-da401fff

```

5)
```

$ lsb_release -d
Description:	Ubuntu 11.10

```

6)
```

$ uname -mr
3.0.0-12-generic x86_64

```


Right now it's working again. But when I reboot the machine, chances are it's not anymore. These outputs always stay the same though. Also, other machines can connect without a problem. It's also not a DNS problem, since IP addresses aren't working either.

Thanks in advance!

---

### Post by wildmanne39 on 2012-03-25
Hi, I see a couple of things intel cards with linux drivers have trouble using N speed so the next time you can not connect try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn nohwcrypt=1
sudo ifconfig wlan0 up
```

Also if that does not help run these commands and post the output here:
```
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etork | tail -n55
```
It may help to turn wireless power management off.
Thanks

---

### Post by collisionystm on 2012-03-25
I had that same card somewhere in my life. It is the power control on the card.

I am sure the laptop will continue to work correctly its plugged into an external power source, but when on battery the power saving is enabled and it stops working correctly.

Its been a while so I honestly cant remember how I disabled power saving on the card, but I hope it points you in the right direction

---

### Post by bigpimpin1 on 2012-03-25
Thanks for the help.

@wildmanne39: I adjusted your code as follows:
([http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/))

```

sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1

```

I also added this to make it permanent:

```

gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf

```

This seems to be working for now. I will confirm this after a couple of reboots. Thanks for the good advice! 

@collisionystm: I did this. This could be helping as well, as I tried both things at the same time.
```

$ sudo iwconfig wlan0 power off

```

---

### Post by wildmanne39 on 2012-03-25
Hi, the way you did the power off it is only for one boot but I recommend we make it permanent.
Thanks

---

### Post by bigpimpin1 on 2012-04-01
The problem didn't occur again after the resolution of the N-speed incompatibility. Thanks a bunch for the help, again!

---

### Post by wildmanne39 on 2012-04-01
Hi, you welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

