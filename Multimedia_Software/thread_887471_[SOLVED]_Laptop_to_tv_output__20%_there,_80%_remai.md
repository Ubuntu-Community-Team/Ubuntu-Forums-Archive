---
title: "[SOLVED] Laptop to tv output : 20% there, 80% remains to be done"
date: 2008-08-12
forum: Multimedia Software
---

### Post by greatboss on 2008-08-12
First let me tell everybody that after days/nights of trying to get laptop output on TV, it suddenly started appearing to head in the right direction when I upgraded from Hardy 8.04 to 8.04.1. Ubuntu-diety ONLY knows why and how ?

But I havent reached the destination. Please advise.

Laptop - Compaq EVO N610C with S-video, mobility radeon 7500
TV     - Bush DVD142TV, analogue, mode AV1

When I boot my machine and do Fn+F4, the messages that appear while booting, start getting displayed on TV which is great, and the laptop screen goes blank - messages are displayed in black and white.

Fine till now.

But when the time comes to display the login screen, 
Login screen appears on laptop screen, with the screen big enough for resolution 800X600, but the letter font is very tiny.

Horizontal black/white bands are displayed on TV screen, which is NOT FINE. 

What must be wrong can any of the experts advise ?

Happy to give any more information required but I want to prove to my wife that using Ubuntu, we can scee the movies on TV screen instead of laptop.

Currently, STUCK STUCK STUCK -:(

PS : After upgrading to 8.04.1 happy to announce that Bluetooth problem also got fixed - was able to transfer files FROM mobile to PC which was not happening before.

---

### Post by Jose Catre-Vandis on 2008-08-12
TV Out is good at running the boot screens but once the graphics driver takes over the fun starts.

What resolution can your TV run at? Suggest you set your laptop down to 800x600 or 1024x768 and see if that makes any difference. if your TV can't hack a higher resolution it will not display properly.

If that doesn't work then the next step is to do some work in your xorg.conf file. Search out the good thread on the forum for TV-Out / Dual Displays

These links might help

[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

[http://ubuntuforums.org/showthread.php?t=50749](http://ubuntuforums.org/showthread.php?t=50749)

[http://ubuntuforums.org/showthread.php?t=85769](http://ubuntuforums.org/showthread.php?t=85769)

---

### Post by greatboss on 2008-08-12
Hi

This is a silly question but how can i check my tv resolution ?
Its a old Bush DVD142TV - TV / dvd combo.

It has various modes like PAL, NTSC etc. Do these modes dictate resolution of the screen ?

Regards
Greatboss


> **Jose Catre-Vandis said:**
> TV Out is good at running the boot screens but once the graphics driver takes over the fun starts.

What resolution can your TV run at? Suggest you set your laptop down to 800x600 or 1024x768 and see if that makes any difference. if your TV can't hack a higher resolution it will not display properly.

If that doesn't work then the next step is to do some work in your xorg.conf file. Search out the good thread on the forum for TV-Out / Dual Displays

These links might help

[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

[http://ubuntuforums.org/showthread.php?t=50749](http://ubuntuforums.org/showthread.php?t=50749)

[http://ubuntuforums.org/showthread.php?t=85769](http://ubuntuforums.org/showthread.php?t=85769)

---

### Post by Jose Catre-Vandis on 2008-08-12
> **greatboss said:**
> Hi

This is a silly question but how can i check my tv resolution ?
Its a old Bush DVD142TV - TV / dvd combo.

It has various modes like PAL, NTSC etc. Do these modes dictate resolution of the screen ?

Regards
Greatboss

Unless the manual or on screen setups tell you, or you can find out from the interweb it's just a guessing game, so start low and build up. My Panasonic 36" widescreen (CRT) won't cope with more than 1024x768

---

### Post by lisati on 2008-08-12
On the one and only occasion I've successfully hooked up my laptop to my TV while running Ubuntu (checking things out in case it's needed when an acquaintance's laptop won't work with a projector), I found that 800x600 seemed to work best.

---

### Post by greatboss on 2008-08-19
Hi

I upgraded to 8.04.1. After that I configured my TV as second screen.

Selected the vesa driver and the problem got solved.

So i can say that I am happy to get output on TV and was able to toggle back and forth between the 2.

The TV output is black and white but that is more related to scart etc. etc.

Very happy with ubuntu - fingers crossed.

---

