---
title: "Odd Translucent Window Behind GNOME MPlayer"
date: 2010-11-16
forum: Multimedia Software
---

### Post by AdamShumpisxXx on 2010-11-16
I'm having an issue with GNOME MPlayer. I don't know how to explain it in  a manner that would give you guys/gals a proper description of what's going on. So...can you just fix it?

Hahaha...No, I'm kidding. Here's some screenshots.

My desktop with nothing open:

[IMG]http://i55.tinypic.com/167njo6.png[/IMG]

My desktop with GNOME MPlayer open:

[IMG]http://i53.tinypic.com/2zgrv69.png[/IMG]

My desktop with GNOME MPlayer closed and the "Save Screenshot" dialogue box closed:

[IMG]http://i52.tinypic.com/dmy0cl.png[/IMG]

This only happens when I use xv or xvmc as a video output option. No, I can't use vdpau. Maybe it's a window painting issue? I'm using Ubuntu 10.10 Desktop i386 on an Eee PC 900HA (dual-booting with Windows 7 Ultimate). Well, let me know what you think. Thank you very much in advance for your responses!

---

### Post by AdamShumpisxXx on 2010-11-17
Bump, please? I hate this "paper cut".

---

### Post by AdamShumpisxXx on 2010-11-17
So...no ideas from anyone at all? It's just really annoying that I'm forced to install GNOME MPlayer, because of the mozilla-mplayer replacement gecko-mediaplayer, and I have to deal with this graphical glitch when I was perfectly happy with my MPlayer + SMPlayer + mozilla-mplayer combo in previous distributions. If this is fixable...someone let me know, please. Thank you in advance.

](*,)

---

### Post by AdamShumpisxXx on 2010-11-17
My last BUMP before I abandon this post. I'll make another post in General Help a day or two from now for anyone with a similar problem (as well as myself...obviously). If a moderator sees this would you please delete this post as opposed to moving it? I'd rather not have potential helpers see a reply count higher than 0 for obvious reasons. Thanks either way whatever the result may be.

:-|

---

### Post by mc4man on 2010-11-17
there does seem to be an issue w/ gmome-mplayer in 10.10 When opened it opens a blank video window that may be rectangle or broken up. 
Here it disappears when a video starts, or if going to a vid -> open w/ gnome-mplayer you'll see the blank box for a second. (plays vids ok, here I use totem-mozilla for Internet so no use for gnome-mplayer
Why not just use smplayer if you want a gui.

If you wish a newer mplayer for 10.10 this ppa is quite good - updates every 3 days or so
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)
also includes the old gmplayer (mplayer-gui), if that is an interest.

Edit:
the interface has a number issues, -if you go thru the option combo's all sorts of weird behavior can result, occasionally will open correctly somewhat at random
It does open consistently without white or even clear boxes if the showplaylist option is enabled

(most options are set in gconf-editor - apps/gnome-mplayer/preferences

---

### Post by AdamShumpisxXx on 2010-11-18
I did in fact try enabling the "Start with playlist visible" under Edit - Preferences - Interface. The issue no longer appears due to the window now being as large or larger than the translucent window anomaly. The GNOME MPlayer window does however display pink unless it is currently being moved. Still a "paper cut" in my opinion. I might just remove GNOME MPlayer and gecko-mediaplayer and try my luck with another program all together. Thanks for the link. I'll explore that option first.

The thing that still bugs me about this is that the initial anomaly only occurs if xv or xvmc is selected under Edit - Preferences - Player - Video Output and is not present if, for example, x11 is chosen. If anyone knows anything about THAT I welcome a response. Thank you mc4man!

---

### Post by Stigmata13 on 2010-12-30
I'm also running 10.10 and I can too confirm that this also happens to me. It isn't more than annoying, but it would be nice if this small bug did get squished.

---

