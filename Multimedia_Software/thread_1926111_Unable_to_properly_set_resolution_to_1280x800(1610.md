---
title: "Unable to properly set resolution to 1280x800(16:10)"
date: 2012-02-15
forum: Multimedia Software
---

### Post by Jukodan on 2012-02-15
When I attempt to set the resolution to 1280x800 the screen cuts off in the top left corner. I am using a 15" HD TV as my monitor and from the looks of it, lucid properly recognizes this. I was wondering if it had anything to do with the drivers. Google searches haven't really given me an answer to this as similar issues usually deal with Ubuntu not recognizing native resolution. Anyway, here is my lspci output, hope someone can point me in the right direction. 

```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)

```

---

### Post by winh8r on 2012-02-15
Check in System> Administration> Hardware Drivers and see if there are any proprietary drivers enabled on your system.

---

### Post by Jukodan on 2012-02-15
No proprietary drivers are currently in use by the system.

---

### Post by winh8r on 2012-02-15
Ok, can you please copy and paste the *-display section of the command 

```
lshw
```


I am guessing you are running a compaq presario as your lspci is identical to one of mine!

---

### Post by Jukodan on 2012-02-16
Here is the output and yes I am using a Compaq Presario :)

```
*-display UNCLAIMED
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:d8000000-dfffffff(prefetchable) ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff(prefetchable)

```

---

### Post by winh8r on 2012-02-16
Ok, I am running 10.04LTS so this should be very similar for you.

I did have issues with monitors when I first started using 10.04 I beleive this is the method I used to cure it.

```
sudo apt-get remove fglrx
```

then run

```
sudo apt-get install xserver-xorg-video-radeon
``` 

I couldn't enable desktop effects in compiz so i id this:

```
sudo gedit /etc/ld.so.conf.d/GL.conf
```

put this

```
/usr/lib
```

above the entry that is already there, but make sure there are still two lines in that file when you save it.

then issue this command

```
sudo ldconfig
```

this redoes the loader cache.

and just to finish off run

```
sudo apt-get update
```


your graphics should all work now with no bits missing around the edges of the screen or weird stuff at boot time.

I just could not seem to have any success with the fglrx drivers but if the xorg drivers do not work for you then you can reverse the process and remove the xorg driver and re-install fglrx.

You can of course install these drivers via the synaptic package manager if you prefer. 

Hope this is of some help in resolving the issue.

---

### Post by winh8r on 2012-02-16
On doing a little bit of digging it seems that sometimes there are clashes between computers and TV's being used as monitors.

Check this link and also the link from that page:


[http://ubuntuforums.org/showthread.php?t=1572268]("http://ubuntuforums.org/showthread.php?t=1572268")


I have always used monitors, both crt and lcd, so wonder if your issue is more specific to the use of the TV as a monitor?

---

### Post by Jukodan on 2012-02-16
I tried your suggestion and when I raise the resolution the screen still cuts off as the other user stated in the link you provided. I'm going to try the method provided in the other thread. Nonetheless, thanks again for pointing me in this direction. Fairly new to ubuntu and just want to have a nice display to work with :)

---

### Post by winh8r on 2012-02-16
Ok, no problem, like I said, the more I thought about it the more I thought it was likely to be an issue with the actual TV as  everything else is working fine and your graphics are stable.

Good luck with it .

---

