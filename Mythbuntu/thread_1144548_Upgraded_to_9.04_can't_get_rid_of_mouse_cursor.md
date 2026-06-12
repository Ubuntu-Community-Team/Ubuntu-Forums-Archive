---
title: "Upgraded to 9.04: can't get rid of mouse cursor"
date: 2009-04-30
forum: Mythbuntu
---

### Post by pssturges on 2009-04-30
Hi,

I just upgraded all three of my mythboxes to 9.04 and all went really well.

I only have one minor problem. On one of my frontends I can't get rid of the mouse cursor on the screen. I've tried checking the setting to hide it in the "Appearance" settings. If I un-check this setting then reset it it will disappear for a while, but it soon reappears.

Strangely, I can't even move the cursor from VNC of by using a mouse connected to the box.


Any thoughts?

Phil

---

### Post by pssturges on 2009-05-29
Still having this problem. Any thoughts?

---

### Post by elgordo123 on 2009-05-29
What happens if you restart the box without the mouse connected?

---

### Post by pssturges on 2009-05-29
Generally I don't have a keyboard or mouse connected. I only connect one occasioally when I need to. 
Thanks

---

### Post by jyavenard on 2009-05-29
I have the exact same problems since I upgraded to 9.04.

Sometimes the mouse cursor re-appears. I have no idea why.

The work around is when I start mythtv, I move the mouse in the bottom right corner so you can't see it.

So I start mythtv with:
  /usr/bin/xwit -root -warp 1920 1080
  /usr/bin/mythfrontend > /dev/null

That's for a 1920x1080 screen, change it to whatever your resolution is.

---

### Post by pssturges on 2009-05-29
Hmm. Interesting that the frontend I'm having problems with is 1920x1080. Doesn't seem like the sort of thing that should matter, but my other frontends are diferent resolution, and they don't have this problem. Is yours 1080i or 1080p. Mines 1080i. Also do you have XBMC installed/running on your system. My problem seems to be more prevelant when I've been switching between myth & XBMC.

Anyway, it's good to know this problem is not unique go my system

Phil

---

### Post by jyavenard on 2009-05-30
> **pssturges said:**
>  Is yours 1080i or 1080p. Mines 1080i. Also do you have XBMC installed/running on your system. My problem seems to be more prevelant when I've been switching between myth & XBMC.


1920x1080 screen...

I see the mouse cursor reappear when I use xrandr to change the refresh rate.

---

### Post by pssturges on 2009-05-30
> **jyavenard said:**
> I see the mouse cursor reappear when I use xrandr to change the refresh rate.

I seem to remember something about XBMC using xrandr. I wonder if that's where the problem is?

Cheers
Phil

---

### Post by gator on 2009-05-30
same here. i wrote about it in another thread. [http://ubuntuforums.org/showthread.php?p=7298264#post7298264](http://ubuntuforums.org/showthread.php?p=7298264#post7298264) and then i read yours - so i'm not alone this has happened since adding the refresh definition file. Hopefully we will find an answer

mythbuntu 9.04 x64
msi 9400GT
4GB ram

---

### Post by pssturges on 2009-06-01
> **jyavenard said:**
> 
So I start mythtv with:
  /usr/bin/xwit -root -warp 1920 1080
  /usr/bin/mythfrontend > /dev/null

Just tried this work around. Works great!

Just had to install xwit first.

Thanks
Phil

---

