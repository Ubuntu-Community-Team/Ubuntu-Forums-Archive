---
title: "Wireless problem in acer aspire one mini laptop"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by skkmaths on 2012-07-26
I have installed ubuntu 12.04 in acer aspire one D270 laptop.  wi fi is not working , How to install the wi fi driver for ubuntu 12.04 for this laptop.  Please help me ....

---

### Post by kc1di on 2012-07-26
first thing you want to do is check the additional drivers tool 
go to system settings >hardware> additional Drivers.
See if it offers you any drivers for you machine.
if it does install and try that first.

if not 
please go to a terminal and type the following command and list the result here in this thread

```
lspci
```

l is a lower case L not # 1

---

### Post by skkmaths on 2012-07-26
00:00.0 Host bridge: Intel Corporation Device 0bf1 (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Device 0be1 (rev 09)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. Device 0032 (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)


I GOT THIS WHEN I TYPED THIS COMMAND ...

---

### Post by cortman on 2012-07-26
Do you also have trouble with the laptop freezing when you try to use wireless, or (if wireless is completely absent) when you boot up?
The Atheros drivers should have come with the kernel. Run

```
sudo modprobe ath9k
```

And see if it works upon reboot.

---

### Post by retchid on 2012-07-26
Try using mac puppy USB to see if that finds it [http://macpup.org/](http://macpup.org/)

Using macpuppy on acer one net book 
The wifi on the net book can be a bit awkward at times (stop for no reason then not work for a couple of boots) 

Or use a live USB of ubuntu to see if it find your wireless 

Then you will be in a position to know what the problem is if any

oddly enough on acer net book if you give it a slap on the bottom it will sort itself out (I am not joking - perhaps the manufacture process is not great) actually did that last night and not for the first time and it started working again - the driver is not the problem it just cannot find the device for some reason probably the connection?  Make sure it's turned off if you do give it a slap.

Maybe that will help more than trying to find a driver when it's not a driver problem.

---

### Post by teward on 2012-07-26
> **retchid said:**
> oddly enough on acer net book if you give it a slap on the bottom it will sort itself out (I am not joking - perhaps the manufacture process is not great) actually did that last night and not for the first time and it started working again - the driver is not the problem it just cannot find the device for some reason probably the connection? Make sure it's turned off if you do give it a slap.
 
The Atheros card does not necessarily have included Ubuntu drivers by default.  "Slapping the bottom" is not a recommended procedure, as you can potentially damage the other hardware components.
 
Before trying the "hit your computer" method that retchid stated, try making sure its not a drivers issue.  If you have to hit your computer to make it work, you'll need to start looking for another computer (hardware issues).

---

### Post by cortman on 2012-07-26
> **retchid said:**
> Try using mac puppy USB to see if that finds it [http://macpup.org/](http://macpup.org/)

Using macpuppy on acer one net book 
The wifi on the net book can be a bit awkward at times (stop for no reason then not work for a couple of boots) 

Or use a live USB of ubuntu to see if it find your wireless 

Then you will be in a position to know what the problem is if any



Maybe that will help more than trying to find a driver when it's not a driver problem.

Was this post meant to be a joke?

What is the user going to gain by using a LiveUSB of the same system he's currently running?
The solution is to fix Ubuntu, not install MacPup.

> **retchid said:**
> 
oddly enough on acer net book if you give it a slap on the bottom it will sort itself out (I am not joking - perhaps the manufacture process is not great) actually did that last night and not for the first time and it started working again - the driver is not the problem it just cannot find the device for some reason probably the connection?  Make sure it's turned off if you do give it a slap.

I'm not even sure how to react to this...
> **retchid said:**
> 
Maybe that will help more than trying to find a driver when it's not a driver problem.

I own an Acer Aspire One 722 netbook myself, and I assure you it's probably not a "slap the netbook" problem. :?

---

### Post by retchid on 2012-07-26
It works for me!

So cant really argue with it.

If I did not have an acer net book then I would probably agree that it was bull

---

