---
title: "usb modem newbie help"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by markbol on 2010-09-07
Hi guys I'm a complete newbie to linux i,m running ubuntu 10.04 and i cant connect with 3g modem.I've tried with vodafone and 3 ireland.THE SOFTWARE ICON IS ON SCREEN WITH BOTH MODEMS but when i try to run they cant find autorun files is there a comand to run these files their in media/3connect/autorun.exe.do i need permissions or something ?bear in mind im a complete novice at this any advice would be very much appreciated, mark

---

### Post by Joe of loath on 2010-09-07
Why do you need to run the windows software? You should be able to set up a connection in network manager.

---

### Post by pricetech on 2010-09-07
windows software doesn't run in Linux.

See if you can get the modem to work.  If not, try searching the forums and the web for others with the same modem who may have it working.

Also check the vendor's website.

---

### Post by rsawoseyin on 2010-09-08
> **pricetech said:**
> windows software doesn't run in Linux.

See if you can get the modem to work.  If not, try searching the forums and the web for others with the same modem who may have it working.

Also check the vendor's website.

Honestly, this is the type of issue that does not encourage ordinary people to use any flavour of Linux. I installed Ubuntu on my Samsung NC10 netbook, alongside Windows XP. Mobile broadband with USB Modems is commonplace - just look around everywhere and you see people using it. I have been struggling to get mine to work with Ubuntu. There is the "Network Connections" which allows me to set up the parameters under the "Mobile Broadband" tab. It recognises my device, but there is nothing to click to actually connect. Yes - you have a window that lets you enter the relevant parameters, but does not have a "Connect" button.

Then you search forums to see how to actually connect. You read contributors saying "it is easy". But how? Some go into lengthy geeky commands. Well, up till now, I am unable to use my USB Broadband modems (I have 4 of them, from 4 differentg service providers) with Ubuntu. Ubuntu needs to make such a thing extremely simple.

---

### Post by jarviser on 2010-09-12
I have an example of my experiences with 2 different modems. You will need to know the correct APN for your mobile service as per the article below which works for any dongle that is recognised by Lucid, and that's most of them.

[http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html](http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html)

It's MUCH easier than struggling with WImdows based dashboards, honest!

---

### Post by Tripwire32 on 2010-09-13
> **markbol said:**
> Hi guys I'm a complete newbie to linux i,m running ubuntu 10.04 and i cant connect with 3g modem.I've tried with vodafone and 3 ireland.THE SOFTWARE ICON IS ON SCREEN WITH BOTH MODEMS but when i try to run they cant find autorun files is there a comand to run these files their in media/3connect/autorun.exe.do i need permissions or something ?bear in mind im a complete novice at this any advice would be very much appreciated, mark

Please try restarting after connecting 3g stick and running network connections wizard/setup. I had a similar problem using my phone as modem and with a 3g USB stick (thought I had settings wrong). Restarting did the trick on both occasions. I'd suggest trying this 1st before getting into more complicated solutions.

---

### Post by desnaike on 2010-09-13
You need to install usb-modeswitch from synaptic, Do a google search for it and read up on it then install.


Good luck

---

### Post by jarviser on 2010-09-13
Some modems need modeswitch,and some don't.  I have used E160x and  k3570-z and they both worked without it. If the device appears in the mobile connection setup dropdown, they don't need it.

---

### Post by pricetech on 2010-09-13
> **rsawoseyin said:**
> Ubuntu needs to make such a thing extremely simple.

Another way to look at it is that vendors need to support Linux.  It's not the fault of the creators of Ubuntu, or any other distro, that vendors are lazy with support.

---

