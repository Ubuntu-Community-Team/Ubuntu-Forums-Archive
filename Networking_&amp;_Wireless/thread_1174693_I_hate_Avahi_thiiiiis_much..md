---
title: "I hate Avahi thiiiiis much."
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by nautilus on 2009-05-31
Alright, I've been using Ubuntu for a long time now, but I've had it with Avahi.  In fact, it's the first thing I have torched from my installation as matter of course, but of late, I can't.  I mean I COULD but I'd basically lose any usable installation of X along with it, and a fair chunk of the programs I use.

Case in point:  My audio doesn't work when Avahi isn't running.

Perhaps I'm a babbling idiot who doesn't see the obvious and integral association between my sound card and my ethernet card, but this strikes me as ... well, stupid.  I don't like/want/care about Avahi at all.  I basically have to 'un-convenience' my Avahi setup for about an hour instead of taking the 20-30 seconds to edit my /etc/network/interfaces file and adding 4 lines, the second of which reads "iface eth0 inet static" which, might I add, is no simple task with Avahi. ([http://ubuntuforums.org/archive/index.php/t-296880.html](http://ubuntuforums.org/archive/index.php/t-296880.html))

More to the point, if Ubuntu wants to switch to autoipd, fine.  Do it.  Don't leave competing and obviously conflicting legacy implementations laying around to compete with it.

Remove iproute, remove ifconfig, remove any semblance of manual network management.  Why?  Because it's simply not possible with autoipd kicking around!

Seems like convenience at a disgustingly high price, at least with Win32 you can change such settings with a single utility, dhcp to static, change IPs, etc.  Mac, too, I use those also.  These systems manage to be automated without being intrusively domineering and inconveniently impractical to 'configure' (CAN you configure autoipd?).

Okay, so instead of swearing under my breath I simply uninstall autoipd and carry on... now on Firefox it defaults to Offline Mode.  For the informed, it's simply a matter of going to the File menu, and un-checking the "Work Offline" checkbox, but this is, to me, is broken.  Also broken is the "Not Connected" ethernet icon which has become a fixture on my gnome menubar.  And yet, here I am, typing this message.  It's all because I removed autoipd.  Doing so has left my system in a 'broken' state, but I promise it's far more usable like this than with the crippling mess of Avahi.

---

