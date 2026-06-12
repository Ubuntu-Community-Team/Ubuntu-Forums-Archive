---
title: "more then one graphics card?"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by dstone on 2006-05-27
I've tried over the years to make the switch away from windows to linux on my home PC, but have never been able to get everything I want working the way I want it.
I'm trying again. I spent a day futzing around with Suse 10.1, what a mess...

So I'm wanting to give ubuntu a shot. I have two graphics cards in my PC which under XP obviously allows me to run dual monitors. I would like to do the same under linux.

One is a Nvidia GeForce2 MX/MX400 and the other is an ATI Radeon 9250

When I was messing around with Suse, I was able to (eventualy) get through the install, and everything looked great, although it only ever used the Nvidia, which is the first card. No worries, I figured I could enable the second one after install or whatever.
Nope.... after install I could never boot into X, ever. Spent a day messing around with various configurations, and still no go. I gave up and here I am.

Now , my actual question is... Can I run two graphics cards and get dual monitors under linux in general and Ubuntu in particular, and if so, what in the world do I have to do in order to make it work. I can not for the life of me find anything that talks about this, and that's not for a lack of google and forums searches all over the place!

thanks,
dstone

---

### Post by IYY on 2006-05-27
Yes it is possible, and there are plenty of tutorials that describe this. For example:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards)

Don't worry about the X -configure part, just edit the xorg.conf file.

There's a sample file here too:

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/39966-duel-monitoirs-wiyh-two-graphics-cards.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/39966-duel-monitoirs-wiyh-two-graphics-cards.html)

---

