---
title: "How do I get flash to work properly? (xorg.conf?)"
date: 2014-04-14
forum: Multimedia Software
---

### Post by pmonacular on 2014-04-14
Hola!  I am in the process of getting Lubuntu 13.10 up and running on a fairly ancient rig.  So far, so good, except, for the life of me I cannot get flash to work properly in either Firefox or Chromium.  It functions, but the video is compacted, and the colors are way off.  I have been looking for info on it for the better part of the afternoon.  I have downloaded and run the Intel Graphics installer for Linux, I have uninstalled/reinstalled flash several times, and still no dice.

So, the latest "fix" I have read about is switching from SNA to UXA, whatever that means, by adding a bit of code to a xorg.conf file.  My /etc/X11 folder does not have this file, and I cannot create one in PCManFM.  I'm sure this can easily be done in terminal, but I am a bit weary and leary at this point.  Would doing this fix my problem?  Or just create a new one?  Because when I was reading about xorg.conf, I read a post by someone saying that their Lubuntu failed to boot after creating that file.  

So basically, I would be tickled to know how to make a xorg.conf file IF it will work, or at least not mess anything else up.  Any other fixes/ideas on how to get flash to work right, beyond anything I've already mentioned is welcome also.  Thanks!

---

### Post by monkeybrain20122 on 2014-04-14
Try right click a flash video and disable hardware acceleration.

If that doesn't work please post the outputs of 
```
lshw -C display
```

---

### Post by mörgæs on 2014-04-14
I bet it's an Intel 8xx. 
The correct xorg.conf can be seen if you read the link in my signature. Another option is installing 14.04.

---

### Post by pmonacular on 2014-04-14
> **mörgæs said:**
> I bet it's an Intel 8xx. 
The correct xorg.conf can be seen if you read the link in my signature. Another option is installing 14.04.

I think you are correct...

```
*-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff


```

---

### Post by pmonacular on 2014-04-14
> **mörgæs said:**
> I bet it's an Intel 8xx. 
The correct xorg.conf can be seen if you read the link in my signature. Another option is installing 14.04.

I have what I should add to xorg.conf, I'm just not sure how to create it.  Perhaps I should have put this in the newbie section. :P

---

### Post by mörgæs on 2014-04-14
There are several ways.
You could open Leafpad with the command **sudo leafpad**, copy the text into Leafpad and save it at the correct location.

---

### Post by pmonacular on 2014-04-14
Thank you!  It worked... but as I feared, it did cause another issue.  My screen is mostly black upon booting up.  Icons will show up after mousing over them, but half of the letters in the menus are missing.  Kind of a mess.  I guess I'll have to either delete that config file, or upgrade and spend another day setting everything up.

---

### Post by mörgæs on 2014-04-14
Did you create the xorg.conf with the exact contents that I posted?

---

### Post by pmonacular on 2014-04-14
I did, yes.  Tab before the middle 3 lines and all.

---

### Post by mörgæs on 2014-04-15
Hm, strange...
What about a live boot of 14.04?

---

