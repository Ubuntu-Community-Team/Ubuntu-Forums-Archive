---
title: "Long-standing refresh rate problem"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-07-10
This is a problem I've had for a long time, and my last topic here gained me no possible solutions. I'm going to copy everything I know about this from a [web page](http://pointlessness.freehostia.com/2007/june/tofix.php) I made chronicling the various problems I'm having with Kubuntu (everything on the page is current unfixed by the way):

> From a stock Kubuntu 7.04 install, this combination results in a bizarre refresh rate of 56Hz (interlaced) at 1024x768. Needless to say, this combination of video hardware and monitor can take a hell of lot more than that.

After a while, I found the easiest way to rectify this was to use Restricted Manager to install nvidia-glx (NVIDIA's own binary drivers, in deb form) and tell the KDE Control Panel the exact monitor I'm using (Samsung SyncMaster 793s). This tells me I should be able to use up to 87Hz at 1024x768, which is good since I want to use 85Hz.

After doing this, the login screen suddenly gets up to 1024x768 @ 85Hz, which is good. But after logging in, it suddenly goes down to 1024x768 @ 75Hz, which isn't so good. It gets even stranger in the KDE Control Panel, where I'm then told that the only refresh rates available for this resolution are 50Hz, 51Hz, 52Hz, 53Hz, 54Hz, and 55Hz (bear in mind the monitor is at 75Hz as I look at this).

I can fix this one of two ways. Either by using the KDE Control Panel to change my monitor to a different type, then back to the one I'm actually using (at which point the correct range of refresh rates comes into play) or by using nvidia-settings (either with or without superuser privileges, it makes no difference) where 85Hz is available. Either of these will get me 85Hz, but only for one session. After logging out and logging in again, I'm back to 75Hz, and nothing can make KDE stick with 85Hz between sessions.

So I can get 85Hz easily for one session with nvidia-settings (which is exactly what I do) but can't make this perfectly valid setting stick. No one seems to know why either.
That's everything I know.

---

### Post by iota on 2007-07-11
[http://www.linuxcompatible.org/Screen_refresh_rate_t33565.html](http://www.linuxcompatible.org/Screen_refresh_rate_t33565.html)

Read the second post. Hope that helps :)

---

### Post by Rhapsody on 2007-07-11
Nope. Not only did that not work (KDE seems to be completely ignoring xorg.conf and deciding the possible refresh rates by some other means) but nvidia-settings would no longer allow me to use 85Hz after the changes. I've now reverted them.

I actually one tried editing xorg.conf so 75Hz was below the minimum possible refresh rate available. The result? KDE continued using 75Hz. How is that even possible?

---

### Post by iota on 2007-07-11
Now that's weird ^^ Any chance you could you post a copy of your xorg.conf?

I'm not exactly very good but I'll try and take a look at it, and hopefully someone better than me will come and help soon too :P

---

### Post by Rhapsody on 2007-07-14
Sure. To avoid making this post unnecessarily large, I've [uploaded](http://pointlessness.freehostia.com/other/xorg.conf.txt) it to my website.

What I find most interesting in it is the various "ModeLine" lines in the Monitor section. The first starts with "1024x768@85", and seems pretty valid. Given all that, KControl should allow me to select 43Hz, 60Hz, 70Hz, 75Hz, or 85Hz at 1024x768. So why does it present me with 50-55Hz instead?

---

