---
title: "display garbled, video card is the problem, but so confused ....."
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by rajan on 2007-10-10
my screen starts getting garbled as soon as i start the computer. even the bios messages are garbled but i can't figure out how to start to piece together a solution. there's a screenshot of my system after startup and as you can see, it's still useable, but definitely not optimal. 

even weirder is the fact that a few boots ago, the garbling started only after the system was mostly started up and the current boot actually had the problem at startup but now my screen looks perfectly fine.

i switched to linux because i could diagnose problems like this and actually fix them so please don't suggest i reinstall or upgrade. 

problems that i've eliminated:
1. the monitor works when i plug it into the wife's laptop (and also right now on my linux box).

2. the video card has no noticeable surface defects.



nothing has been changed recently, except that i have just started playing freeciv and tuxracer. i can't imagine that video games would cause this problem when they're not running, but that seems to be the only plausible source of the problem.

```

rajan@paravati:~$ lspci
...
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
rajan@paravati:~$


```

```

rajan@paravati:~$ cat /etc/X11/xorg.conf

....

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

....


```

big TIA to anyone with any possible solution.

---

### Post by CRCarl on 2007-10-11
If the BIOS startup screen does not look right the problem is not with your OS. I would upgrade the firmware on the video card and check all the cables and connectors. 

Craig

---

### Post by rajan on 2007-10-11
yeah it's definitely not the OS. i think the video card is the problem. here's some weird occurences:

-- if i touch the end of the speaker cable to the video card (on the outside, right next to where you plug in the monitor cable) it will mess up the graphics.
-- scrolling with either the mouse middle wheel or the arrow keys on web pages sometimes make the problem much worse.
-- the only time it has worked very well since the problem arose was when i completely detached every cable from the computer box and then reattached them. 
-- fan on the video card spins fine, nothing wrong there.

it looks like i'll be going out and buying another video card soon. 

can someone help me with how to pick out a video card that will fit my motherboard? i know there's some distinctions that will prevent me from using just any video card, right?

---

### Post by nzadLithium on 2007-10-11
And i think you should check if the graphics card needs its own power source if it does then check its plugged in properly and that there is no damage to the connectors.

I had a similar problem with my x1300 when i didnt plug the power in :p cept mine was alot worse it was a complete mess, colours screwed up so bad i couldn't see anything at all :S

If you still need a new card can you post your motherboard model? And i would recommend with going for a nvidia card because ati drivers aren't that great with the newer cards. (x and HD series cards)

---

### Post by rajan on 2007-10-12
it looks like i have the MSI 6712.
here's my partial output from `lshw` :

```


....

    description: Desktop Computer
    product: MS-6712
    vendor: MSI
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: MS-6712
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: Version 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect  socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 i nt5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipbo ot biosbootspecification

.....


```


the plugging in the cable worked actually the first time i tried it and i couldn't get the system to malfunction no matter how hard i tried, but then a few reboots did the trick and now the background on my desktop is messed up. i am sure it is something like what you mentioned, but i can't think of a fix. i'm convinced that it's a hardware problem so i'm gonna skip it and grab a new card. so now i just need to know where i should look for information on compatibility with the MSI 6712. anyone have a hint?


EDIT:
just found this-
"all video cards are compatible with all motherboards unless the motherboard has the wrong type of pci-e slot...." on yahoo answers. is this correct?

---

### Post by nzadLithium on 2007-10-12
I cant find anything on a motherboard with that model number.
but from ur lshw ubuntu says it has an agp slot which i think is likely since you had a 9800 card before. So you can go with any card that says agp. Don't touch anything that says pci-e because it won't work in your motherboard.

As i said before i recommend a nvidia card because ati doesnt have any decent drivers yet.

So in summary NVIDIA using AGP

Just pick a card thats in your price range and that will do what you want it to do. :)

---

### Post by nzadLithium on 2007-10-12
oh and about that edit you posted even though it wont help you 

yes as long as you have a pci-e 16x slot i think it is then you will be able to use any pci-e graphics card (with the right drivers).

But its the same with agp which ubuntu reports you have. As long as you have an agp 8x slot (which im pretty sure you do) any card that says agp will go on your pc

---

### Post by rajan on 2007-10-12
awesome ... thanks a lot!


EDIT: replaced the video card and everything's coming up milhouse! a $10 agp RIVA TNT2 card from ebay did the trick. Thanks again guys.

---

