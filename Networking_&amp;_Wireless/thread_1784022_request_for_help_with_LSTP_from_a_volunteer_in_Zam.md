---
title: "request for help with LSTP from a volunteer in Zambia"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by DominicRowland on 2011-06-16
Apologies in advance for the length of this post - I want to give a bit of background.

A few months ago I came to Zambia from England as a volunteer teacher and despite knowing almost nothing about computers I was put in charge of ICT.

The school has an internet room and I believe the signal comes wirelessly to a big external antena on the roof. In any case there is a wireless router and my laptop (running Lucid) connects automatically.

There is also a fairly modern desktop which (I'm told) was intended to act as a server allowing four other monitors (without CPUs) to connect to the internet.  When I arrived the computer was running Windows and was doing all manner of scary things which presume were due to innumerable viruses etc. I installed Natty (desktop) and although the computer struggles with Unity it works ok with classic gnome. So we could get online which was nice.

Sadly I have no idea how to make the other monitors (thin clients?) work and know exactly zero about networking so am going to need spoon feeding to make this happen. 

If you have an interest in helping out a few Zambians and have a great deal of patience read on...


The PC has one cable contected to the router and four other cables each connected to a little black box (labelled Multi-User Network computing terminal). Each of these is connected to a monitor, keyboard and mouse.

I rather ineptly spent some time looking for advice online and found a set of instructions for setting up LTSP which I tried to follow without much success.

I was told to:

Set a static IP address which I think I managed (despite only having a vague idea what one is) 

Then

$ sudo apt-get install ltsp-server-standalone openssh-server

That was fine. Next I tried 

$ sudo ltsp-build-client 

Which took a while but completed without any scary messages

And now comes the bit where you are going to get exasperated with me - 

The next things I tried gave me errors but I didn't record the terminal output (sorry)

The next instructions were:

$ sudo /etc/init.d/networking restart 

and 

$ sudo /etc/init.d/dhcp3-server restart 

and now the bit where you Really start to hate me...



I found another set of instructions which differed on how to set the static IP. After following those the file /etc/network/interfaces now reads:

auto eth0 (I believe it may initially have said lo or l0 instead of eth0)
iface eth0 inet static
address 192.168.0.25
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1  
iface eth1 inet dhcp  (when I opened the file initially it did not have these two lines and I suspect that the mysterious eth1 I so optimistically typed in may not exist...)

The kicker is, of course, that now the internet doesn't work any more.

If you feel like taking this request on I will be eternally grateful.

---

