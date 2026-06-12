---
title: "Mythbuntu 10.04 upgrade - X doesn't start if no monitor connected"
date: 2010-05-03
forum: Mythbuntu
---

### Post by ardnut on 2010-05-03
In mythbuntu 9.10 if I turned on my monitor after my mythbox had been turned on then I would get no signal but could remotely connect via VNC, logout and back in again and it would work.

Now with mythbuntu 10.04 in this same scenario xorg doesn't start at all and complains about the lack of monitor, which means I can't even log in via VNC.

Is there a way to fake xorg in to thinking my monitor is always connected?  That would be the ideal setup then I wouldn't even have to VNC in.

I have a nvidia 9500gt graphics card.

Thanks,
Ash

---

### Post by slamhound on 2010-05-03
I've seen a bunch of threads on this but have not seen a good solution.  One workaround is to physically trick the computer into thinking that there is a monitor plugged in. Some have put things together using dvi-to-vga adapters, but in my case, I had an old dead video card laying around. I plugged the cable from the computer into this dead card (which is not attached to anything), and even though it isn't a monitor, now the computer thinks there is a monitor hooked up. Everything boots fine.  This is on 9.04, but I've heard of such tricks working on other versions.

---

### Post by ian dobson on 2010-05-03
Hi,

I posted a link to a vga dongle afew days ago. All it does is trick the graphic card into thinking a monitor is attached.

Heres the thread [http://ubuntuforums.org/showthread.php?t=1463178](http://ubuntuforums.org/showthread.php?t=1463178)

Regards
Ian Dobson

---

### Post by Oblong_Cheese on 2010-05-03
While remotely administering my system, I rebooted it and could no longer establish a VNC connection. Checking the X.org logs, I saw there was a "no screens found" error, and I am guessing this is why.

Aside from physical means, I am keen to find a way to fix this. It would be no problem for me to plug a DVI-VGA dongle in to trick the system (I use HDMI output), but for people for whom this is not an option, a solution would be great!

---

### Post by ian dobson on 2010-05-04
Hi,

I believe the problem is the graphic card/bios that don't pass information that a monitor is attached, The only solution that I can think of is use a different graphic card or use the vesa graphic driver in X or try an force X to use a "non-existant" monitor.

What do you see in your X log file when you boot with a monitor attached and without?

Also what driver are you using?

Regards
Ian Dobson

---

### Post by snop3 on 2010-05-04
Hi,

the problem is in the KMS.

Here is decribed the problem and created the ticket:
[https://bugs.freedesktop.org/show_bug.cgi?id=27949](https://bugs.freedesktop.org/show_bug.cgi?id=27949)

There is also a workaround:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

Pls, if someone will have a time, pls help fix this problem.

Thank you

---

### Post by ardnut on 2010-05-04
Thanks for the info.  I was planning this evening to have a go at following this guide...
[http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/](http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/)

From reading about the KMS issue I take it that I'll need to first update my grub2 config options to force it to not ignore my xorg.conf file.  Is that a correct assumption?

---

### Post by snop3 on 2010-05-04
> **ardnut said:**
> I'll need to first update my grub2 config options to force it to not ignore my xorg.conf file.  Is that a correct assumption?

no, pls read the links which i have posted, there is everything what you need

---

### Post by ardnut on 2010-05-04
ok, apologies I'm now a bit confused.

Your first link talks about KMS causing video issues and when you disable KMS and use your old xorg.conf file it then all works.

The second link describes how to disable KMS by adding a boot option to grub.

The link I posted describes how to "save" the state of my connected monitor and how to pass that to xorg every time (using an xorg.conf file) so that even if the monitor is switched off then it still works as if it is turned on.

From your reply I guess I've misread something, could you explain where I'm wrong in my above thinking?

Thanks.

---

### Post by snop3 on 2010-05-04
> **ardnut said:**
> The link I posted describes how to "save" the state of my connected monitor and how to pass that to xorg every time (using an xorg.conf file) so that even if the monitor is switched off then it still works as if it is turned on.


Hi ardnut,

sry, now I apologize :)

This is little bit different problem, so pls try disable KMS if it's solve yours problem, but the problem is in KMS, so pls file bug at:
[https://bugs.freedesktop.org/enter_bug.cgi?product=xorg&component=Driver/Radeon](https://bugs.freedesktop.org/enter_bug.cgi?product=xorg&component=Driver/Radeon)

There are really good guys and reply immediately and tell you what to do, I have very good experiences with guys which are developing radeon drivers. ;)

---

### Post by ian dobson on 2010-05-04
Hi,

Isn't Radeon for ATI cards, ardnut posted in post one that he's using a " nvidia 9500gt graphics card".

Regards
Ian Dobson

---

### Post by mathog on 2010-05-04
> **ardnut said:**
> Is there a way to fake xorg in to thinking my monitor is always connected? 

If by "thinking my monitor is always connected" equates to "always start X11 server", then yes:

[http://www.nvnews.net/vbulletin/showpost.php?p=1957437&postcount=6](http://www.nvnews.net/vbulletin/showpost.php?p=1957437&postcount=6)

---

### Post by snop3 on 2010-05-04
> **ian dobson said:**
> Hi,

Isn't Radeon for ATI cards, ardnut posted in post one that he's using a " nvidia 9500gt graphics card".

Hi,

so absolutely sry, I have problem with ATI 9500 ;) lol, so i should delete all my posts, but I can't.

---

### Post by ardnut on 2010-05-04
No worries.

I've just followed this guide...
[http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/](http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/)
...and xorg starts perfectly whether the monitor has been turned on before or after my machine has booted.  Didn't even need to disable KMS so that's a bonus too :)

---

