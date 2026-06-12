---
title: "Screen shifted to the right with NVidia drivers"
date: 2009-01-18
forum: Multimedia Software
---

### Post by chriswyatt on 2009-01-18
Recently I got a new screen fitted into my laptop (sent it to a computer store).  When I went to the store to check it with the new screen the picture was about 10 or so pixels shifted to the right and the pixels that were supposed to be on the right of the screen were on the left.  This wasn't happening on the BIOS setup screen but was happening while Ubuntu was loading.

At the time nvidia-glx-180.11 was installed so I tried rolling back to the previous stable drivers.  Same problem but logon screen was OK this time, but when I logged in the screen then shifted to the right.  It seems that Compiz triggered it though I didn't make this connection at the time, but I'm quite sure it was enabled.

This wasn't good enough and I thought it was the screen so they ordered the same screen I had in my laptop before and this appeared to be fine.  But when I got home I once again installed nvidia-glx-180.11 and the screen was shifted to the right again but only when I started Compiz :S .  Loading screen before Ubuntu was fine and so was login screen, it was when Compiz loaded it shifted.

When the guy fitted the first screen it bothered me that this was happening when he tried the Windows Setup disk also, Windows setup was shifted (the blue DOS like Windows Setup screen).  So it seemed like a general problem rather than one relating to Ubuntu or the NVidia drivers.

Or could it be that using the latest NVidia drivers triggered this problem and it carried on into booting into Windows Setup?  Using nvidia-glx-180.22 at the moment and I still have the issue.

I didn't have this before the new screen was fitted, with either nvidia-glx-180.11 or nvidia-glx-180.18 or nvidia-glx-177 installed :S .

---

### Post by 73ckn797 on 2009-01-18
I ahve had that problem with my desktop but was able to adjust screen with monitor config button on the monitor. I do not see one on my laptop to do that but never had that issue on the laptop. Not much help, am I?

---

### Post by chriswyatt on 2009-01-18
Just to summarise and elaborate:

Graphics card: NVidia GeForce 7200

Original screen - No glitch

1st new screen - glitch whilst loading Ubuntu (without splash screen) but not on BIOS setup screen.

2nd new screen - Glitch only when using nvidia-glx-180 (180.11 and 180.22 tested)

With both new screens the glitch wasn't present when changing to lower resolutions, only on 1280x800.  When playing with the laptop at the shop I even wiped the xorg.conf file which I'd customised before, and I've been using a system-managed xorg.conf since.

When testing 1st new screen in the shop the glitch returned when switching back to 1280x800 after changing it.  At the moment with 2nd new screen the glitch disappears if I switch to another screen and switch back.

It's the randomness and inconsistency that makes this problem a bit confusing, really I want to know whether it was caused by the guy who fitted the screen or a more general driver problem.  HSync problem perhaps?  Both the new screens were being detected properly by my graphics card.

---

### Post by chriswyatt on 2009-01-18
To 73ckn797, thanks for reply.  I did find another thread on Google and that person also managed to fix it the same way as you.  Can't find anything like this on my laptop sadly. (Which is a HP Pavilion dv2058 btw).  Also, I remember with the first new screen I think the glitch doubled-up on the side of the screen but I'm not completely sure, I remember seeing two recycle bins on the left of the screen except for one, very peculiar.  Also, with the first screen GRUB2 had a glitch whilst it initialising, kind of a glitchy white band on the left of the screen though I don't have this now.

---

### Post by 73ckn797 on 2009-01-18
Running Ubuntu on my Toshiba Laptop has no "function" keys working. Those only work with Windows since Toshiba provides the drivers for the keyboard special features. I have not looked into whether Ubuntu has anything that will make those work.

---

### Post by HavocXphere on 2009-01-18
LCDs don't do usually do the pixels to the left/right thing. CRT yes, but not LCDs.

The other thing that comes to mind is the connection. Displays connected via analog tend to do weird alignment things more than those connected via digital. Not sure how the connectors work on laptops, but I suppose it can have both analog and digital internally.

I doubt that the PC shop messed with a nix install so something has presumably changed hardware wise.

---

### Post by 73ckn797 on 2009-01-18
> **HavocXphere said:**
> LCDs don't do usually do the pixels to the left/right thing. CRT yes, but not LCDs.

The other thing that comes to mind is the connection. Displays connected via analog tend to do weird alignment things more than those connected via digital. Not sure how the connectors work on laptops, but I suppose it can have both analog and digital internally.

I doubt that the PC shop messed with a nix install so something has presumably changed hardware wise.


Yes, as mentioned, My laptop has never had that problem, so, there you go!

---

### Post by chriswyatt on 2009-01-18
Here's the screen my laptop uses:

