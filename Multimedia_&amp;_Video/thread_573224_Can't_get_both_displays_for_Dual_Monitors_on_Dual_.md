---
title: "Can't get both displays for Dual Monitors on Dual Video Cards on Dell Dimension 3100"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by FishFoot on 2007-10-11
Hi Guys,

I'm trying to configure a Dimension 3100 with its onboard video card, an Intel 82915G/GV/910GL Express,  and an ATI X1300 PCI card.

I can get each card to work individually and I've got both listed in the xorg.conf file, but I can't get them to work at the same time.  If I go into the BIOS I can choose to boot with the "On Board" or the "PCI" as the primary video card and whichever one I choose is the one that works when the system comes online.  

There are errors in the syslog that read:
```
gdm[5410]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
gdm[5537]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
gdm[5839]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```
regardless of which video card I boot with.

The ATI card is using the fglrx and the onboard is using the i810 driver.

When I run lspci I see:
```

00:02.0 Display controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
04:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
04:00.1 Display controller: ATI Technologies Inc Unknown device 71a3

```

I've used the first 2 entries listed there for the corresponding video cards in the xorg.conf.

I have a Dimension 3100 at work with 2 video cards that is running in windows and I had no trouble setting it up.  I had to set the bios to use the onboard as the primary.

I'd be glad to post my xorg.conf if that would help


Thanks
FishFoot

---

### Post by Masterj15 on 2007-10-11
wow, this is way out of my league but if your just trying to have split monitors then you should try a video spliter. I bought one for like 5 bucks at a concer computer store.

---

### Post by FishFoot on 2007-10-11
I appreciate the response but clearly I'm not looking for a Y splitter.  I'm looking to have a dual headed linux box, just like my windows.  Here I want to use 2 cards because I have them and I don't have to go out and purchase anything new.

---

