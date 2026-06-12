---
title: "Internet not working right after boot"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by KeiNivky on 2012-06-16
Right after Ubuntu boots, I have no Internet connection. The ethernet works thou. I have to run dhclient in order to make the Internet work (sometimes I must run more than once). One thing I noticed is that the Ip after the boot is always 192.168.1.7, and also DNS server is set to a strange default, looking in the net I discovered that it is my ISP DNS server. My /etc/network/interfaces asserts that eth0 will use dhpc, I don't know where these default values are set. After I run dhclient, the server is changed to my router. I would like to set things up so that everything is working after the boot.

Another problem is that, after I set everything working with dhclient, past some random time even the ethernet stops working. I can't even ping my router. But this is really random. Some days it happens within a couple of minutes, some days within a couple of hours and some days it doesn't even happen.  Is there a way for me to know what is going on when this happens, and possibly fix it?

I am running Ubuntu 10.04.4,  ethernet card is a Realtek RTL8111/8168B. I have other computers on the network, I also have other Os'es in this computer, and all of them work correctly.

Below I'll write some commands outputs, just in case it may help:

right after booting:
```

$ ping www.google.com
ping: unknown host www.google.com

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=20.4 ms

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dhcp

$ cat /etc/resolv.conf 
nameserver 200.175.5.39
nameserver 200.175.89.39

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 14:da:e9:f3:c2:17  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:fef3:c217/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:33 overruns:0 frame:33
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2588 (2.5 KB)  TX bytes:3541 (3.5 KB)
          Interrupt:30 Base address:0xc000 

```Running dhclient and trying to ping google. It doesn't work at a first try:
```

$ sudo dhclient eth0
Listening on LPF/eth0/14:da:e9:f3:c2:17
Sending on   LPF/eth0/14:da:e9:f3:c2:17
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 39781 seconds.

$ cat /etc/resolv.conf 
nameserver 192.168.1.1
domain lan
search lan

$ ping www.google.com
ping: unknown host www.google.com

```So I decided to wait some time and try again. I did not run dhclient again, just waited some seconds. It worked. But, again, after waiting a bit of time it doesn't work anymore, so I try to ping my router to check the ethernet. The first three packets are lost, but afterward they started to come back.
```

$ ping www.google.com
PING www.google.com (177.99.189.226) 56(84) bytes of data.
64 bytes from www.l.google.com (177.99.189.226): icmp_seq=1 ttl=59 time=19.8 ms

$ ping www.google.com
ping: unknown host www.google.com

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1013 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=6.45 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.533 ms

```I also noticed that there are many "eth: link up" entries on dmesg output:

```

$ dmesg | tail -31
[   12.776349] r8169: eth0: link up
[   12.776354] r8169: eth0: link up
[   15.208105] r8169: eth0: link up
[   15.510659] r8169: eth0: link up
[   25.690415] eth0: no IPv6 routers present
[   86.922088] r8169: eth0: link up
[   87.169904] r8169: eth0: link up
[   88.688344] r8169: eth0: link up
[   99.231357] eth0: no IPv6 routers present
[  296.632185] r8169: eth0: link up
[  489.434882] r8169: eth0: link up
[  598.450412] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  598.530237] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  604.697340] r8169: eth0: link up
[  607.254592] r8169: eth0: link up
[  608.689136] r8169: eth0: link up
[  623.381364] r8169: eth0: link up
[  737.236723] r8169: eth0: link up
[  837.487647] r8169: eth0: link up
[ 1028.154749] r8169: eth0: link up
[ 1061.317655] r8169: eth0: link up
[ 1108.262172] r8169: eth0: link up
[ 1174.263663] r8169: eth0: link up
[ 1179.215922] r8169: eth0: link up
[ 1253.650062] r8169: eth0: link up
[ 1403.201881] r8169: eth0: link up
[ 1695.700384] r8169: eth0: link up
[ 1697.328117] r8169: eth0: link up
[ 1704.084355] r8169: eth0: link up
[ 1853.014957] r8169: eth0: link up
[ 1975.884243] r8169: eth0: link up

```

---

### Post by praseodym on 2012-06-16
> iface eth0 inet dhcp
Remove this line and reboot.

