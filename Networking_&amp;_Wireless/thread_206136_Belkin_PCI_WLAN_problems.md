---
title: "Belkin PCI WLAN problems"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2006-06-29
I've been at it for a week and have lost count at the number of hours I have devoted to getting online with Kubuntu installed my HD. Yet I've been very briefly online booting with Ubuntu and Kubuntu live 6.06 CDs and also with my installed Kubuntu. So far Bill & Co are winning.

For the time being I've two issues. How do I connect Kubantu with a Belkin F5D7000 reliably to my Linksys WAG54G router and next how do I connect to the internet. It's not that I haven't seen Google briefly several times both on live CD boots and my installed Kubuntu. My two XP PC's are connected to the WLAN although I'll admit that they work better if only only one PC is on using our WLAN.

I've several problems using Kubuntu, let's start with the first. I want sudo iwconfig to show I have a WLAN link when I boot up Kubuntu. I've retyped my sudo nano /etc/network/interfaces file. (I'm not sure why I couldn't cut and paste from Open office where I'd copied this network/interfaces file and then onto a USB memory stick.) Next I want my Linksys WLAN's DHCP server in the router to include my new Kubuntu loaded PC.

Here's my sudo nano /etc/network/interfaces 

auto lo
iface lo inet loop
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid xxxxxxxx
wireless-channel x
wireless-key xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx-xx

auto ra0

When I tried out Ubuntu live on my XP machine I used a ndiswrapper for my XP's machine Linksys PCI card. My Belkin CD software though doesn't have a .bin file but anyway my Belkin ra2500 card and ra2500 drivers should be OK with Dapper D because the drivers are there already they tell me.

I've tried setting sudo /sbin/ifconfig ra0 192.168.1.100 up
I've tried using Network Assistant.
sudo dhclient ra0 doesn't find any offers.

Last night my router recognised my Linux PC as a client with a wireless connection but not as a DHCP client. Today I have no link with my router.

Is there any problem with my ralink 2500 card being called ra0 and not wlan0?

How should I set the IP addresses? I have a dynamic IP from my ISP.

I've disabled IPv6 which made no difference.

Yes and I'm careful about my typing of ra0 instead of ra0.

I've posted on the beginners forum but had few replies.

Any help would be appreciated

---

### Post by Handssolow on 2006-07-01
Well I've finally on the internet with my Linux PC running Kubuntu 6.06 and this is my first post with it.

Many further hours were spent yesterday and last night with no luck. I tried everything. I briefly got connected to my router once but lost the link when I tried to connect to the internet and Google. In the past week I've seen Google about twice for half a second, briefly accessed my router's web page about four times and had sudo iwconfig report link quality of about 48/100 for around 20% of time.

This morning I decided to try moving my Linksys WAG54G ver 1.2 wireless ADSL modem router using a telephone lead extention  next to the PC and I connect!!

Link quality reported before with the router in a different room was around 48/100, with the router on top of the PC it's 92/100, two metres away its 83/100.

Where's the problem? My WAG54G router, my Belkin PCI ralink 2500 card, my settings or do I need to rebuild my house? 

Any helpful comments?

---

### Post by Handssolow on 2006-07-02
Today I ordered a new Netgear WLAN ADSL router to replace my Linksys WAG54G-UK ver 1.2. There now seems little doubt that some of my difficulties in setting up a connection can be traced to my Linksys router. We're now increasingly losing WLAN connection when we use our two XP machines and we're have to frequently switch off the Linksys router to allow it to cool down.

From day one the Linksys router ran hotter than I thought it should and looking on the Internet I discovered that is a common Linksys feature, with people adding cooling fans. Component failures are likely to be greater the higher the temperature.

Whilst I notice there may be some issues with Dapper D dropping connections if the PC is idle, consider the possibility of your router being faulty or losing output. Looking on the Internet the router seems like one of the most unreliable pieces of kit.

---

### Post by Handssolow on 2006-07-04
My new Netgear ADSL modem wireless router DG834PN arrived today to replace my old Linksys toaster/house warmer and I've now got my three PCs configured for the new WLAN router. 

My Ubuntu PC is furthest away from the router and it took a few goes to input my new essid before it had been updated. (Checking with sudo iwconfig)
I used both System>Administration>Networking 
and
sudo nano /etc/network/interfaces

Initially I was unable to get a link, fortunately I had another phone socket closer and I was temporarily able to move the wireless router closer to the PC. Another go with
sudo dhclient
and we're off.

I've moved the router back and the link quality has gradually risen from <20/100 to 52/100. I'd put this down to the characteristics of this model of Netgear router.

My journey of a thousand miles starts with my first step.

---

