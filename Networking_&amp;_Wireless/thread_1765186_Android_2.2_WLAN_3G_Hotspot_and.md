---
title: "Android 2.2 WLAN 3G Hotspot and"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by saberoth on 2011-05-22
Hello,

I'm having the issue that I cannot conenct to the wlan of my Motorola Milestone/Droid with Android 2.2 and the 3G Hotspot service started.
When I want to connect, I have to type the WPA2 passhrase in, I do that correctly and then the system tries to conenct. This failed and then I have to type the passphrase again.
It's a Samsung N130 Netbook with Ubuntu 11.04 installed.

lshw -C net tells me that:
```
  *-network      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:5a:73:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff

```

And dmesg that:

```
[  145.335425] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 1/3)
[  145.532168] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 2/3)
[  145.732132] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 3/3)
[  145.932213] wlan0: direct probe to a4:ed:4e:25:51:f6 timed out

```

This comes up again and again...

syslog in etc/log/ tells that:

```
May 22 23:33:47 markus-N130 wpa_supplicant[506]: Authentication with a4:ed:4e:25:51:f6 timed out.
May 22 23:33:47 markus-N130 NetworkManager[465]: <info> (wlan0): supplicant connection state:  associating -> disconnected
May 22 23:33:47 markus-N130 NetworkManager[465]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
May 22 23:33:48 markus-N130 wpa_supplicant[506]: Trying to associate with a4:ed:4e:25:51:f6 (SSID='Nexus' freq=2462 MHz)
May 22 23:33:48 markus-N130 NetworkManager[465]: <info> (wlan0): supplicant connection state:  scanning -> associating
May 22 23:33:48 markus-N130 kernel: [  123.243348] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 1/3)
May 22 23:33:48 markus-N130 kernel: [  123.440064] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 2/3)
May 22 23:33:49 markus-N130 kernel: [  123.640200] wlan0: direct probe to a4:ed:4e:25:51:f6 (try 3/3)
May 22 23:33:49 markus-N130 kernel: [  123.840142] wlan0: direct probe to a4:ed:4e:25:51:f6 timed out
```

So, how to solve this issue? Connection to another wlan, like to my access point, works.
Thanks for helping!

---

### Post by Martin_sensei on 2011-05-25
Same here.

I could connect with 10.10, but after the upgrade to 11.04 it stopped connecting.

I can, interestingly, connect to my friend's Android Hotspot on his HTC Desire.

I have posted many times about this with no joy so far.

---

### Post by saberoth on 2011-05-25
I tried to connect to my phone with MeeGo OS, also timed out by associating the Wlan. Dunno what to do to get it working.
It's really annoying why Linux couldn't connect to the Android Hotspot.
Well, I think it's a problem with Droid. Friends told me they are able to connect to their smartphone with hotspot, like with HTC and Samsung. Has Motorla failed with another feature?

Would be really great if there will be a workaround for this, i don't want to root my phone :(

---

### Post by Martin_sensei on 2011-05-26
Hi I am beginning to think this is a problem with Motorola software/hardware.  I have tried connecting to numerous friends Android hotspot with my Ubuntu 11.04 laptop, HTCs work, Samsung Galaxy S works, Motorola milestone does not.

However Ubuntu 10.10 works with everything.

---

### Post by saberoth on 2011-05-27
Yep, I think this, too. I think the iptabels are missing in the Milestone/Droid kernel. Seems I have to replace the kernel with one which supports iptabels.

---

