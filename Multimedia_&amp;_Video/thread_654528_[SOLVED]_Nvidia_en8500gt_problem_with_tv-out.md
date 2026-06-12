---
title: "[SOLVED] Nvidia en8500gt problem with tv-out"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by Kristian9K on 2007-12-31
Hi all
I've been going through a lot of problems with getting tv-out working with my new card, bought for that sole purpose. I've even considered going back to the-OS-which-shall-not-be-mentioned.

My current status is that I do get tv-out, but not the way I would like it. I get an extra desktop, but I'm going for a clone.

SPECS:
I installed drivers via the Envy script.
I set up xorg with things found in this post: 
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

my xorg.conf:
[http://pastebin.ubuntu.com/3146/](http://pastebin.ubuntu.com/3146/)

my lspci:
[http://pastebin.ubuntu.com/3147/](http://pastebin.ubuntu.com/3147/)

Can anybody help?
Kristian

---

### Post by overdrank on 2008-01-01
> **Kristian9K said:**
> Hi all
I've been going through a lot of problems with getting tv-out working with my new card, bought for that sole purpose. I've even considered going back to the-OS-which-shall-not-be-mentioned.

My current status is that I do get tv-out, but not the way I would like it. I get an extra desktop, but I'm going for a clone.

SPECS:
I installed drivers via the Envy script.
I set up xorg with things found in this post: 
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

my xorg.conf:
[http://pastebin.ubuntu.com/3146/](http://pastebin.ubuntu.com/3146/)

my lspci:
[http://pastebin.ubuntu.com/3147/](http://pastebin.ubuntu.com/3147/)

Can anybody help?
Kristian

HI and although that first link maybe a good thread it is a little outdated. Have you tried using nvidia settings to setup up your TV. There is option separate x screen.

---

### Post by Kristian9K on 2008-01-01
Yes, I have goofed around with Nvidia settings as well as the "Screens and Graphics" tool in Ubuntu - no luck.

---

### Post by Kristian9K on 2008-01-01
Well... after doing some thinking, I think my next step should be changing xorg.conf to TwinView. I tried this earlier on, but was still having some basic problems then, which are sorted out now. I've been rebooting X for a week now, so thanks to everyone reading this and giving it some thought.

Happy New Year
Kristian

---

### Post by Kristian9K on 2008-01-02
No need to worry about this anymore, found a workaround that will have to do until I can get a geek, sorry expert to look at my machine :)

This Nvidia-driver really is a bummer though, even more so as it looks like the real problem (getting the source code) won't be solved anytime soon :(

Kristian

---

