---
title: "INTREPID GeForce4 Card.  Cannot get acceleration to work"
date: 2009-04-26
forum: Multimedia Software
---

### Post by guitarMan666 on 2009-04-26
A friend of mine and I are trying to set up her computer with Ubuntu and we are attempting to get her old NVidia card to a high resolution.  While 3D acceleration isn't a real issue it certainly seems like getting it enabled would also allow us to use her monitors full resolution (which because it's a CRT is fairly high).

We have tried the proprietary drivers (nvidia-glx-71 and nvidia-glx-96) to no avail.  They give a max res of 640x480.  The open-source, non-accelerated driver gives a maximum resolution of 800x600.  Our target resolution is AT LEAST 1024x768.

Here is her output from a quick check:
```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX - nForce GPU]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

```

Any thoughts would be great.  We would upgrade to Jaunty but it seems that Jaunty doesn't use the latest XOrg server and so the issue would remain.

---

### Post by inobe on 2009-04-26
tell me what methods you used to install the proprietary driver.

---

### Post by guitarMan666 on 2009-04-26
We installed the driver thru Synaptic.  However we solved the problem using a different method posted at [http://ubuntuforums.org/showthread.php?t=971103](http://ubuntuforums.org/showthread.php?t=971103).  Now it seems windows cannot be resized or moved (while using Compiz) without using the window menu.  I will however post this in the topic where we got the fix.

---

### Post by inobe on 2009-04-26
good deal :)


guitarMan666 when ever you start a thread always include the changes you made, this is so we can avoid adverse affects and also provide a solution you haven't already tried :guitar:

so you bang the strings, are you base player ?

no need to answer :P

---