### Post by sol.const on 2011-06-01
Had the same problem with Asus EeePC 901 + HTC Legend Hotspot.
Manual installing latest driver as described here :[http://ubuntuforums.org/showthread.php?t=1476007]("http://ubuntuforums.org/showthread.php?t=1476007") solved the problem.

---

### Post by Martin_sensei on 2011-06-03
> **sol.const said:**
> Had the same problem with Asus EeePC 901 + HTC Legend Hotspot.
Manual installing latest driver as described here :[http://ubuntuforums.org/showthread.php?t=1476007]("http://ubuntuforums.org/showthread.php?t=1476007") solved the problem.

That doesn't look like the same problem.  My laptop can conect to many hotspots, wifi is generally working, just not with motorola hotspots.

---

### Post by cabez0n on 2011-06-03
Same thing happening here.
I use to be able to connect when using ubuntu 10.10 and after upgrading to 11.04, the connection started to failed. 

I can still connect from a windows pc so I guess the problem is not on the motorola milestone but on the newer ubuntu. 

Anybody has any clues about this ?

---

### Post by Martin_sensei on 2011-06-06
> **saberoth said:**
> Yep, I think this, too. I think the iptabels are missing in the Milestone/Droid kernel. Seems I have to replace the kernel with one which supports iptabels.

Did you try this?  Any success?

---

### Post by Martin_sensei on 2011-06-15
Any ideas out there?

---

### Post by fabianmartins on 2011-06-27
I´m with the same ... exactly the same messages!!

Unfortunately Windows 7 connects properly.


It is this kind of issue that still makes ordinary people stay away from Linux.

I hope it gets solved soon.. because 10.04 was working properly.

---

### Post by cjpetrie on 2011-06-28
Same here - I didn't see this thread and had posted [http://ubuntuforums.org/showthread.php?p=10984909#post10984909](http://ubuntuforums.org/showthread.php?p=10984909#post10984909)

Of course neither the handset nor the cell provider will deal with this. Probably a subtle error that will take extensive Ubuntu, 802.11, and telecom expertise to solve. Meanwhile, my major Internet connection is off the air. Time to root.

---

### Post by cjpetrie on 2011-06-30
This seems to be a HUGE problem with 11.04. There is another thread about "tethering" no longer working in this release too. "Ubuntu 11.04 tethering problem".   I can't believe no one is publishing a fix to such a big problem. I was going to get around the WiFi problem by rooting and tethering, but it seems that doesn't work either.

---

### Post by fabianmartins on 2011-07-12
Friends, after reading a lot I found a solution
 
Taking a look at lspci output (command is "sudo lspic -v") I´ve realised that my wireless board is a Ralink corp RT3090. The details indicate:
 
Kernel driver in use: rt2800pci
Kernel modules: rt2860sta, rt2800pci
 
So I´d read in some posts that rt2800pci is unstable under 11.04, but rt2860sta is not.
 
To solve it, I´ve edited /etc/modprobe.d/blacklist.conf and inserted the following line:
blacklist rt2800pci
 
When restarting the service (or the computer) Ubuntu 11.04 imediately got connected to Motorola Milestone 2 hotspot service. Solved!
 
So, probably most of you may have the same problem:
1) Check your wireless card (embedded or not)
2) Check installed and working drivers (kernel modules)
3) Try to blacklist some, leaving just one working
4) If nothing of this works, try to get a driver from vendor site.
 
That´s it. Hope it help you all.

---

### Post by Martin_sensei on 2011-07-19
Hello,

I tried updating the ath9k driver on my machine to the [compat-wireless 3.0 stable release]("http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.0_stable_releases") as this looked like the very latest stable driver for ath9k on Ubuntu 11.04.

