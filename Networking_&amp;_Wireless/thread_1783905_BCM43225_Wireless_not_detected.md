---
title: "BCM43225 Wireless not detected"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Tillman32 on 2011-06-16
Hello, I know there are a million threads about this, but my problem tends to be slightly different. 

I've read the sticky on here, I've googled around for a few days now, I've re-installed new drivers, tried a lot of different things. A lot of people seem to be having the issue of being able to see wireless networks, but they can't connect. I'm not that far yet.

When I click on my connections area, near the top right of the screen, then I got to edit connections, under wireless there is no wlan0 or eth1, where as if I do the same for the wired network, it lists a eth0. For some reason my wireless is on eth1, but I can only see that though lshw -C network.

Sometimes my laptops wireless "Light" is on, and sometimes its not. When its on, it means the wireless is enabled. But even when it is on, unfortunately I still have the same issue. 

I'm on Ubuntu 11.04 64-bit. I'm using an Acer Aspire 7552G-5430, it has the BCM43225 Wireless card. 

Here is my lshw -C network 

 *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 20:6a:8a:30:f2:9b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.10.129 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 memory:d0100000-d010ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 88:9f:fa:34:59:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0200000-d0203fff


Thanks for your time.

---

### Post by chili555 on 2011-06-16
First of all, Network Manager is designed is designed to disallow a wireless connection if wired is available; in your case it is:> ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb [COLOR="Red"]ip=192.168.10.129[/COLOR] Second, the wireless interface for some Broadcom devices comes up as eth1, not wlan0; that's perfectly normal.> *-network DISABLED
description: Wireless interface
product: BCM43225 802.11b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: [COLOR="Red"]eth1[/COLOR]
version: 01
serial: 88:9f:fa:34:59:75
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
resources: irq:17 memory:d0200000-d0203fff
So we wonder why your wireless interface is showing as DISABLED. Where is the wireless switch or key combination set on your laptop at the moment? Please run and post:```
rfkill list all
lsmod | grep acer
```

---

### Post by Tillman32 on 2011-06-16
Here u go.

My wireless switch "off" and "on" on my keyboard, doesn't have an off or on position, if I hit the key combination, the light us supposed to go either "on" or "off". But it doesn't do that. It will in windows, but not in linux. 


0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


acer_wmi               23771  0 
sparse_keymap          13898  1 acer_wmi



Thanks again for your time.

---

### Post by chili555 on 2011-06-16
Let's see if we can get it going:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Now is your wireless working? If so, we'll need to tweak a file or two to make it persistent.

---

### Post by Tillman32 on 2011-06-16
AWESOME! It works, and I'm connected to my wlan, okay so now how do I make it permanent?

P.S You are a God.

---

