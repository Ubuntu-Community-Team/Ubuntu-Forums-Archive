---
title: "Can't connect to router: Ubuntu XP dual boot"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by SatishP on 2009-04-06
Hi All,
I have a dual boot machine with Windows XP Professional and Ubuntu 8.04 LTS. I have a ADSL internet connection and I have a wireless router. I run a cabled connection from my machine to the router. The router is configured to dial in as soon as it is switched on. I can connect to the internet from Windows.
I am trying out Ubuntu as a substitute for my 'un-licensed' Win but am stuck with the internet connection issue.

I have two ethernet cards (one of them does not work) - Realtek and Davicom. I do see 'eth0' and 'eth1' in my System-Administration-Network but neither of them works. I was not able to figure out which one of them corresponds to my Davicom card (Realtek card does not work). My router connects to internet fine and I am able to browse from my work laptop (connected to the router over wireless)

My ADSL modem's IP is **192.168.1.1** and my router's **192.168.10.1**. The output from ifconfig is below:

```
eth0     Link encap:Ethernet   HWaddr  00:80:ad:84:f2:f8
         UP BROADCAST MULTICAST   MTU:1500   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:20 Base address:0xd000

eth1     Link encap:Ethernet   HWaddr  00:13:d3:08:4b:46
         UP BROADCAST MULTICAST   MTU:1500   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:16 Base address:0xd1000

eth0:avahi  Link encap:Ethernet     HWaddr 00:80::ad:84:f2:f8
            inet addr: 169.254.12.7  Bcast: 169.254.255.255  Mask:255.255.0.0
            UP BROADCAST MULTICAST   MTU:1500  Metric:1
            Interrupt:20 Base address:0xd000

eth1:avahi  Link encap:Ethernet     HWaddr 00:13:d3:08:4b:46
            inet addr: 169.254.4.92  Bcast: 169.254.255.255  Mask:255.255.0.0
            UP BROADCAST MULTICAST   MTU:1500  Metric:1
            Interrupt:16 Base address:0xd1000

lo       Link encap:Local loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:924 errors:0 dropped:0 overruns:0 frame:0
         TX packets:924 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:46732 (45.6 KB)  TX bytes:46732 (45.6 KB)         

```

I have noticed one other strange thing. As soon as I switch on my machine, the LED on the router corresponding to my machine comes up. But after Ubuntu starts, it goes into blinking mode (not as rapidly as it does during data transfer). It comes on, stays on for a few seconds and then goes off for a few seconds.

As you might have guessed, I am a total newbie and hence appreciate all and any help that comes my way.

Thanks
Satish

---

### Post by alfplayer on 2009-04-06
```
I was not able to figure out which one of them corresponds to my Davicom card
```
The third post in this thread might be useful:
[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-determine-which-physical-interface-corresonds-to-eth0-eth1-eth2-and-eth3-638984/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-determine-which-physical-interface-corresonds-to-eth0-eth1-eth2-and-eth3-638984/)

Apparently the network cards are working. It looks like the cable from your machine to the router wasn't connected when you got that ifconfig output, is that right? If it is connected you may be having a faulty cable or a misconfigured router (DHCP server not set).

You can try setting a static IP in the network card you try to use.

---

### Post by SatishP on 2009-04-07
Thanks alfplayer!! I will check the link and find out the right 'eth'.

Coming to the actual issue, I figured something's amiss with the physical connection but everything works quite well when I boot XP. Only when I boot Ubuntu, the LED on the router starts blinking (like it's in sleep mode). I will verify it again. 

I would try the static IP setting (giving the same values as that in XP's TCP/IP Properties) and see if that helps.

Thanks for your help.

---

### Post by Iowan on 2009-04-07
Check **lshw -C network**. That might help identify which card is which.

---

### Post by SatishP on 2009-04-07
Thanks Iowan. I figured which is which by comparing the MAC address and XP's physical address values. Nevertheless, I learned something new from your tip. Thank you

I referred another thread "[[COLOR="RoyalBlue"]_How to fix problem with Davicom Ethernet Adapter in Ubuntu_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=186430")" but the resolution given there did not work for me.

I am pretty sure something's wrong with the connection between my machine and the router as the LED does not stay on. But since XP connects just fine, there might be a problem with the hardware in Ubuntu. But I am out of ideas. Looks like I have to get back to XP.

---

### Post by superprash2003 on 2009-04-07
your pc isnt getting an ip.. try typing the following 2 commands in your terminal and post output.
1)sudo dhclient eth0
2)sudo dhclient eth1

---

### Post by alfplayer on 2009-04-07
I don't think the card's LED is a problem (it can be intermittent or it can be off after the driver is loaded).

