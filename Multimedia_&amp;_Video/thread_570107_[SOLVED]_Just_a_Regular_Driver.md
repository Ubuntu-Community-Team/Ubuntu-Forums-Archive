---
title: "[SOLVED] Just a Regular Driver"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by oneadvent on 2007-10-07
I would like to configure my video driver, or download one and then install it. I am not sure how to do this, would someone like to enlighten me?

My laptop is a Gateway 200ARC. I know no more. Let me know if I can provide something to help this out...

Thx in advance.

---

### Post by overdrank on 2007-10-09
> **oneadvent said:**
> I would like to configure my video driver, or download one and then install it. I am not sure how to do this, would someone like to enlighten me?

My laptop is a Gateway 200ARC. I know no more. Let me know if I can provide something to help this out...

Thx in advance.

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by oneadvent on 2007-10-09
Here ya go.

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
```

---

### Post by overdrank on 2007-10-09
> **oneadvent said:**
> Here ya go.

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
[COLOR="Red"]00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/COLOR]
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
```

Ok I have highlighted your graphics chipset and you may try the 915 resolution found here
[http://ubuntuforums.org/showthread.php?t=420185&highlight=intel+915+resolution](http://ubuntuforums.org/showthread.php?t=420185&highlight=intel+915+resolution)
Also you can verify in your xorg that you are using the i810 driver with this command
```
cat /etc/X11/xorg.conf

```
It will look something like this ```

Section "Device"
    Identifier     "nVidia Corporation NV28 [GeForce4 Ti 4800 SE]"
    Driver         "nvidia"
EndSection

```
But of course yours will say intel

---

### Post by oneadvent on 2007-10-09
I hate to be a complainer, however, now when I put it on 1280x1280 (which wasn't there before, so that is good) it restarts X. 

hum....we are getting closer. Do you have any idea on this?

Thanks.

---

### Post by overdrank on 2007-10-09
> **oneadvent said:**
> I hate to be a complainer, however, now when I put it on 1280x1280 (which wasn't there before, so that is good) it restarts X. 

hum....we are getting closer. Do you have any idea on this?

Thanks.

Hi and it might have something to do with the resource's like memory for the graphics. Some bios will let you change the amount of memory shared so you may look there. I run my laptop with the intel chipset at 1200x 800. Good luck!

---

### Post by oneadvent on 2007-10-09
Its not editable, but stuck at 8MB. Shouldn't that be enough?

Is there anything esle that I could try?

Thx for all your help so far.

Josh

---

### Post by oneadvent on 2007-10-09
OK, get this. I got it to do it, I don't know how, but it just worked. However now my screen is too...small. I have to scroll up and and down to see the whole screen...thats really weird...i better figure out how to revert. 

(It is doing the same thing going back...)

Josh

---

### Post by oneadvent on 2007-10-09
So how do i edit the resolution thing, so that it works? It crashes when I change it.

---

### Post by oneadvent on 2007-10-09
Ok, found another clue in my search to find a solution. If I log in as another user, (in this case, root...ya, ya don't blah blah blah,) It works fine. The resolution is perfect.

This has to be able to be fixed by changing a config flat file somewhere.

Thanks for being patient.

---

### Post by oneadvent on 2007-10-09
And it fixed itself.

Here is what I discovered:

xorg.conf was not changed in anyway, everything was already listed at 1024x786.

rc.local was not changed in anyway at all.

What I did was log in as root (uh, oh.) and then logged in as myself again, and everything was back to normal. I think I will take a break from this today.

Josh

---

