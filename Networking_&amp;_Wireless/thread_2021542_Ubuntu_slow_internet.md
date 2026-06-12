---
title: "Ubuntu slow internet"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by ibrahim52 on 2012-07-09
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

Above are the Wired & Wireless Cards of my laptop Lenovo G550. I was a fedora user and than since i had some issues with Fedora 17 i moved to Ubuntu, i liked it but there are so many issues going on with Broadcom cards, following are the issues i have faced and noticed always.

    My wireless card does not support HW550-3G - Aztech routers, the LAN works fine but the internet stops in less than a minute and its too annoying it never works again.

    If i download something from my Dual Boot Windows, because i have 40Mbps connection, it takes 2 minutes to download 50MB of file where UBUNTU takes 8 minutes and the download speed is around 200KB/sec where windows boost upto 3MB/sec

    Again wherever i go, page loading is dead slow.

    I tried even connecting USB wireless still there is no change in download speed.Thinking that it might be the issue of my wireless card

    Please advice me if there are issues with broadcom or is there any driver update because whenever i try updating my driver it says, i can't because i have low powered bcm43xx card. Should i change it or simply switch to WINDOWS or FEDORA again.

---

### Post by chili555 on 2012-07-09
> My wireless card does not support HW550-3G - Aztech routersPerhaps your card doesn't have the correct driver. Please do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now does the wireless work? Is, by chance, the ethernet working better?

---

### Post by ibrahim52 on 2012-07-09
Hi,
according to the solution provided in the link below, i had removed the STA Drivers and installed the following :

```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
```

Referred link :
[http://ubuntuforums.org/showthread.php?t=1932922](http://ubuntuforums.org/showthread.php?t=1932922)

Should i uninstall it and than execute those two commands or leave it as it is ?

---

### Post by chili555 on 2012-07-09
> **ibrahim52 said:**
> 
Should i uninstall it and than execute those two commands or leave it as it is ?Leave it as is. You know how the b43 and firmware solution is working; it isn't, obviously. Please reinstall bcmwl-kernel-source and let's go from there.

The reinstall will blacklist b43 so a reboot will get you going I suspect.

---

### Post by ibrahim52 on 2012-07-09
Tried even the ethernet but the download speed never goes more than 200 or 300KB/sec but if i am using windows. It takes to 4MB/sec in just two seconds and yeah my ethernet is also BCM (unfortunately).

Did run those two commands you mentioned so restarting my laptop, is there any other output i can post over here to have more clear picture ?

---

### Post by chili555 on 2012-07-09
Why don't we start with the ethernet. Please let us see:```
dmesg | grep -e tg3 -e eth0
ping -c3 www.google.com
nm-tool
```Thanks.

---

### Post by ibrahim52 on 2012-07-09
Well my concern is only wireless because usually its wireless i use everywhere, so if you don't mind. Shall we start with wireless first :) ?

---

### Post by ibrahim52 on 2012-07-09
I had tried installing the kernel source and than modprobe but than the wireless stopped working after the REBOOT and than i had to uninstall all the bcm43 related drivers.

Installed only ADDITIONAL DRIVERS (STA) and than did the kernel source & modprobe.

---

### Post by ibrahim52 on 2012-07-09
```
 [    1.859629] tg3.c:v3.121 (November 2, 2011)
[    1.859688] tg3 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.859705] tg3 0000:07:00.0: setting latency timer to 64
[    1.904256] tg3 0000:07:00.0: eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address xx:xx:xx:xx:xx:xx
[    1.904261] tg3 0000:07:00.0: eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[    1.904264] tg3 0000:07:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    1.904267] tg3 0000:07:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.328295] tg3 0000:07:00.0: irq 48 for MSI/MSI-X

```

---

### Post by ibrahim52 on 2012-07-09
```
PING www.l.google.com (173.194.79.105) 56(84) bytes of data.
64 bytes from pb-in-f105.1e100.net (173.194.79.105): icmp_req=1 ttl=49 time=1469 ms
64 bytes from pb-in-f105.1e100.net (173.194.79.105): icmp_req=2 ttl=49 time=1626 ms
64 bytes from pb-in-f105.1e100.net (173.194.79.105): icmp_req=3 ttl=49 time=1259 ms