Also, both cards are being detected by linux so you can try to use both cards (maybe you simply couldn't make the card you think is faulty work).

---

### Post by SatishP on 2009-04-08
> **superprash2003 said:**
> your pc isnt getting an ip.. try typing the following 2 commands in your terminal and post output.
1)sudo dhclient eth0
2)sudo dhclient eth1
I configured 'eth0' to use static IP (because that's how it is configured in Win XP). I will post the both the outputs (from *ifconfig* and the commands above) as soon as I reach home.


> **alfplayer said:**
> I don't think the card's LED is a problem (it can be intermittent or it can be off after the driver is loaded).
The LED I mentioned was not of the ethernet card but on the router. My router has four ethernet ports (along with wi-fi). I connect my machine to the port numbered '1' and the corresponding  LED '1' on the front of the router lights (as soon as I switch on my PC). If I boot Windows, this LED remains ON but if I boot Ubuntu, the LED goes into intermittent on/off.
Also when I shut down Ubuntu, I see some errors related to NetworkManager. Is there any log where these errors are logged?


> **alfplayer said:**
> Also, both cards are being detected by linux so you can try to use both cards (maybe you simply couldn't make the card you think is faulty work).
Oops! I presumed the card to be dead since in Windows, my connection wouldn't work if I connect the cable to this card.



I would post some more information soon. Maybe it would make sense to you experts.

Again, thanks for taking time to help me out.

---

### Post by SatishP on 2009-04-08
I have attached the outputs for the following commands:
[LIST=1]
[*] ifconfig -a
[*] dhclient eth0
[*] dhclient eth1
[*] lspci
[*] dmesg
[/LIST]

Other files (**/etc/modules** and **/etc/modprobe.d/blacklist**) that I modified y'day are also attached

Please let me know if there's anything wrong with my setup/hardware.

---

### Post by superprash2003 on 2009-04-08
have you tried pinging your router?? ping 192.168.10.1

---

### Post by SatishP on 2009-04-08
> **superprash2003 said:**
> have you tried pinging your router?? ping 192.168.10.1

I get a '*Destination Host Unreachable*' message.

---

### Post by alfplayer on 2009-04-08
```
I configured 'eth0' to use static IP (because that's how it is configured in Win XP)
```Are you sure that eth0 (the Davicom card) is the adapter that is working with static ip in XP?
from your dmesg output:
```
eth0: Davicom DM9102
...
8139too Fast Ethernet driver 0.9.28
...
eth1: RealTek RTL8139
```You can try to ping your card with static ip:
```
ping 192.168.10.2
```If this fails there may be a driver issue.

The Davicom card is using the driver 8139too. Is this appropriate for your card?
That article about the Davicom adapter is old. Maybe someone solved the problem so that it isn't necessary to blacklist the tulip driver (you can try booting Ubuntu with or without that line in /etc/modprobe.d/blacklist)

Also, the command dhclient may not work properly on an interface set to static ip (can the command assign an ip address on an interface with a static ip?). The commands dhclient eth0 or dhclient eth1 try to connect to the router through the interface eth0 or eth1 respectively, so you need to connect the cable to the eth0 card when you run dhclient eth0 and connect the cable to the eth1 card when you run dhclient eth1. 

You can try setting back eth0 to dynamic ip, running dhclient eth0 and dhclient eth1 (with sudo) with the cable connected to each card when you do it. It would be nice if you could get a DHCP offer from the router.

---

### Post by SatishP on 2009-04-09
> ping 192.168.10.2
This works. I get the following message
```
64 bytes from 192.168.10.2: icmp_seq=xx ttl=64 time=0.0xx ms
```


> The Davicom card is using the driver 8139too. Is this appropriate for your card?
I have no idea which is appropriate. Wierd, but the 'lshw -C network' command shows that the eth0 interface is using 'dmfe' driver. Here's the relevant output from that command.
```
*-network:0
    description: Ethernet Interface
    product: 21x4x DEC-Tulip compatible 10/100 Ethernet
    vendor: Davicom Semiconductor, Inc
    physical id: 2
    bus info: pci@0000:01:02.0
    logical name: eth0
    version: 31
    serial: 00:80:ad:84:f2:f8
    width: 32 bits
    clock: 33 MHz
    capabilities: pm bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.10.2 latency=32 link=no maxlatency=40 mingnt=20 module=dmfe multicast=yes
*-network:1
    ...
    ...

```


I tried the DHCP/dhclient thing too. But nothing happened. It tried to get an ip from the router for sometime but later spit out the following message
```
No DHCPOFFERS received
No working leases in persistent database - sleeping.

```

There are a couple of things I am planning to try:
1. Unblacklisting the tulip driver and checking again
2. Lastly, going for Ubuntu 8.10 in the hope of resolving the issue.

Thank you all.

---

### Post by superprash2003 on 2009-04-09
do keep us updated.. its pretty weird that you arent getting an ip address via DHCP.. if windows can get one..

---

### Post by alfplayer on 2009-04-09
If the Davicom card works in Windows with static ip you should try to make the card work with static ip first.

Did you set the static ip with Network Manager? No matter how you did it, you needed to set at least three or four values (copied from Windows): the address (192.168.10.2), the netmask (255.255.255.0), the gateway (192.168.10.1), and at least one DNS server (the address can be the router's address, one provided by your ISP, or a free public one like OpenDNS).

It's important to set the DNS server address to have everything working but it doesn't make a difference if you can't ping the router.

> its pretty weird that you arent getting an ip address via DHCP.. if windows can get one..     Can he connect with a dynamic ip with windows?

> Unblacklisting the tulip driver and checking againYou can do this to check if it works (ping the card and the router) using the tulip module.
Anyway, the tulip module may never load if it is not meant to be used with your card.

---

### Post by SatishP on 2009-04-17
Hi All,
It's been a week since I stopped trying but today I felt I should give this some more tries.

I am almost sure now that the problem is with making my ethernet card work in Ubuntu. I executed the '***sudo ifdown eth0***' command and the LED on the router is ON now. As soon as I execute '***ifup***', it goes back to the annoying blinking/flashing.

When I open the syslog or the kern.log, I see a lot of 'eth0: Tx Timeout - resetting' messages.

Can I get the right driver for my card somewhere?


```
eth0: Davicom DM9102 at pci0000:01:02.0, 00:80:ad:84:f2:f8, irq 220.
```

---

