---
title: "[SOLVED] Problem with 3D games in Ubuntu 7.10"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by Nerdriot on 2008-01-29
Hello,

I'm having a bit of difficulty, and no one seems to be able to help me.

I have an onboard VIA Unichrome video card, which, I know, it's awful, but it's what I have at the moment.

When I run glxgears, the 3D does appear to be working. The gears move, and my FPS is generally between 400+ and 600. Not too bad, I suppose.

However, when I try to run most 3D games, like SuperTuxKart, it runs fine for a few seconds, then freezes up, and I eventually have to reboot my machine.

Someone suggested adding this in the xorg.conf file, but when I added it, 3D games refused to work at all mostly, and running "glxinfo" freezes my machine, and running glxgears gives me a segmentation fault.

Basically, I'm just wondering if there is ANYONE here who has managed to get 3D games working properly with a VIA video card, and if so, how'd you do it? I would almost be willing to pay to have it fixed at this point... gah. ::Shakes fist at Microsoft for having a monopoly::

Thanks for any help, guys. It's MUCH appreciated!

---

### Post by overdrank on 2008-01-29
> **Nerdriot said:**
> Hello,

I'm having a bit of difficulty, and no one seems to be able to help me.

I have an onboard VIA Unichrome video card, which, I know, it's awful, but it's what I have at the moment.

Thanks for any help, guys. It's MUCH appreciated!

Hi and have you looked here
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by Nerdriot on 2008-01-29
Hey, thanks for the reply :)

Well, the pre-installed VIA drivers from the Ubuntu 7.10 installation (as far as I know, the newest VIA drivers) failed to play 3D games properly for me, which made me decide to try Openchrome. I have the same results with it, too.

It's kind of odd, really. In order to get WINE to work, I have to disable 3D rendering altogether. Then, what few games actually do with 3D, won't work at all. But, if I have 3D rendering enabled, WINE crashes/freezes, and most 3D games (like SuperTuxKart) freeze, and force me to reboot.

I've added "*Option 		"EnableAGPDMA"*" under "Device" in my xorg.conf, which someone said would help if there's a big lag or freeze, but it failed to do anything, really. Adding "DisableIRQ" essentially causes the machine to refuse any 3D game, and locks up the machine, too.

I'm completely at a loss. The official VIA drivers don't work with 3D properly, and the Openchrome drivers don't, either. I suppose there's nothing I can do, sadly. I was just hoping someone had some kind of miracle fix for it, but it looks like, because VIA is an absolute failure at releasing decent drivers for Linux, there's nothing that can be done...

Sadface.

---

### Post by Nerdriot on 2008-01-30
BTW, I did end up installing the VIA drivers from their site, which caused major issues. The screen was warped, and couldn't be adjusted. Then, when I used "glxinfo | grep render", it showed that rendering was off, and so on. I had to uninstall the VIA drivers, and re-install Openchrome to get the display back to normal. I had to do all of this in the Generic kernel, mind you...

Now, the generic kernal says I have no 3D, no matter what I do, even after installing the Openchrome drivers, and basically returning it to normal. It's as if it's ignoring my Xorg.cong file altogether...

Weird.

I'm using the RT kernel now, and everything is "normal" again. 3D will crash most times, and WINE hates it, but at least it's normal.

---

### Post by Nerdriot on 2008-01-31
I'm marking this thread as "Solved", only because I know there's no real resolution, because VIA refuses to release good working drivers.

Some 3d games work, and others don't. It's iffy, really.

I re-installed Ubuntu, and the standard drivers do their job nicely, considering.

Adding the aforementioned entries in xorg.conf seem to work a little, but won't be a magic fix.

Thanks anyway, guys. :)

---

