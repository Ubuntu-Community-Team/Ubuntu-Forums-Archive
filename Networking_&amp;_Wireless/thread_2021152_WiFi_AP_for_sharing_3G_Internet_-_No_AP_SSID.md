---
title: "WiFi AP for sharing 3G Internet - No AP SSID"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by Billycat99 on 2012-07-08
Hi Guys,

New Ubuntu user here and are liking it a lot. 

I have a problem that I was hoping someone might be able to help me out with.

Situation

I have installed 12.04 desktop i388 on my Toshiba laptop and managed to get it working with my 3G internet modem (E1762) all good.

However, I'm having trouble trying to create a WifI AP with the laptop to 'share' my 3G internet.

I have created a "New Wireless Network"  AP as follows:

SSID: ubuntu
Mode: ad-hoc
band: automatic 
IPv4: Shared to other computers
Security: 128 bit WEP

When I enable this WiFi AP, Ubuntu appears to create the network, however I can't find the Wifi Network when I search for it using my other WiFi devices. It is nowhere to be found.

Am I missing something?

TIA,

Mike

---

### Post by Billycat99 on 2012-07-11
Bump... Anyone?

---

### Post by Kirk Schnable on 2012-07-11
I wonder if your WiFi card doesn't support adhoc mode.

Do you know which wireless hardware you have installed?  If not, please paste us the output of this command:

```
lspci
```

Kirk

---

### Post by Billycat99 on 2012-07-12
Thanks ; )

Here is the output from lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
01:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 07)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04
```)

---

### Post by linux_falguni on 2012-07-12
Does your other device support adhoc networking? like many phones and tablets have no support of adhoc.

---

### Post by Kirk Schnable on 2012-07-12
> **linux_falguni said:**
> Does your other device support adhoc networking? like many phones and tablets have no support of adhoc.

That might be a good point.  I found another forum thread with a similar question, and they solved it by following a tutorial to make their Android phone recognize the network.

See: [http://ubuntuforums.org/showthread.php?t=1977556](http://ubuntuforums.org/showthread.php?t=1977556)

Do you have any other laptops you can test this Ad-Hoc hotspot with in the meantime?

Kirk

---

### Post by Billycat99 on 2012-07-13
My phone is an Android Google Nexus S. I'll follow the link and see if it contains anything that might help.

Mike

EDIT:Have checked out links and looks like it wants me to root the phone to install software patches... I don't want to do that so I guess my phone just cant connect to ADHOC networks.

Thanks for the help regardless.

---

### Post by Kirk Schnable on 2012-07-13
> **Billycat99 said:**
> My phone is an Android Google Nexus S. I'll follow the link and see if it contains anything that might help.

Mike

EDIT:Have checked out links and looks like it wants me to root the phone to install software patches... I don't want to do that so I guess my phone just cant connect to ADHOC networks.

Thanks for the help regardless.

I mentioned your problem to my coworker who owns an Android phone, and he looked at me like I was insane when I asked if his phone could connect to Ad-Hoc networks.  He's done it many times.

He has an HTC Thunderbolt.  What sort of phone do you have?  (Then again, I know his is rooted)

Kirk

---

### Post by hovrashko on 2012-07-13
try to see if you can do in via Win 7, i was able to do that on the iPhone. This way you will know if it possible at all.

---

### Post by Loranga on 2012-07-15
I have the same problem with the same scenario. I manage to get the 3G connection up and running, I create a wireless network with NetworkManager, but it cannot be found by my other computer.

My wlan card is an Atheros ar9285, does it support adhoc?

---

### Post by Kirk Schnable on 2012-07-15
> **Loranga said:**
> I have the same problem with the same scenario. I manage to get the 3G connection up and running, I create a wireless network with NetworkManager, but it cannot be found by my other computer.

My wlan card is an Atheros ar9285, does it support adhoc?

Here's an unsolved thread of someone else with the same question:
[http://ubuntuforums.org/showthread.php?t=2009112](http://ubuntuforums.org/showthread.php?t=2009112)

This guy looks like he's having some issues doing ad-hoc on your chipset:
[http://forums.whirlpool.net.au/archive/1377267](http://forums.whirlpool.net.au/archive/1377267)

Kirk

---