```

---

### Post by ibrahim52 on 2012-07-09
```
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth2  [kala9999] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    hamoksha:        Infra, C0:C1:C0:54:64:36, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    alice56:         Infra, 00:21:04:7A:1A:22, Freq 2417 MHz, Rate 0 Mb/s, Strength 24 WPA WPA2
    linksys:         Infra, 00:1E:E5:91:DD:28, Freq 2462 MHz, Rate 0 Mb/s, Strength 35
    *kala9999:       Infra, xx:xx:xx:xx:xx:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP
    ELDINO:          Infra, 80:B6:86:A0:05:E4, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    veronica:        Infra, 00:26:75:0C:3C:EA, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP

  IPv4 Settings:
    Address:         192.168.1.52
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.4.4
    DNS:             8.8.8.8


```

---

### Post by chili555 on 2012-07-09
> **ibrahim52 said:**
> Well my concern is only wireless because usually its wireless i use everywhere, so if you don't mind. Shall we start with wireless first :) ?Not at all. In order to correctly diagnose, please leave the ethernet detached. Let's get the driver to load on boot automatically first:```
sudo su
echo wl >> /etc/modules
exit
```Frankly, your settings look awesome until we see this:> 64 bytes from pb-in-f105.1e100.net (173.194.79.105): icmp_req=1 ttl=49 [COLOR="Red"]time=1469 ms[/COLOR]For comparison, on my adequate, but not spectacular system, the ping time  to Google is 37 ms. Let's see how far back the clog is:```
ping -c3 173.194.79.105
ping -c3 8.8.4.4
ping -c3 192.168.1.1
```In Network Manager, is IPv6 set to Ignore? Please see attached.

---

### Post by ibrahim52 on 2012-07-09
```
64 bytes from 173.194.79.105: icmp_req=1 ttl=49 time=314 ms
64 bytes from 173.194.79.105: icmp_req=2 ttl=49 time=854 ms
64 bytes from 173.194.79.105: icmp_req=3 ttl=49 time=785 ms

```

---

### Post by ibrahim52 on 2012-07-09
```
64 bytes from 8.8.4.4: icmp_req=1 ttl=49 time=313 ms
64 bytes from 8.8.4.4: icmp_req=2 ttl=49 time=311 ms
64 bytes from 8.8.4.4: icmp_req=3 ttl=49 time=635 ms

```

---

### Post by ibrahim52 on 2012-07-09
```
64 bytes from 192.168.1.1: icmp_req=1 ttl=255 time=2.76 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=255 time=2.67 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=255 time=6.73 ms

```

---

### Post by ibrahim52 on 2012-07-09
and i always i keep my ipv6 on ignored mode only.

---

### Post by ibrahim52 on 2012-07-09
One more thing i would like to inform you that, regarding the drivers below.

```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
```

I had to uninstall it and install only the ADDITIONAL DRIVERS (STA) and than the KERNEL SOURCE Driver because the wireless had stopped working totally with the firmware-b43-lpphy-installer

---

### Post by ibrahim52 on 2012-07-09
its so annoying and so slow that even i have to wait for YOUTUBE VIDEOS to load first so i should be able to watch it properly.

---

### Post by chili555 on 2012-07-09
Sticky little problem we have here. May I see:```
cat /etc/hosts
cat /etc/nsswitch.conf
```How did you get the Google DNS nameservers? Did you configure Network Manager?

---

### Post by ibrahim52 on 2012-07-09
```
127.0.0.1	localhost
127.0.1.1	ibrahim52-PC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by ronnysingh on 2012-07-09
All wireless cards are not fully compatible with Ubuntu but all of them are usually compatible with Ubuntu.

---

### Post by ibrahim52 on 2012-07-10
That's true but why the LAN works sometimes and internet not and when internet works why the speed is so limited comparing to Windows ?

---

### Post by ibrahim52 on 2012-07-10
@chilli555 : i removed STA Drivers (Additional Drivers) installed following :

firmware-b43-lpphy-installer
than
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

but its same there is just no change. If i use windows its awesome but Ubuntu is slow.

