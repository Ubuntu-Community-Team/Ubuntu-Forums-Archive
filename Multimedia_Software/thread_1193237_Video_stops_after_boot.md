---
title: "Video stops after boot"
date: 2009-06-21
forum: Multimedia Software
---

### Post by MarcG on 2009-06-21
I've got a Shuttle gaming PC that I want to use as a Myth box. The motherboard's S-Video connector is broken, so I got a video board from Craigslist. The board is an STB Systems no-known-model, with a 1998 date. STB went away back then, so there's no support from them.

The video is fine during the boot process, up through the Ubuntu splash screen. But, when using just S-video, it never shows the Hardy and no login screen. I know the sync signals are fine because the TV tells me if there's "no usable signal". I don't get that, just a black screen.

If I plug in a monitor before booting, that works fine, and I get scrambled video on the TV, while the monitor is used. If I boot without the monitor, then plug it in later, no video on that, either.

Any ideas on what's going on and how to fix?

Thanks.

--Marc

---

### Post by LKjell on 2009-06-21
Hi I guess I have the same problem. My tv is a Philips tv with HDMI and VGA input. When I boot Jaunty with VGA from the tv I get the progress bar then it goes blank when the login screen pops up. Even if I type in username and password in blindfold the screen stays blank. 

The only solution I have found is to boot and login from a monitor (LCD). Then you connect to the tv. I have an Eee box.

---

### Post by xc3RnbFO8P on 2009-06-21
Never connect VGA or DVI when the computer is turn on!
It will destroy your graphic card.

---

### Post by MarcG on 2009-06-22
Booting with a monitor and then using the S-video just gets me an un-sync'ed TV screen. Maybe I can play with the resolution and make that work. Although that wouldn't be a good solution for me. I don't want a monitor hanging around.

And thanks for the safety tip. I don't think I wrecked my card, since it still works the same as before, but I'll make sure not to push my luck.

--Marc

---

### Post by LKjell on 2009-06-22
I fixed my problem now by using vesa driver. my xorg.conf files looks like this: ```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

```

As for the precaution. Ignorance is always good. Consider all user who connect and disconnect their cables. Kids who connect their PS3 to a TV during use; DVD player' cable is loose and dad is disconnecting it and connect it again. A teacher connect his laptop to a projector while his laptop is on for a presentation.

---

### Post by MarcG on 2009-06-26
Thanks. The vesa driver did it.

---

