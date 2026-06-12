---
title: "[SOLVED] m1530 mic - works in ubuntu, not kubuntu"
date: 2008-05-13
forum: Multimedia Software
---

### Post by rossmoore on 2008-05-13
Hi all,

The title says it all. I installed Ubuntu Hardy on my M1530, and got the internal microphone working by switching on the appropriate channels in the volume control.

I then decided to try out Kubuntu Hardy (not KDE4) on my M1530. I think I probably prefer it, but I can't get the mic working.

The volume control settings in Kmix are a bit different from those in Gnome, so I've had to make a few sensible guesses, but I can't hear anything.

Any suggestions? And is there a quicker way of testing it in Kubuntu than using Skype test calls? ;)

Thanks,
Ross

---

### Post by rossmoore on 2008-05-14
Does anyone have any suggestions?

aplay -l reports two sound card drivers, a digital and an analogue one.
Everything appears to be enabled in alsamixer - although I have options of "mic" and "front mic", and I don't know which it should be.
Kmix seems to reflect the settings in alsamixer.

I've found a quicker way of testing than using Skype, I think. Is arecord and aplay the right answer? I can't be sure, given that my mic doesn't work!

I'd love to hear from a sound guru, or just someone with a working M1530 or M1330 mic in Kubuntu so I can nab their settings.

Cheers,
Ross

---

### Post by rossmoore on 2008-05-14
no ideas, anyone? Not having a mic's gonna be a bit of a disaster - I don't want to have to install a different operating system over this, even if it is only ubuntu rather than kubuntu.

---

### Post by Zorael on 2008-05-14
Likely it works but the volume control applet (kmix) is confusing you. :>

You could try entering [FONT="Courier New"]alsamixer[/FONT] in a terminal and see if that's easier to understand. And I guess there should be a package for the gnome mixer somewhere; I don't know the name of it.

edit: [gnome-alsamixer](http://packages.ubuntu.com/hardy/gnome-alsamixer)? I'd try that one.

---

### Post by rossmoore on 2008-05-14
Ahh - yes, kmix is confusing me. You've definitely helped thank you! I tried downloading gnome-media, the package that contains gnome-volume-control, and then followed the ubuntu style instructions elsewhere on this forum (just search google for m1530 ubuntu mic). That didn't get me anywhere - I'm not sure why.

But then I thought there must be a way to get the same level of control in kmix, and the answer is that if you right click on one of the volume controls there's a menu that comes up and gives you the opportunity to set the channels - which is where the magic is. Switch on Digital, digital input mic 1 and surround (as in the link mentioned above) and it all works perfectly.

I think they need some usability testers on that mixer - but I got there in the end. Thanks for your suggestion, and nudging me in the right direction!

---