### Post by chili555 on 2011-06-16
Let's blacklist acer-wmi and run rfkill on boot:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a line at the end:```
blacklist acer-wmi
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/rc.local
```Add a new line above exit 0```
rfkill unblock all
```Proofread carefully, save and close gedit.

Enjoy your wireless. I'm glad it's working.

---

### Post by Tillman32 on 2011-06-16
Okay, so I'm assuming to test this I need to restart my computer. So I restarted and its still working, looks like it works.


If you don't mind, I'm a developer at a software company, I recently made the switch to linux due to the fact that I'm also going to be working with their linux db's. So if you have time I'd like you to briefly explain sorta what you did, just so I can learn.

It looks to me like you unblocked that soft block. 

I'm sorta curious why it would block it right off the bat with this clean install. 

Thanks again.

---

### Post by chili555 on 2011-06-16
Many laptops require a little module to translate key presses, Fn+F5, for example, into usable information like, "Turn on the dang wireless!" Some examples are acer-wmi, dell-laptop, ideapad-laptop, et al. Learn a bit more with:```
modinfo acer-wmi
```The trouble is, they often don't work very well. I suspect we could force another series than what the module detects and make it work, however, I've yet to find any substantial documentation telling me to use force_series=123xyz for the Acer 123 laptop.

You could probably gain more information by issuing:```
sudo modprobe acer-wmi
sudo rmmod -f acer-wmi
```Then check:```
sudo tail -n20 /var/log/syslog
```You might see more about the mechanism that takes place when the module loads and tries (unsuccessfully) to detect your Acer model.

The only remedy I've found so far is to remove the module altogether. At least it gets the wireless working so we can go on line and Google up a better solution!

Post back if you'd like to discuss this further; I'm happy to help.

---

### Post by SUPERFITTER on 2011-06-17
[FONT=Times New Roman][SIZE=4]I have a similar problem. I'm on **[COLOR=#ff0000]Ubuntu[/COLOR]** **[COLOR=#ff0000]11[/COLOR]**.04 64-bit. I am using an E machine laptop with a duel boot Win XP and Ubuntu. Both systems work great, the XP can go on line with a touch of the Fn and F2 keys but the Ubuntu mode will not. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I do not have a manual switch or button to activate the wireless. I don&#8217;t want to mess up the windows XP Fn, F2 connection when I boot into XP. What should I do to connect Ubuntu to the Internet?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Are there other keys to activate wireless in Ubuntu or the wireless (addresses) routers in my area?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Is there a directory of key combinations that work with Ubuntu?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I used Ctrl, Alt and 6 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]rfkill list [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]to find that. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Wireless Lan[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Soft blocked: no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Hard blocked: no[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I am using a Linksys Router.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I can connect Ubuntu with a wired connection but not wireless. My drivers are up to date.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Sorry for the rambling, just a newbie question that I cannot find an answer that fits without me worrying about messing things up.[/SIZE][/FONT]

---

### Post by nm_geo on 2011-06-17
> **SUPERFITTER said:**
> [FONT=Times New Roman][SIZE=4]I have a similar problem. I'm on **[COLOR=#ff0000]Ubuntu[/COLOR]** **[COLOR=#ff0000]11[/COLOR]**.04 64-bit. I am using an E machine laptop with a duel boot Win XP and Ubuntu. Both systems work great, the XP can go on line with a touch of the Fn and F2 keys but the Ubuntu mode will not. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I do not have a manual switch or button to activate the wireless. I don’t want to mess up the windows XP Fn, F2 connection when I boot into XP. What should I do to connect Ubuntu to the Internet?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Are there other keys to activate wireless in Ubuntu or the wireless (addresses) routers in my area?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Is there a directory of key combinations that work with Ubuntu?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I used Ctrl, Alt and 6 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]rfkill list [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]to find that. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Wireless Lan[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Soft blocked: no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Hard blocked: no[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I am using a Linksys Router.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I can connect Ubuntu with a wired connection but not wireless. My drivers are up to date.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Sorry for the rambling, just a newbie question that I cannot find an answer that fits without me worrying about messing things up.[/SIZE][/FONT]

You may not get another answer here as Chili and the OP have solved the problem. i usually read the threads that Chili is working to learn more, but he knows the OP's problem is solved and may not return to this thread. I would recommend four things.

Open terminal 

run these three codes:

1 ```
lspci -nn
```2 ```
sudo lshw -C network
```3 ```
rfkill list
```Then start another new Thread and add the result of those first 3 codes.

---

### Post by SUPERFITTER on 2011-06-18
[FONT=Times New Roman][SIZE=4]nm_geo [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Thanks for the heads up[/SIZE][/FONT]

---

### Post by martinkorlu on 2012-09-11
root@bt:~# lshw -C network   *-network                        description: Ethernet interface         product: NetLink BCM57780 Gigabit Ethernet PCIe         vendor: Broadcom Corporation         physical id: 0         bus info: pci@0000:02:00.0         logical name: eth0         version: 01         serial: 1c:75:08:bd:84:5e         size: 100MB/s         capacity: 1GB/s         width: 64 bits         clock: 33MHz         capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on  broadcast=yes  driver=tg3 driverversion=3.117  duplex=full  firmware=sb ip=192.168.2.7 l atency=0  link=yes  multicast=yes  port=MII  speed=100MB/s         resources: irq:44 memory:d4800000-d480ffff    *-network UNCLAIMED         description: Network controller         product: BCM43225 802.11b/g/n         vendor: Broadcom Corporation         physical id: 0         bus info: pci@0000:03:00.0         version: 01         width: 64 bits         clock: 33MHz         capabilities: pm msi pciexpress bus_master cap_list         configuration: latency=0         resources: memory:d3800000-d3803fff         dont know what to do next... i'm stuck. please help

---