---

### Post by ibrahim52 on 2012-07-10
Do u think changing the wireless will resolve the issue ?

---

### Post by ibrahim52 on 2012-07-11
Ok it does not make any sense if i am booting from my live USB the speed is upto 3MB/sec but if i boot through the INSTALLED ubuntu , its the same tortoise speed. Whats the difference.

---

### Post by ibrahim52 on 2012-07-11
pinging google.com is 185ms in USB live and INSTALLED one, u know it already.

---

### Post by chili555 on 2012-07-11
> **ibrahim52 said:**
> Do u think changing the wireless will resolve the issue ?I doubt it. Weren't you having the same issue with wired ethernet? That suggests the issue is related to networking generally and not your wireless driver or device.

Your hosts and nsswitch.conf files look perfect. We see nothing to fix or tweak here. I wonder if it's a firewall problem. Let's momentarily disable the firewall and see if it changes anything:```
sudo ufw disable 
ping -c3 www.google.com
```Any change? In either case, quickly re-enable the firewall:```
sudo ufw enable
```Your ping times to the router/gateway are pretty solid:> 64 bytes from 192.168.1.1: icmp_req=1 ttl=255 time=2.76 msOnly when you get to the outside world do we see the slow-down:> 64 bytes from 8.8.4.4: icmp_req=1 ttl=49 time=313 msCould this be a problem with your router? Your ISP? Are your Windows machines unaffected?

---

### Post by puneetsoni on 2012-07-11
Has any one seen that the ethrenet connection to internet jams after every half an hour and then i need to restart the computer.

---

### Post by chili555 on 2012-07-11
> **puneetsoni said:**
> Has any one seen that the ethrenet connection to internet jams after every half an hour and then i need to restart the computer.Please start your own new thread and give us some details about your system: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by ibrahim52 on 2012-07-11
Honestly, i tried it this morning already by disabling the ufw but there was no change at all. still if i ping through windows or the usb live, it is 180ms and windows is 56ms.

These are the results after disabling the ufw

```
64 bytes from sea09s01-in-f17.1e100.net (173.194.33.17): icmp_req=1 ttl=57 time=287 ms
64 bytes from sea09s01-in-f17.1e100.net (173.194.33.17): icmp_req=2 ttl=57 time=287 ms
64 bytes from sea09s01-in-f17.1e100.net (173.194.33.17): icmp_req=3 ttl=57 time=286 ms


```

---

### Post by ibrahim52 on 2012-07-11
and yeah i tried both Ethernet and Wifi, the speed was amazing using USB LIVE DRIVE of ubuntu.

---

### Post by ibrahim52 on 2012-07-11
i did the IFCONFIG and found TUN0 , i don't have any VPN installed ?


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.170.xx.xx P-t-P:10.170.xx.xx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5803017 (5.8 MB)  TX bytes:548978 (548.9 KB)

---

### Post by chili555 on 2012-07-11
> the usb live, it is 180ms and windows is 56ms.Neither of those are very impressive times. Here is mine:> chili@LAPTOP60:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (173.194.73.103) 56(84) bytes of data.
64 bytes from vb-in-f103.1e100.net (173.194.73.103): icmp_req=1 ttl=43 time=[COLOR="Red"]36.8[/COLOR] ms
64 bytes from vb-in-f103.1e100.net (173.194.73.103): icmp_req=2 ttl=43 time=36.6 ms
64 bytes from vb-in-f103.1e100.net (173.194.73.103): icmp_req=3 ttl=43 time=37.9 ms
Are you certain you don't have a router or ISP problem? What does this tell us?```
traceroute www.google.com
```

---

### Post by ibrahim52 on 2012-07-11
woooohooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo , i got it it was OPENVPN, which was creating problem and keeping the VPN open all the time, thats why i was wondering like though i have so many websites block through my ISP why all the websites works always. :D wooohoooooooooooooooooooooooooooooooooooooooooooo its back, thanks a aload. chilli5555.

---

### Post by chili555 on 2012-07-11
Awesome! Glad it's working!!!

---

### Post by ibrahim52 on 2012-07-11
Thanks once again Chilli555 :)

---

