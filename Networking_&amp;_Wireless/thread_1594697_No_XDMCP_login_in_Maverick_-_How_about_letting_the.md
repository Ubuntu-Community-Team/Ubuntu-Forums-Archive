---
title: "No XDMCP login in Maverick? - How about letting the user decide?"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by jssilva on 2010-10-12
Hello all,

I can't do without remote XDMCP login, as explained below, not available in Maverick any more. So, either someones helps me to get it back or I'll have to switch to Debian.

In fact, in Maverick release notes:
"**Ubuntu 10.10 does not support the XDMCP protocol for remote graphical logins**. Users who require XDMCP support will need to install another display manager, such as wdm or xdm, for this functionality"

It happens that I need timed auto-login, as explained in a while, and xdm doesn't do it at all; as to wdm, it stops a couple of "enter" keypresses away, which I don't know how to provide automatically and, if even if I did, doesn't look very elegant and robust solution. So, no alternatives for me.

What I don't understand is what seems to me as "paternizing" the user, I mean, not letting him decide the security level he needs. As long as the default options don't allow the remote login and there is enough advising against it, why not let the user decide?

Now, my specific situation is my home theater box which, before upgrade to Maverick, used to auto-login and run stand-alone xbmc when the power switch is pressed. I need this because I don't even have a keyboard in the living room and, even if I did, part of my family wouldn't know how to use it just to watch their movies or photos. They use the remote control for that; login would be too cumbersome.

Sometimes, I need to do maintenance to the box and that's why I need remote login. Of course I don't want to keep my family from watching TV while I use it as a screen for the box. I also don't want to disconnect the box and take it to my study where I have the screen and keyboard.

The only situation where I can remote control the box is when a user is already running X, which is not an usual case because I run xbmc standalone. I could run xbmc on top of gnome but again, my family would be very confused.

Although this text isn't perfect English, which is not my birth language, I hope it's enough to communicate my need for your help and also to express my feeling that this modification was very unthoughtful.

Anyway, apart from this, I love Ubuntu and I'll miss it much if I have to move away.

Regards
jss

---

### Post by itzfritz on 2010-10-12
Wow.  I just spent the evening trying to figure out why I couldnt use XDMCP to connect from my windows laptop w/ xming.  Any alternatives?

---

### Post by jssilva on 2010-10-12
> **itzfritz said:**
> Wow.  I just spent the evening trying to figure out why I couldnt use XDMCP to connect from my windows laptop w/ xming.  Any alternatives?

As the authors say, for your case maybe you can replace gdm (I assume you use gnome) by xdm, or better wdm; in any case, you'll loose the auto-login possibility and other gdm features, as I said before.

Regards
jss

---

### Post by jssilva on 2010-10-26
Well, as I couldn't get any help, and after trying all those k..w..x..dm's, had to switch to debian.

It's now working perfectly, as it should; ubuntu-1, debian+1. I guess that not all the latest is so greatest.

Thank you all, anyway.

---

### Post by cszikszoy on 2010-12-09
Try this: [http://ubuntuforums.org/showthread.php?t=1471703](http://ubuntuforums.org/showthread.php?t=1471703)

It works for me perfectly on 10.04.  I use xming on windows and also xnest on my other ubuntu box to connect to my server.  I haven't tried on 10.10 though.

---

### Post by jssilva on 2010-12-09
Thank you for your help. I can't remember exactly but I'm almost sure that I tried that also without success on 10.10.

Anyway, it doesn't matter for me anymore; as I said, I switched to Debian and I'm loving it; it's like our parents: much more prudent, reliable and stable, although not 'latest and greatest', top-of-the-fun.

Keep well.
jss

---

### Post by nuspl on 2010-12-17
Hi, it can be solved with some effort ... hence it would be better to make it available directly.

---

### Post by mckemie on 2011-02-11
What a screwed up mess!  I've had XDMCP working on Ubuntus 8.x and prior.
With 10.10 (server plus Xbuntu), I've tried all sorts of things, WDM, XDM, finally back to GDM.  Enabled WDM and XDM by un-commenting "*  anyhost" in /etc/X11/xdm/Xaccess and /etc/X11/wdm/Xaccess.  Rebooting in each case.  Get a black screen or a screen with an "X" cursor when I "X :1 -query <ip>" from another Ubuntu box on my lan.  With GDM, I add 
[xdmcp]
enable=true
to /etc/gdm/custom.conf
Same results.

If someone understands the problem(s), a howto or a faq would be greatly appreciated.

Or maybe straight Debian is the way to go.  Does anyone know if Mepis or other Debian derivative has this straightened out?

---

