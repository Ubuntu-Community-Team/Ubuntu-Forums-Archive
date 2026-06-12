---
title: "Can't get a complete working ATI Driver installed!"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by bus_ter on 2008-01-18
Video Card: ATI X1950 Pro 512mb AGP
Monitor: Dell 1905FP (Digitial)
OS : Ubuntu Gutsy 7.10 (clena install)

I can't get an accelerated driver installed and working that will support 3D Destops like Compiz.

The original Open drivers work great but have no acceleration, and to me aren't even suitable for deskktop use. Scrolling web pages is a choppy affair.

The default proprietary drivers that can be installed automatically also work ok. Hardware acceleration works ok but can't use Compiz.

I've tried Envy but after rebooting the PC goes to a Black screen and locks up. I have to edit the xorg.conf file to get back in. I tried the manual options and none of the drivers worked with the same Black Screen issue. One of the drivers was 8.40.4. I have those installed in PCLinux working ok.

So what do I need to do to get an accelrated ATI driver installed that will let me use a 3D desktop?

There are I've noticed A LOT of posts on here regarding video card drivers. Going through them is like a needle in a haystack. I don't know what I need to do.

Perhaps someone has similar hardware to me and can hopefully suggest a solution.

Thanks in advance.

---

### Post by LebThug on 2008-01-23
I have the same problem as you.  My AGP ATI X1950 512MB Sapphire card just won't work with anything but the default VESA drivers.

I tried installing the new 8.10 drivers from ATI website following the manual install instructions, I tried installing drivers using ENVY, all results go to a black screen and no option but to reboot in recovery mode and use "dpkg-reconfigure xserver-xorg" to reset settings.

I've been searching for a week and I agree, finding the one solution is near impossible with all the posts! So i join in hope of some1 using the same card helping us out...

---

### Post by Talon2 on 2008-01-23
I feel your pain.

I have the same problem with a x1650pro 512mb agp.

I tried to install the latest 8.1 driver and all I get it a blank screen.

I've been researching the issue.  I can't say for sure at this point but it seems like a lot of people with similar problems are running agp cards.

Could the problem be in the agp support?

---

### Post by mumidadi on 2008-03-06
yeah same here ! i been working all this evening to install Ati driver and still all in vain besides teh fact that installation completed and there is ATI catalyst in Applications but it dsnt response and neither it works......visual looks ant work either

---

### Post by sanddgroper on 2008-03-06
Hi Guys
Maybe I am missing something here but I thought vesa and envy were for
nvidia cards.
If you have used these drivers god knows how screwed up your system.
as for compriz I dont think it is all lthe best at the moment I have it turned of.

Cheers
Sandy

---

### Post by alexforcefive on 2008-03-07
Envy can install ati drivers as well as nvidia drivers. However, it doesn't work :p

I got my direct rendering working using [this guide]("http://linuxmint.com/forum/viewtopic.php?t=6317"). glxgears goes really weird, but it seems to work ok apart from that. I did some extensive "testing" using planet penguin racer :D

---

