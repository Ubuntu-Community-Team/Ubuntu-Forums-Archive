---
title: "unable to browse internet :("
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by us11csalyer on 2011-05-25
At first I could browse the Internet and download like 5 torrents at the same time with frostwire running. A few days ago whenever frostwire was running I couldn't connect to any websites other than google. Today I can't even download one torrent without the internet not working. Ping, lookup, whois, ect are unable to complete.

My internet is roadrunner extreme. 30down/5up

Could my ISP saw my activity and decided to be a ****?

Frostwire, transmission bittorrent, and firefox(?) are all using the UPnP. My modem has UPnP enabled. Should I manually forward the program's ports?

I also notice that multiple things are assigned the same IRQ. Is this an issue?

---

### Post by mindstorms83 on 2011-05-25
> **us11csalyer said:**
> At first I could browse the Internet and download like 5 torrents at the same time with frostwire running. A few days ago whenever frostwire was running I couldn't connect to any websites other than google. Today I can't even download one torrent without the internet not working. Ping, lookup, whois, ect are unable to complete.

My internet is roadrunner extreme. 30down/5up

Could my ISP saw my activity and decided to be a ****?

Frostwire, transmission bittorrent, and firefox(?) are all using the UPnP. My modem has UPnP enabled. Should I manually forward the program's ports?

I also notice that multiple things are assigned the same IRQ. Is this an issue?
It could be that your ISP already was a ****, but decided to let you have a taste of freedom before dashing your hopes, ;), alright, now to help, first, check in your browser's settings for proxy servers (firefox:edit,options,advanced,network(tab)) You should then see a line saying something like"configure how firefox connects to the internet" click that button and go through all the resulting tabs and boxs and make sure that all of them are set to something like "direct connection, No proxy, automaticly detect proxy" etc etc, most other browsers are set up essentialy the same way, if you are using google chrome or any derivative, then I would reccomend you stop and switch to firefox :) also, what OS are you running, which version? and what bittorrent program are yu using?

---

### Post by us11csalyer on 2011-05-26
ubuntu 11.4
using pre-installed transmission bittorrent and firefox.
firefox is set to no proxy

i restarted and saw that my nic's irq# is used on 3 other devices.

---

### Post by mindstorms83 on 2011-05-26
oh, so what kind of device are you using to connect? (wireless PCI card, sb adapter, built in ethernet card, PCI ethernet card)?
the IRQ is the system that was used before plug-and-play came around, what is the IRQ number of you NIC, and what are those devices, also, type these commands into the terminal and tell me what you get

[COLOR=Red]lspci
iwconfig
ip addr


[COLOR=Black]Also, what is the brand of your NIC?[/COLOR]
[/COLOR]

---

### Post by us11csalyer on 2011-05-26
lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5750 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
family@family-G41M-ES2L:~$ 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:24:1d:ed:ba:66 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 6c:fd:b9:2f:06:20 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.4/24 brd 192.168.0.255 scope global eth1
    inet6 fe80::6efd:b9ff:fe2f:620/64 scope link 
       valid_lft forever preferred_lft forever

I have onboard 1000/100/10 gigabyte ether which I disabled.
I am using a 1000/100/10 nic card bought from bestbuy
irq is 10, or 11, with usb cntrl, bus something, and input something.
sorry i have short term memory issues.

---

### Post by us11csalyer on 2011-05-26
Just seen something and don't know if it matters.

loopback interface (lo)
IPv6 ::1  128  host

eth1 has a long hex key but in editing auto eth1 it has IPv6 as connect auto but the method is ignore.

---

### Post by us11csalyer on 2011-05-26
Is this considered solved?

I put my pc on the DMZ host address and now I can run torrents, and frostwire. I'm not getting the internet browsing speed that I think I should be getting but I can download and browse at the same time now.

---

### Post by us11csalyer on 2011-05-26
Okay I officially solved this issue

I turned off DMZ and the problem came back
I then found that my modem has firewall settings
I turned off ip flood detection and firewall protection.

Now i'm enjoying 5+ torrents at a time and still able to browse the internet and even watch youtube!

---