[http://www.auo.com/auoDEV/products.php?sec=notebook&func=info&product_id=88&items_id=2](http://www.auo.com/auoDEV/products.php?sec=notebook&func=info&product_id=88&items_id=2)

The interface it uses is 1ch LVDS.  Timing issue perhaps but it's weird that it would be caused by switching Compiz on.  Or maybe Compiz reinitialises the display and just causes this hardware problem to surface.

By the way, does this effect have a technical name, is this skewing?

[http://en.wikipedia.org/wiki/Low-voltage_differential_signaling](http://en.wikipedia.org/wiki/Low-voltage_differential_signaling)

---

### Post by chriswyatt on 2009-01-19
I found a similar issue to mine, not quite the same:

[http://ubuntuforums.org/showthread.php?t=484011&highlight=nvidia-glx+screen+shift](http://ubuntuforums.org/showthread.php?t=484011&highlight=nvidia-glx+screen+shift)

---

### Post by pmendham on 2009-01-19
I have exactly the same problem, but without the hardware issues. I have a Sony Vaio Laptop running Intrepid and have just upgraded to the 180 nVidia drivers using the restricted drivers tool. Everything was fine until I spun the desktop (compiz effect) which was the first time compiz had been required to do anything.  At that point the desktop shifted right (and wraps round) and has stuck there.  As far as I can see, this entirely a 180.xx driver issue (or certainly related to it).  Anyone got any ideas?

TIA

---

### Post by chriswyatt on 2009-01-19
Is this anything to do with LVDS then?  Seeing as when my 1st screen was fitted it was a similar problem to what I have now, but more severe.  By the way NVidia X Server tells me it's a dual connection.  Also, like in the other thread toggling the GPU settings helps.

---

### Post by pmendham on 2009-01-19
IMHO this is nothing to do with LVDS.  In my case this does not appear to be hw related at all.  This appears to be an issue with the 180 version of the nVidia drivers.  I only upgraded to sort out the title bar rendering bug, and now I get this :)

I have the same situation as chriswyatt, if I open the nVidia X server settings and switch the GPU scaling method to "centred" and back to "stretched" again, it sorts itself out.  But I have to do this every time I reboot.

---

### Post by pmendham on 2009-01-19
In fact, if I leave the gpu scaling set to "centred" all I need to do is *open* the nvidia X server settings and it sorts itself out. Bizarre.

---

### Post by chriswyatt on 2009-01-19
Does that always work though.  Sometimes when I open up NVidia X Server Settings the screen flashes to black as I'm guessing its resetting.  I tried setting to centred, switching to Compiz to bring the issue back and going back in but the glitch didn't disappear.  Perhaps if I opened server settings for the first time in a session it would work as the screen flashed when I first loaded it this session.

I'm still debating whether to take my laptop back to the computer shop as it'll be difficult to convince them it's a hardware problem seeing as it only happens with the latest drivers.  Sadly I don't have Windows installed to test with, I would install it but it's too much hassle (SCSI drivers and not having a full version of Windows to hand to authorise my Windows XP Upgrade disc).

Tonight I'm probably going to install Windows 7 Beta to some empty space on my HD and see how things turn out, if Windows is fine I'll assume it's a Linux/NVidia problem, if not I'll have more of an argument for blaming the guys at the computer shop.

Also, pmendham, are you getting a 1 pixel tall line at the top of the screen that looks garbled?  I can see a . moving with my mouse pointer and a few other dots, bit like when you see the VBI interval on a TV set.  If anyone wants me to do a screenshot I could take a photo on my phone and upload.

---

### Post by chriswyatt on 2009-01-19
OK, another interesting thing.  The glitch only occurs when I enable Compiz through System, Preferences, Appearance.  Not when I enable/disable Compiz via the Compiz Fusion Icon.  Neither does the Compiz Fusion icon get rid of the glitch once it's there.

Not speaking with much knowledge but it seems to maybe be an inconsistency between the way NVidia's drivers handle the videocard and the way Ubuntu itself handles things, just my two cents.

---

### Post by Danielaus on 2009-01-24
Hi guys!
I also have the same exact problem on my Ubuntu 8.10 Laptop with nVidia proprietary drivers and compiz!
I agree that the bug should be related to the drivers (180.11) or compiz, and their interaction.
If I select the desktop effects from ubuntu desktop settings I get like 10-15 pixels of the right of the screen wrapped on the left. There's also, like someone noted before, a row of 1-2 pixels on the top that's screwed.
There is the possibility to activate compiz from compiz-fusion-icon too, and from here there are no problems(as said before)!
Don't know if it's of some help, but I noted that if I take a desktop screenshot there's no shifting in the captured image.
I also figured out that there is something wrong with gnome-settings-daemon (although I don't know if this is related).
My screen is 1280x800. if I change the resolution to 1024x768 from gnome display settings, the screen becomes again straight, but I loose all my theme settings, and seems that gnome-settings-daemon crashes, but there's is no logged error anywhere. Now I have to set again the resolution to 1280x800 and manually start gnome-settings-daemon to apply this change e have back my theme.
For now I solved with this script on my desktop and I run it on every boot, but I would like to find a better solution! (The sleeps are there to give the time to the card to set the options)

```

#!/bin/bash
nvidia-settings -a GPUScaling=1,1
sleep 2
nvidia-settings -a GPUScaling=2,3
sleep 1

```

---

### Post by Danielaus on 2009-01-25
Hi guys!
Have someone figured out what the problem is?
I filed a bug here [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/321224](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/321224)
trying to include as many informations as possible

---

### Post by chriswyatt on 2009-01-25
Subscribed and added some more info, also marked that it's affecting me also so hopefully it'll attract some devs :).

---

### Post by Danielaus on 2009-01-25
Thanks!! I'm crossing **all** my fingers!!;)

---

### Post by chriswyatt on 2009-01-28
Someone has mentioned this on NV News :)

[http://www.nvnews.net/vbulletin/showthread.php?t=123852&highlight=screen+shifted](http://www.nvnews.net/vbulletin/showthread.php?t=123852&highlight=screen+shifted)

---

