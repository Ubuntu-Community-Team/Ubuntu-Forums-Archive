---
title: "I need help to configure my wireless"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by hoboy on 2009-03-13
My computer has wireless it works on windows.
I ma using ubuntu 8.10.
when I go to System/Preferences/Network configuration, I se Wired Auto etho.
On the right side of it there is wireless when I click on it then click on add
I windows called wireless connction open with fields.

SSID;
MODE;
BSSID;
Mac Address;
MTU.
my problem I don't know ho to fell these fields.
i am using ADSL.

---

### Post by issih on 2009-03-13
If your wireless card is working, you don't need to mess with that.

Just right click on the networking icon in the system tray (in the top right) and make sure that enable wireless is selected.

At that point when you click on the networking icon you should get a list of detected wireless networks in range, and you simply click on the one you want to use and enter any necessary encryption passwords.

Hope that helps.

---

### Post by hoboy on 2009-03-13
> **issih said:**
> If your wireless card is working, you don't need to mess with that.

Just right click on the networking icon in the system tray (in the top right) and make sure that enable wireless is selected.

At that point when you click on the networking icon you should get a list of detected wireless networks in range, and you simply click on the one you want to use and enter any necessary encryption passwords.

Hope that helps.

When you said Just right click on the networking icon in the system tray (in the top right) ? is this the little computer picture on the right top ?
if so when i right click on that I only se Enable Networking

---

### Post by issih on 2009-03-13
Right, then your wireless card is almost certainly not being detected.

Start by opening a terminal (under accessories) and then enter:

```
sudo lshw -C network
```

enter your login password and hit enter when prompted and then copy and paste the output (use the mouse) here.

That will let us see what your networking hardware is and we can go from there.

Hope that helps

---

### Post by hoboy on 2009-03-13
> **issih said:**
> Right, then your wireless card is almost certainly not being detected.

Start by opening a terminal (under accessories) and then enter:

```
sudo lshw -C network
```

enter your login password and hit enter when prompted and then copy and paste the output (use the mouse) here.

That will let us see what your networking hardware is and we can go from there.

Hope that helps

luc@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:24:21:10:ed:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.2 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:0b:dd:ab:0c:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
luc@ubuntu:~$

---

### Post by issih on 2009-03-13
Hmmn I'm pretty sure that is not showing your wireless card at all. The eth0 interface is your hardwire interface, and pan0 is usually a bluetooth interface. It really should show up in there if it is connected to the computer. What kind of computer do you have, and what sort of wireless card?

integrated wireless, usb dongle?

---

### Post by issih on 2009-03-13
One thought, if this is a laptop with a switch/key combination to turn off the wireless networking, try using it and then running lshw again.

---

### Post by hoboy on 2009-03-13
> **issih said:**
> Hmmn I'm pretty sure that is not showing your wireless card at all. The eth0 interface is your hardwire interface, and pan0 is usually a bluetooth interface. It really should show up in there if it is connected to the computer. What kind of computer do you have, and what sort of wireless card?

integrated wireless, usb dongle?

I am using

Fujitsu Siemens stationary PC - AMILPI3620E0
about what sort of wireless i am using I don't know, i know it works on window I can se my Netgear on that then I use it without any internet cable.

---

### Post by hoboy on 2009-03-13
> **issih said:**
> One thought, if this is a laptop with a switch/key combination to turn off the wireless networking, try using it and then running lshw again.

It is stationary pc

---

### Post by hoboy on 2009-03-13
> **issih said:**
> Hmmn I'm pretty sure that is not showing your wireless card at all. The eth0 interface is your hardwire interface, and pan0 is usually a bluetooth interface. It really should show up in there if it is connected to the computer. What kind of computer do you have, and what sort of wireless card?

integrated wireless, usb dongle?
I have just copy and transalate from the machine specifiaction.

Interface/connection   	
TV ud 	DVI
TV tuner 	yes
Networkcard type 	10/100/1000
Wireless interface 	yes
USB 2.0 	8
FireWire (IEEE 1394) 	1
cardreader 	yes
Cardreader type 	USB, CF I&II, MD, SMC, MS, MSM, SD, SDHC, MC,

---

### Post by issih on 2009-03-13
well that computer model number turns up zero hits on Google and the fujitsu siemens website, so I can't even research what card it should have.

See if you can find a better model number anywhere, or we are going to grind to a rapid halt.

Can you also post the output of running "lsusb" and "lspci" in the terminal.

---

### Post by hoboy on 2009-03-13
> **issih said:**
> well that computer model number turns up zero hits on Google and the fujitsu siemens website, so I can't even research what card it should have.

