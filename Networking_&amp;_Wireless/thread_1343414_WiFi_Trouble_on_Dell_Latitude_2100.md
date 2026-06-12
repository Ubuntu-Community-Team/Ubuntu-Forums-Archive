---
title: "WiFi Trouble on Dell Latitude 2100"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by elmoisk00l on 2009-12-01
[U][B]DOUBLE EDIT: I had the problem again and found this topic: [http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906). 
EDIT: Fixed my problem not sure how, just restarted and ran hardware drivers a couple of times...Try Googling Broadcom STA wireless driver if you are in the same situation as I was.[/B][/U]
_**Thanks to all that helped me.**_ 
I had gotten a virus on my school issued netbook (Windows) and decided instead of having them re-image it for me I would just put Ubuntu on it fully. (Had had it dual-booting) So I used a Live USB and reformatted over the entire drive. Now, I cannot use the Fn+F6 combination to turn on the WiFi card. (LSPCI output: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)) It had worked when I had it dual booting... Any suggestions on how to get the Wireless card to come on? I am currently using an Ethernet cable to post this. It seems to not be recognizing it. 
**It had worked in the past so I know that it is compatible, to a degree.**
Various Stats:
Dell Latitude 2100 Netbook
**Dell 1510 wireless card**
2 GB ram
16 GB SSD
 
As soon as I get WiFi working I will be a very happy person :smile:
 
(Sorry for the lack of organisation, this thread is just a re-worded post.)

---

### Post by RedSingularity on 2009-12-01
Why cant you use the Key combo?  It wont work?

---

### Post by elmoisk00l on 2009-12-01
The physical light surely works, it lights up on start-up. The keys them self work, I test them both. They should both also work in combination, the problem is the that some were Ubuntu must not put together, Fn+F6 = Turn on Wireless card. Like I said it worked before (an hour ago) and doesn't work now. Hardware Drivers does not detect anything. 

I will be eating dinner soon. Be back

---

### Post by RedSingularity on 2009-12-01
If the light is turning on it seems that the card is on.  Pressing the key combo should turn the light on and off.  Does it do this?

Also try the combo and then restart the computer.

---

### Post by elmoisk00l on 2009-12-01
> **RedSingularity said:**
> If the light is turning on it seems that the card is on.  Pressing the key combo should turn the light on and off.  Does it do this?

Also try the combo and then restart the computer.

Ok. I will the light is not on continuously it only flashes on at start up.

---

### Post by elmoisk00l on 2009-12-01
Restarted, had no effect. Fn+F6 has no effect. Light is still off.

---

### Post by RedSingularity on 2009-12-01
So it was working a little while ago?  Did you do any system updates before it broke?

---

### Post by RedSingularity on 2009-12-01
Post your output of ifconfig

---

### Post by elmoisk00l on 2009-12-01
> ryan@ryan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:f7:68:63  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fef7:6863/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17509399 (17.5 MB)  TX bytes:1693122 (1.6 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
Other logs that might be helpful (don't know how helpful)

LSPCI command
> [SIZE=1]ryan@ryan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)[/SIZE]


---

### Post by RedSingularity on 2009-12-01
It seems like there is no wireless interface turned on.  You should have a wlan0 in the output of ifconfig.  The computer detects it (lspci says so) but there is no wlan setup which happens if it is off.  There has to be a way to turn it back on..........

---

### Post by teward on 2009-12-01
> **RedSingularity said:**
> It seems like there is no wireless interface turned on. You should have a wlan0 in the output of ifconfig. The computer detects it (lspci says so) but there is no wlan setup which happens if it is off. There has to be a way to turn it back on..........

This is assuming the drivers exist.  I know of many problems with Broadcom cards and Ubuntu Linux.  I also searched up your card.  Its driver is a restricted driver, so I'm not sure where you'll be able to get the drivers.

---

### Post by elmoisk00l on 2009-12-01
> **TrekCaptainUSA said:**
> This is assuming the drivers exist.  I know of many problems with Broadcom cards and Ubuntu Linux.  I also searched up your card.  Its driver is a restricted driver, so I'm not sure where you'll be able to get the drivers.

The drivers, I would assume, exist. As I stated earlier, I was able to get it to run when dual-booting with XP. I was able to to install it via the **hardware drivers.** Does that rule out the need for NDISwrapper?

---

### Post by elmoisk00l on 2009-12-01
Oh wow.. just a moment.. I think I got this puppy workin..

I opened up hardware drivers, and NOW it shows:
Broadcom B43 wireless driver (free)
and 
Broadcom STA wireless driver (proprietary)

Which one should I select?

---

### Post by RedSingularity on 2009-12-01
Proprietary probably has better quality.

---

### Post by elmoisk00l on 2009-12-01
Fixed it. I'm not sure how I got it to work... Best bet for this situation with my card... search Google for "Broadcom STA wireless driver".

---

