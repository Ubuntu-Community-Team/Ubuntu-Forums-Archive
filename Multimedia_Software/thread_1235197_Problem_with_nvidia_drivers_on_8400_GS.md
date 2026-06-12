---
title: "Problem with nvidia drivers on 8400 GS"
date: 2009-08-08
forum: Multimedia Software
---

### Post by Bai Shen on 2009-08-08
I had a 6600 video card in my ubuntu box and everything was working fine.  I had the nvidia drivers installed.

I swapped out the 6600 for an 8400 GS, and now with the nvidia drivers the display doesn't work correctly, and I have no sound.  If I use the ubuntu drivers, the display works fine and I have sound.

The problem with the display is that it cuts off about 1/2" on each edge.

This never happened with the 6600 card, so I'm not sure why the 8400 GS card is causing the problem.

---

### Post by Vakman on 2009-08-08
Follow [this]("http://ubuntuforums.org/showthread.php?t=1125400") HowTo.
That should work out quite well.

---

### Post by Bai Shen on 2009-08-09
> **Thisislaw said:**
> Follow [this]("http://ubuntuforums.org/showthread.php?t=1125400") HowTo.
That should work out quite well.

Unfortunately not.  I just tried that and I still get the same problems as before.  AFAIK, I didn't have any errors when following the instructions, but it still acts the same as with the 180 drivers.

---

### Post by Vakman on 2009-08-09
Okay. When you say "use the Ubuntu drivers" it does not do this. What Ubuntu drivers? Do you mean the ones found in Administration > System > Hardware Drivers?

---

### Post by Bai Shen on 2009-08-09
> **Thisislaw said:**
> Okay. When you say "use the Ubuntu drivers" it does not do this. What Ubuntu drivers? Do you mean the ones found in Administration > System > Hardware Drivers?

No.  I'm referring the the default drivers that Ubuntu installs when I first do the install or run from the live cd.

Doing the Hardware Drivers menu is when I have the problem.

---

### Post by Bai Shen on 2009-08-09
I just tried the linked instructions again, this time using the beta drivers.

With 180, 185, and 190, I still get the exact same problem.

---

### Post by Vakman on 2009-08-09
All right and hate to ask but you are sure you have an 8400 card?
Post the output of ```
lspci
``` to see what hardware you have as well as the output ```
glxinfo | grep direct
```

---

### Post by Bai Shen on 2009-08-09
> **Thisislaw said:**
> All right and hate to ask but you are sure you have an 8400 card?
Post the output of ```
lspci
``` to see what hardware you have as well as the output ```
glxinfo | grep direct
```

The box says Gigabyte 8400 GS.

lspci says it's an 8400 GS (rev a1)

glxinfo says direct rendering: Yes
 GL_EXT_depth_bounds_test, GL_EXT_direct_state_access

Everything worked fine with the 6600.  No idea why I'm having all these problems with the 8400.

---

### Post by Vakman on 2009-08-09
Interesting. Uh, all right so you have tried installing the drivers manually and followed the Howto I linked to you. So far, nothing is working. Have you tried installing the drivers using EnvyNG. This is the link, [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
Try installing the drivers following the steps on that page using EnvyNG.

---

### Post by Bai Shen on 2009-08-11
> **Thisislaw said:**
> Interesting. Uh, all right so you have tried installing the drivers manually and followed the Howto I linked to you. So far, nothing is working. Have you tried installing the drivers using EnvyNG. This is the link, [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
Try installing the drivers following the steps on that page using EnvyNG.

No joy there.  It installed the 180.44 drivers with the same results as every other version I've tried.

---

### Post by Bai Shen on 2009-08-13
Any other ideas/suggestions or am I just screwed?

Could it be something wrong with the card?

And any ideas why the nvidia drivers would screw up the sound?

---

### Post by Vakman on 2009-08-14
> **Bai Shen said:**
> Any other ideas/suggestions or am I just screwed?

Could it be something wrong with the card?

And any ideas why the nvidia drivers would screw up the sound?

Just the sound now? Or does the screen still do that?

---

### Post by Bai Shen on 2009-08-16
> **Thisislaw said:**
> Just the sound now? Or does the screen still do that?

No, it's still both. :(

---

### Post by Bai Shen on 2009-09-01
I take it I seem to be the only 8400 GS owner with this particular problem?

---

### Post by Vakman on 2009-09-02
> **Bai Shen said:**
> I take it I seem to be the only 8400 GS owner with this particular problem?
Unfortunately, I am not sure. You have tried to install the drivers manually, with EnvyNG, and through System > Hardware Drivers. Have also tried beta drivers even. Not quite sure really. Sorry. If I think of anything I will post back.

---

### Post by Bai Shen on 2009-09-16
So, I have new facts to add to this.  I finally had a chance to take it down to the shop and try out a new card.

Last night, I turned it on, and got the exact same symptoms.  Works fine with Ubuntu drivers, but loading the nVidia ones causes the sound to cut out and the screen to overscan.

At the shop we swapped it out for another 8400 GS(same brand, etc).  Plugged it into a VGA monitor and everything worked.  Got sound on the bootup and no overscan.

Plugged it into a DVI monitor.  Worked fine there as well.

Swapped back to the original card.  Worked just fine.

The monitor was running 1440x900.  Don't remember the brand.

So I'm wondering if it's something to do with my setup.  Gonna try hooking the machine up to the tv with a VGA cable and see how that works.  Also going to retry the DVI connection.

I've also been having power problems.  When the machine turns off, it won't turn back on until I unplug it and plug it back in.  However, it booted just fine at the shop.

No idea why all this weirdness is happening.

---

### Post by Bai Shen on 2009-09-16
Okay, I just found out some more information.  The problem appears to be an issue with the hdmi connection.  Not sure if it's specific to my tv.

I plugged headphones into the computer, and it's outputting sound.  But for some reason when the nvidia drivers are loaded, the tv won't output anything.  So I'm assuming there's something wrong with the dvi output.  However, it only seems to have this problem when hooked up to the tv.  As I mentioned earlier, it worked fine on a monitor.

I tried hooking it up to the tv using vga.  The boot screens were weird, but ubuntu detected the 1366x768 resolution that the tv uses internally.  The screen looked okay except for a little bit cut off the top.  Not sure why that happened.

---

