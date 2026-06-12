---
title: "Nova-T 500 not detected (and no its NOT the reversion!)"
date: 2008-05-17
forum: Mythbuntu
---

### Post by Belistner on 2008-05-17
Hi,
I recently purchased a Hauppauge Nova-T 500 and installed the latest version of Mythbuntu. The card is v287 V2.0UK which according to the Mythbuntu Wiki and the LinuxTV wiki is supported. (It is NOT the Nova TD 500 reversion model - which I understand doesn't work.)

The problem is the card is not detected even though I have the drivers and the firmware. I had read this card was auto detected but just in case I followed this [http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) and installed the latest drivers. I also got a copy of the newest firmware linked to by the MythBuntu wiki.

But still nothing. /dev/dvb doesn't exist. MyTVBackend can't detect it. As far as I can tell the card isn't being detected at all. The only thing I can see is that lsusb mentions Hauppauge.

Can anyone offer ANY help? Please!

thanks
Lewis

---

### Post by Nikas on 2008-05-17
Post the output from "dmesg | grep -i dvb".

The old drivers looks for the old .fw-file but you should have the right drivers when using MythBuntu 8.04.

---

### Post by Belistner on 2008-05-17
Hi, thanks for the reply.

"dmesg | grep -i dvb" give no output. Whatsoever.

I know the card is plugged in and working because the system dual boots windows and its working fine with that.

I just don't understand why Mythbuntu isn't detecting it.I've posted the output of some commands below in case they help.

uname -a gives this
```

Linux lewis-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```



lspci gives this:

```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 2040:9951 Hauppauge 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 148f:2671 Ralink Technology, Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0471:0815 Philips 
Bus 001 Device 001: ID 0000:0000  

```

And just for good measure lspci gives this:

> 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)


thanks for ANY help!
Lewis

---

### Post by Nikas on 2008-05-17
Try to install the latest v4l-dvb-drivers

```
cd /usr/src/
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make
make install
```

---

### Post by Nikas on 2008-05-17
Try to install the latest v4l-dvb-drivers

```
cd /usr/src/
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make
make install
```

You may have to install the linux sources first.

---

### Post by Belistner on 2008-05-17
Hi, thanks again for the reply.

I've already tried that. Installed them.

Rebooted and still nothing...

Very strange. Any more ideas? Or am I back to Windows XP Media Centre? :-(

---

### Post by Beebock on 2008-05-17
> **Belistner said:**
> Hi, thanks again for the reply.

I've already tried that. Installed them.

Rebooted and still nothing...

Very strange. Any more ideas? Or am I back to Windows XP Media Centre? :-(

Hi,

Follow this, it worked for me

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Regards
Richard

---

### Post by GordonEndersby on 2008-05-18
From you DMESG it looks like you only have USB 1
Dont you need USB2 for the Nova T 500.

The Nova T 500 appear to the system as usb devices and im pretty sure it would need usb2.

Gordon

---

### Post by Nikas on 2008-05-18
The Nova T-500 has a built in controller (VIA) for USB.
Just like a PCI-card with usb-ports but in the Nova T-500-case the ports are directly connected to the tuners.

So, you dont need any usb-ports at all. The card adds the usb-ports needed.

I dont have any problems with my two T-500 and MythBuntu 8.04.

Check your card. Look for the VIA-chip on the board. If you don't have it you have the strange revision (uses DiB0710 for USB). The diversity version has two aerial connectors too.
Don't mind the box... [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)
"This card appears to have been released, in low volumes, only in the UK, but unfortunately it seems that Hauppauge is shipping the Diversity* card in regular NOVA-T-500 boxes!"

But that depends on where you bought your card. :)

---

### Post by Belistner on 2008-05-18
> **Nikas said:**
> 
Check your card. Look for the VIA-chip on the board. If you don't have it you have the strange revision (uses DiB0710 for USB). The diversity version has two aerial connectors too.
Don't mind the box... [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)
"This card appears to have been released, in low volumes, only in the UK, but unfortunately it seems that Hauppauge is shipping the Diversity* card in regular NOVA-T-500 boxes!"

But that depends on where you bought your card. :)

Hi,
I bought my card from PC world in the UK. But I had read that article before hand and was careful NOT to buy the reversion. 

It has one Ariel socket, and is the right version. No diversity stickers on the box. The code on the chip on the board itself was the Nova T 500 and not the Nova TD 500 (which is what the reversion has).

Therefore I'm 99.9999% sure it is not the reversion. :-)
According to that article anyway.

EDIT: I just opened it up to have a look. The board **does** have the VIA Chip.

Lewis

---

### Post by Belistner on 2008-05-18
> **Beebock said:**
> Hi,

Follow this, it worked for me

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Regards
Richard

Thanks for the link.

It contains mostly stuff I have already tried but there are a few commands I haven't run.

Will try it later today.

Lewis

---

### Post by Beebock on 2008-05-18
> **Belistner said:**
> Thanks for the link.

It contains mostly stuff I have already tried but there are a few commands I haven't run.

Will try it later today.

Lewis

I had tried many things before blundering onto that post.

Just start from the top and work your through. Where it says reboot, power off, count to 10 and power on again. The part about the 'warm state' proved true on my system, and the power off fixed it all

Regards
Richard

---

### Post by Belistner on 2008-05-18
> **Beebock said:**
> I had tried many things before blundering onto that post.

Just start from the top and work your through. Where it says reboot, power off, count to 10 and power on again. The part about the 'warm state' proved true on my system, and the power off fixed it all

Regards
Richard

HEY! Beebock that was awsome advice. Cheers for that. Just to test it I turned off my system for a few mins and turned it back on and it was detected!!!

Unfortunately it still doesn't work properly. I click watch TV and it flickers but does nothing. Despite me setting it up in Backend setup.

But at least I now have something to work with. If its detected I at least stand a chance of fixing it now!

Lewis

---

### Post by Beebock on 2008-05-19
> **Belistner said:**
> HEY! Beebock that was awsome advice. Cheers for that. Just to test it I turned off my system for a few mins and turned it back on and it was detected!!!

Unfortunately it still doesn't work properly. I click watch TV and it flickers but does nothing. Despite me setting it up in Backend setup.

But at least I now have something to work with. If its detected I at least stand a chance of fixing it now!

Lewis

No Worries.

Now that you have it going (detected) you will need to set it up (you probably already have) and scan for the channels.

Now here is something that I figured out at the cost of a lot of time and hair. If you are splitting the arial, digital signals do not like this.

Get a direct feed from the arial to the card, scan things and get a picture and only then slip the signal to the rest of your TV equipment. I have found that the signal DB halves everytime you split it. If you are in the 30db to start with, the signal is too low to do anyhing. (ie 2 devices running)

There is somewhere in there that you can look at the signal strength, ensure that these are high enough. Digital is nowhere near as forgiving as the old analogues. I found myself on a long ladder putting the arial outside to get a good signal. Admittably I'm running at 36DB after a split :D:guitar:

Richard

---