See if you can find a better model number anywhere, or we are going to grind to a rapid halt.

Can you also post the output of running "lsusb" and "lspci" in the terminal.

Thanks for your time.

---

### Post by hoboy on 2009-03-13
> **issih said:**
> well that computer model number turns up zero hits on Google and the fujitsu siemens website, so I can't even research what card it should have.

See if you can find a better model number anywhere, or we are going to grind to a rapid halt.

Can you also post the output of running "lsusb" and "lspci" in the terminal.

sorry but this is a danish link to it, but this is an english forum

[http://www.elgiganten.dk/is-bin/INTERSHOP.enfinity/WFS/store-elgigantenDK-Site/da_DK/-/DKK/ViewSearch-Start;pgid=BSSz6oZKU8dSR0EjRNJBwx1k000070huROgi?searchtext=amilpi3620e01&categories=&submit=submit](http://www.elgiganten.dk/is-bin/INTERSHOP.enfinity/WFS/store-elgigantenDK-Site/da_DK/-/DKK/ViewSearch-Start;pgid=BSSz6oZKU8dSR0EjRNJBwx1k000070huROgi?searchtext=amilpi3620e01&categories=&submit=submit)

---

### Post by issih on 2009-03-13
We need a lot more detail than just that is should have a wireless interface. We need to know what manufacturer and what chipset the wireless uses. We also need to know why it isn't showing in lshw.

As an example the lshw information from earlier tells me that your ethernet port is an nvidia product running on the mcp73 chipset.

I need that level of information about your wireless hardware.

---

### Post by issih on 2009-03-13
There are no links I can find to find your hardware, and fujitsu don't admit that it exists, which makes it tricky.

please post the output of lsusb and lspci though, those are our last hope of finding out what the wireless card is short of you managing to find out, because I'm getting no where, hopefully there might be slightly more available in your area, given they sell it there :S

---

### Post by issih on 2009-03-13
After a bit of poking of the fujitsu site, I think you probably have this wireless card:

Azure Wave AW-NU222

Unfotunately most of the sites about it are in German, and my German is pitiful.

Your best bet would be to hunt about on google for someone who has that card working under linux (or ideally ubuntu) and try that.

You might even want to post a new thread asking for help with that specific card

I can't really help any more than that I'm afraid.

---

### Post by issih on 2009-03-13
After poking around in german ...here:

[http://209.85.229.132/search?q=cache:1lr9wjOd8boJ:forum.ubuntuusers.de/topic/wlan-injection-patch-problme-zd1211rw/next/+AW+NU222+linux&cd=12&hl=en&ct=clnk&gl=uk&client=firefox-a](http://209.85.229.132/search?q=cache:1lr9wjOd8boJ:forum.ubuntuusers.de/topic/wlan-injection-patch-problme-zd1211rw/next/+AW+NU222+linux&cd=12&hl=en&ct=clnk&gl=uk&client=firefox-a)

I think that your card is based on the ralink 2870 chipset, and a bit of a search around here turn up this:

[http://locoteam.ubuntuforums.org/showthread.php?t=960642](http://locoteam.ubuntuforums.org/showthread.php?t=960642)

as being probably your best bet.

Hope that helps

---

### Post by JerryI on 2009-03-13
Sorry to barge in, but it looks like you are chasing/diagnosing a problem similar to mine.  I can see my network 2wire411 from Ubuntu Hardy but cannot get the system to accept my wep key 0360663701 that is perfectly acceptable from other computers on my wireless network. Here's what I get from your suggested query:

jerry@laptop:~$ sudo lshw -C network
[sudo] password for jerry: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:86:5c:8e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1e:37:f6:cc:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
jerry@laptop:~$ 

Any idea how I can correct my problem and get online?

Thanks

Jerry Isaacs

---

### Post by issih on 2009-03-13
Generally you should start a new thread, and you are a lot further down the road than hoboy..you actually see a list of networks.

First of all try selecting to use a wep key rather than a passphrase (or vice versa) in the little dialog box.

If that doesn't work you should, temporarily, disable the encryption on your wireless network to check whether the wireless card is actually functioning.

Oh, and start a new thread..

---

### Post by JerryI on 2009-03-13
You're way ahead of me on unencryption, etc.  Three days ago I couldn't even spell Ubuntu.  I will start a new thread in Wireless and Networking and would appreciate it if you would pick it up.  I have been worrying about this problem for several hours and have a hunch you will be able to guide me.  I will entitle the thread 2wire Network WEP Key Loop

---