Unfortunatley I still could not connect to the motorola (but can connect to anything else) :-(

I have a year left of my mobile phone contract, I really want to get this sorted.  So, do we think I went to the right place to install the latest drivers for my wireless interface?  Any other ideas out there?

---

### Post by Martin_sensei on 2011-07-21
any ideas?

---

### Post by ehaley on 2011-07-21
the only way I can connect is through easytether using USB which stinks I would like to let people know to try 11.04 from the disk before install as it will not work with tethering as 10.10 does best thing I know is to stay at 10.10 if you want to wireless tether

---

### Post by scottb181249 on 2011-07-21
Hi All

I am a newbie but have a HTC Legend with a Samsung N125P netbook. The WiFi Hotspot in the HTC Legend works with Windows 7 and did work with the previous version of Ubuntu - something has happened since then to change things.

I really like Ubuntu but this is becoming a serious problem as I use this phone when I am roaming (quite a lot) and I do not want to have to use W7 all the time.

This has been an issue for some time in the forums but I am sorry to say that it appears that, it looks like, unless a moderator or serious Ubuntu buff has the problem, it remains unsolved.

ScottB

---

### Post by ehaley on 2011-07-21
the only thing you can do is go back to older version of ubuntu or use easytether with usb which works but can't leave phone in a good spot for service and have to have wires hooked to laptop
this is not a hardware issue it is something wrong with 11.04 network manager as the one in 10.10 works great

---

### Post by ehaley on 2011-07-21
and the very bad part of easy tether usb connection is you will not get a phone call as you can with wireless tether

---

### Post by scottb181249 on 2011-07-21
Thanks for your commiserations - actually, it is Lubuntu I have installed and it is a superb distro for me - it just fits like a glove - it would be a real shame if I had to go back a version and then worry every time there was an update in case the same thing recurred.

Scottb

---

### Post by Rzulf on 2011-07-27
This is a kernel issue. If I choose kernel from 10.10 at startup i can easily connect with hotspot.

---

### Post by scottb181249 on 2011-08-02
How would I go about choosing the kernel from 10.10 at startup?

scottb

---

### Post by kveh on 2011-08-24
Hello people... I got the same problem here, with Motorola's hotspot...

When I try to connect, Ubuntu ask me the password, and I know thats this is right...

So, I saw that is possible to get back kernel 10.10 or 10.04, but I want to still using 11.04, what i need to do to work my hotspot??

Sorry about my english...

And thks =)

---

### Post by fragu81 on 2011-08-27
Same problem 
ath5k
10.04 ok
11.04 broken
waiting

Somebody???

---

### Post by leorodriguez on 2011-08-28
Hey Guys, Unfortunately I have the same problem with my Motorola Defy (Android 2.2) the hotspot connection works perfect in Windows 7, but in Natty it can´t connect.... anyone know how to solve???

---

### Post by metoor30 on 2011-08-30
Solved my problem by:

clicking network manager icon
edit connections
wireless tab
select my wifi network
click edit
click IPv4 tab
select "Automatic (DHCP) address only"
Enter DNS server

Not sure why this worked.

Another observation.  I have an HP and a dell laptop (can provide more info if you need it).  The HP was 10.10 and upgraded to 11.04.  The Dell was installed with 11.04.  The Dell didn't connect to my android wifi but my HP does.

---

### Post by kveh on 2011-08-30
> **metoor30 said:**
> Solved my problem by:

clicking network manager icon
edit connections
wireless tab
select my wifi network
click edit
click IPv4 tab
select "Automatic (DHCP) address only"
Enter DNS server

Not sure why this worked.

Another observation.  I have an HP and a dell laptop (can provide more info if you need it).  The HP was 10.10 and upgraded to 11.04.  The Dell was installed with 11.04.  The Dell didn't connect to my android wifi but my HP does.

I did it, and not works...

I'm using Motorola Defy 2.2...

---

### Post by metoor30 on 2011-08-31
> **kveh said:**
> I did it, and not works...

I'm using Motorola Defy 2.2...

I am using kernel 2.6.38-8-generic.  I tried with 2.6.38-11-generic and it wasn't working.  Boot into 2.6.38-8-generic and see if it works there.  (with the fix I previously mentioned)

---

### Post by kveh on 2011-09-01
> **metoor30 said:**
> I am using kernel 2.6.38-8-generic.  I tried with 2.6.38-11-generic and it wasn't working.  Boot into 2.6.38-8-generic and see if it works there.  (with the fix I previously mentioned)

Ok, I Tried to search the kernel 38-8, but I don't founded it...

What I need to do to use a old kernel? Because I don't have it on my grub... 

Thanks =)

---

### Post by metoor30 on 2011-09-01
> **kveh said:**
> Ok, I Tried to search the kernel 38-8, but I don't founded it...

What I need to do to use a old kernel? Because I don't have it on my grub... 

Thanks =)

You should be able to install the older kernel with 

```
sudo apt-get install linux-image-2.6.38-8-generic
```


You can test this without reconfiguring grub.  After the install just reboot and hold down shift to get the grub menu.

---