You may change the driver to r8168:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget [http://media.cdn.ubuntu-de.org/forum/attachments/24/23/3005217-r8168-dkms-8.031.00.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/24/23/3005217-r8168-dkms-8.031.00.tar.gz)
sudo tar xvf 3005217-r8168-dkms-8.031.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.031.00
sudo dkms build -m r8168-dkms -v 8.031.00
sudo dkms install -m r8168-dkms -v 8.031.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
```

---

### Post by chili555 on 2012-06-16
> $ cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dhcpYou haven't told the system you want to start eth0 automatically and it's doing exactly that:> Right after Ubuntu boots, I have no Internet connection. I disagree with my colleague. You need this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp 
```

---

### Post by praseodym on 2012-06-16
Well, if he wishes to do so (e.g. for wake-on-lan or sth.), he needs to change "false" to "true" in the file **/etc/NetworkManager/nm-system-settings.conf**, otherwise the network-manager ignores these settings.

---

### Post by chili555 on 2012-06-16
> **praseodym said:**
> Well, if he wishes to do so (e.g. for wake-on-lan or sth.), he needs to change "false" to "true" in the file **/etc/NetworkManager/nm-system-settings.conf**, otherwise the network-manager ignores these settings.I haven't read yet that he's running Network Manager. I suspected, since he could start the interface with dhclient, that he wasn't. How about it, KeiNivky?

---

### Post by KeiNivky on 2012-06-16
> **chili555 said:**
> I haven't read yet that he's running Network Manager. I suspected, since he could start the interface with dhclient, that he wasn't. How about it, KeiNivky?

I am not running network-manager.

I put "auto eth0" in /etc/network/interfaces and now the interface is correctly configured upon boot. I am still curious, do you have any idea where the previous configuration came from? The 192.168.1.7 ip and the dns server...

@praseodym, I am downloading the packages and the driver (it is at a really low speed, don't know why). As soon as it finishes I'll try it. Anyway, those "eth: link up" mean that the ethernet link is constantly going down? Is this unusual?

EDIT: Just installed the module. Should blacklisting r8169 prevent it from being loaded at boot time? Because it is still being loaded. Also, should I put r8168 into /etc/modules?

Just a question. What happens if one of these modules is loaded when the other is also loaded?

---

### Post by chili555 on 2012-06-16
> do you have any idea where the previous configuration came from? The 192.168.1.7 ip and the dns server...They are coming from the DHCP server, that is the router.

If the wireless is working as expected now, do you really want to install an alternative driver?> What happens if one of these modules is loaded when the other is also loaded? Probably neither will work.

---

### Post by KeiNivky on 2012-06-16
> **chili555 said:**
> They are coming from the DHCP server, that is the router.

But then why do I get a different DNS server when I boot with the misconfigured interfaces file from when I set "auto eth0" into it?

> **chili555 said:**
> 
If the wireless is working as expected now, do you really want to install an alternative driver?

I was considering the suggestion of installing other driver because I believed that the second problem I pointed out (losing the ethernet link with the router) was caused by the driver. Do you think it was caused by the /etc/network/interfaces misconfiguration? If so, after running dhclient, shouldn't everything be fine (since I would already get all the network info I need from dhcp).

---

### Post by chili555 on 2012-06-16
> $ cat /etc/resolv.conf 
nameserver 200.175.5.39
nameserver 200.175.89.39These are undoubtedly the listings in the router provided by the ISP when the router gets *its* IP address. It is the functional equivalent of simply the router's address, probably 192.168.1.1. I don't know why dhclient gives the router and /interfaces gives the underlying DNS nameservers. They do the same thing in the end. 

On a side note, you could learn about namebench and figure out and use the fastest DNS nameservers, not just the ones the ISP provides. [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/) The package namebench is available in the Ubuntu repositories.

Is your ethernet connection stalling now that /interfaces is corrected? If so, I would surely compile the newer driver and blacklist the old. praseodym's excellent instructions cover that quite well. Remember, my premise was, 'If the wireless is working as expected now...' If it is not, compile.

---

### Post by praseodym on 2012-06-16
Blacklist r8169, and
```

sudo modprobe -rfv r8169
sudo modprobe -rfv r8168
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

