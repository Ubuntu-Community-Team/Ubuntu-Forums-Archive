---
title: "Broadcom 4318 works with Puppy 4.1.1, why not in Ubuntu?"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by dmber on 2008-12-19
My father-in-law gave me his old Gateway MX6121, with a Broadcom 4318 wifi card in it.  The card works just fine with Puppy Linux 4.1.1, but not with Ubuntu.  Why is that?  Couldn't I just take whatever's working for Puppy and get it going in Ubuntu?

Obviously, I'm a noob, so I'm more looking to get more knowledge about how Linux works.  Don't read this post as a whiny "Why won't this work??", rather I'm genuinely curious as to why it would work in one Linux Distro, and not another.  (Of course, I'd like to get it working in Ubuntu, as Puppy Linux is fast, but not to my taste).

Kernel is 2.6.25.16 (i686) if that helps.  I've attached a screenshot of the Wifi Driver.  

Thanks.

[[IMG]http://img201.imageshack.us/img201/5194/b43driverer7.th.png[/IMG]](http://img201.imageshack.us/my.php?image=b43driverer7.png)

---

### Post by xjcannonx on 2008-12-19
well i guess a first step would be to post the output of: ```
lspci
sudo iwlist scanning
```
And what version of ubuntu are you running?

I think your 4318 has a restricted driver you can enable in System-->Administration-->Hardware Drivers

---

### Post by dmber on 2008-12-19
> **xjcannonx said:**
> well i guess a first step would be to post the output of: ```
lspci
sudo iwlist scanning
```
And what version of ubuntu are you running?

I think your 4318 has a restricted driver you can enable in System-->Administration-->Hardware Drivers
I'll have to get back to you once I install Ubuntu.  I should have been more clear in my first post, sorry.  I had borrowed this same laptop about a month ago while my Eee PC was getting fixed.  I put Hardy on it and the Wifi didn't work.  When I gave it back to my father-in-law, he put Puppy back on it, and just tonight he said I could have it for keeps.  So I still have Puppy on it.

I'll probably throw Intrepid on here tomorrow and post the results of you code then.

Thanks!

---

### Post by Ayuthia on 2008-12-19
Is Puppy using 2.6.25.16 also?  My guess it is because of the changes in the kernel module.  I was thinking that the 4318 did not do too well until Intrepid.  You might try the depreciated driver (bcm43xx) and see if it works better.

Is this a custom kernel?  For some reason I was thinking that the last few kernels in Ubuntu have been in the even numbers not 2.6.25.

Also, are you using the right firmware?  The firmware for the b43 driver changes between 2.6.24 and 2.6.25.  You might check dmesg to verify:
```
dmesg|grep b43
```

---

### Post by Ayuthia on 2008-12-19
> **dmber said:**
> I'll have to get back to you once I install Ubuntu.  I should have been more clear in my first post, sorry.  I had borrowed this same laptop about a month ago while my Eee PC was getting fixed.  I put Hardy on it and the Wifi didn't work.  When I gave it back to my father-in-law, he put Puppy back on it, and just tonight he said I could have it for keeps.  So I still have Puppy on it.

I'll probably throw Intrepid on here tomorrow and post the results of you code then.

Thanks!

If you check lspci and see if it is a 4318 rev 02, it should work fine in Intrepid.  This card seems to be working much better in this version than in Hardy.

---

### Post by spcwingo on 2008-12-19
The reason it works in Puppy is because Puppy includes many proprietary drivers by default.  Ubuntu doesn't.

---

### Post by dmber on 2008-12-20
Thanks.  So that leads to my next question: is there any way to "extract" the driver from Puppy and use it in Ubuntu?

---

### Post by dmber on 2008-12-20
> **Ayuthia said:**
> Is Puppy using 2.6.25.16 also?  My guess it is because of the changes in the kernel module.  I was thinking that the 4318 did not do too well until Intrepid.  You might try the depreciated driver (bcm43xx) and see if it works better.

Is this a custom kernel?  For some reason I was thinking that the last few kernels in Ubuntu have been in the even numbers not 2.6.25.

Also, are you using the right firmware?  The firmware for the b43 driver changes between 2.6.24 and 2.6.25.  You might check dmesg to verify:
```
dmesg|grep b43
```
The Kernel I listed is the one I'm using with Puppy.  Sorry about the confusing first post.  I should have been more specific.  I've got Intrepid downloaded and I'm going to try to install it now and see if it works.

---

### Post by joustin on 2008-12-20
I just got my 4318 working three days ago on Xubuntu 8.0.4. There is nothing hard to it really, the b43fwcutter is a pain IMO,I used the Windows drivers and ndiswrapper, took about 5 mins and it was working well. I get 54mb's max connection with an average throughput of about 20, that is about what my laptop got under Windows. I never liked the idea of using ndiswrapper but it worked so well lol :P

---

### Post by Ayuthia on 2008-12-20
> **dmber said:**
> Thanks.  So that leads to my next question: is there any way to "extract" the driver from Puppy and use it in Ubuntu?

You shouldn't try to copy the driver over because it is dependent on the kernel.  However, you can copy the firmware over.  You will need to copy over /lib/firmware/b43 over to Ubuntu.  Just make sure that if you do this, you will need to make sure that Ubuntu that you are using is 2.6.25 or higher.  Otherwise you will run into a firmware incompatibility issue.

It won't guarantee that it will work in Ubuntu because Ubuntu does apply some patches to the b43 module which will might make it act differently.

---

### Post by dmber on 2008-12-20
> **xjcannonx said:**
> well i guess a first step would be to post the output of: ```
lspci
sudo iwlist scanning
```
And what version of ubuntu are you running?

I think your 4318 has a restricted driver you can enable in System-->Administration-->Hardware Drivers
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
```

and 

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

I am up and going on Intrepid.  The ethernet works fine (I'm posting from the Gateway MX6121).

---

### Post by dmber on 2008-12-20
> **Ayuthia said:**
> Is Puppy using 2.6.25.16 also?  My guess it is because of the changes in the kernel module.  I was thinking that the 4318 did not do too well until Intrepid.  You might try the depreciated driver (bcm43xx) and see if it works better.

Is this a custom kernel?  For some reason I was thinking that the last few kernels in Ubuntu have been in the even numbers not 2.6.25.

Also, are you using the right firmware?  The firmware for the b43 driver changes between 2.6.24 and 2.6.25.  You might check dmesg to verify:
```
dmesg|grep b43
```

```
$ dmesg|grep b43
[    3.778030] b43-pci-bridge 0000:06:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.504086] b43-phy0: Broadcom 4318 WLAN found
[   31.848698] input: b43-phy0 as /devices/virtual/input/input10
[   31.932068] firmware: requesting b43/ucode5.fw
[   31.968871] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   31.968885] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   32.040524] input: b43-phy0 as /devices/virtual/input/input11
[   32.104055] firmware: requesting b43/ucode5.fw
[   32.107725] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   32.107737] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  133.592414] b43-phy1: Broadcom 4318 WLAN found
[  137.753972] input: b43-phy1 as /devices/virtual/input/input12
[  137.840071] firmware: requesting b43/ucode5.fw
[  137.845081] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  137.845097] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  137.900171] input: b43-phy1 as /devices/virtual/input/input13
[  137.968051] firmware: requesting b43/ucode5.fw
[  137.971480] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  137.971494] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).

```

---

### Post by dmber on 2008-12-20
Well...it's working!

I followed the link that the Terminal spit out to me : [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

and it worked!

I'm pumped!  Thanks for the help!

---

### Post by dmber on 2008-12-29
well...it was working.  Now, it takes up to 5 restarts to get the wireless to "engage."  Usually Ubuntu starts up, but does not offer any choice of wireless networks.

Any ideas?
Thanks.

---

