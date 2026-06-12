---
title: "Unable to view video in gnome-mplayer after upgrading to 9.04"
date: 2009-04-24
forum: Multimedia Software
---

### Post by kyl416 on 2009-04-24
After upgrading to 9.04 video won't play in gnome-mplayer. The audio will play just fine, but all I get for video is a white screen. This happens with both xv and x11. Video is working fine in Totem and mplayer.

Video Driver:
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade/XP [1023:9910] (rev 63)

---

### Post by oregonbob on 2009-05-03
I also have video problems after upgrading. Default video app for avi file is gnome-mplayer. If I go full screen, the window goes full screen but the video stays same small size, displaying two images of it.

I guess 9.04 is the buggiest release ever to come out. At least that is what I see.A big price to pay for faster boot times. Something went wrong in management for this to go out. Still hardwaredon't work. USB is in the dark ages. For the first time I am disappointed with Ubuntu.

Wow, I unloaded on that subject.

---

### Post by kyl416 on 2009-05-24
An update on this. If I enter the direct URL to a stream gnome mplayer works fine, however if I open up any .asx playlist file I get the white screen but audio plays just fine.

---

### Post by kyl416 on 2009-06-03
It ended up being a bug with gnome-mplayer and they fixed it in the latest SVN trunk and it will be in version 0.9.6 coming out this week or next week.

Unfortunately Ubuntu's repository is still using version 0.9.4 so anyone else experiencing this problem will either have to wait until they finally update to the latest version or compile it yourself using the SVN trunk at gnome-mplayer's site.

---

