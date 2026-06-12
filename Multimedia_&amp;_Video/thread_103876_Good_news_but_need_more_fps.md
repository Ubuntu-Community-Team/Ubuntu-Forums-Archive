---
title: "Good news but need more fps"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by nalmeth on 2005-12-14
I just installed breezy i386 on my EM64T, and automatically detected and setup was the i810 driver. I have 3D-accel support, but fps are not spectacular, and I think my hardware should give better performance.

I have heard in other posts, and especially for intel cards, that sometimes very low ram is allocated to the graphics card, causing low fps and other problems (running scorched3D crashed my system!).

Can anyone tell me where I can change how much ram is allowed to the graphics card? or if there might be another way to boost fps?

Thanks all

---

### Post by Sutekh on 2005-12-14
Firstly fps - from glxgears? - is hardly reliable.  How do things run graphically?  Do screensavers look good and run smooth?? How about scrolling large windows of text, or opening lots of windows and dragging them around?? If that looks good to you, then don't worry about your fps... seriously.

You could always try a different kernel to see if it things look better too.

---

### Post by nalmeth on 2005-12-14
Only 3D fps are suffering. Everything else is fast and smooth in 2D :smile: 
I had an ATI driver installed before that ran scorched3d, and ran billiardgl and foobillard just as well.
I think there must be something wrong when the proper driver is not operating as well as the wrong driver..
Since I have heard of other people having ram related graphics problems that is all I can really think of as a problem. 
Of course I'm open to anything

Here are my computer specs:
3GHz pentium 4 with hyper-threading
Gigabyte motherboard, built-in Intel 915GL / ICH6 128 mg graphics card
512 meg RAM

---

### Post by Sutekh on 2005-12-14
So you're saying that the wrong driver works better than the proper one?  Bizzare.

Anyway your specs look like they should be great.

I don't know anything about the RAM issue you mentioned.  Isn't that the reason why video cards have their own RAM, so that graphics don't need to use the system RAM?

---

### Post by nalmeth on 2005-12-14
Yeah, from what I've heard that should be true, but with built-in graphics cards, sometimes the card gets little or no ram. I don't exactly know why.. But I'm certain I've read posts from people who have found that only 1 meg of RAM was alloted to the graphics card!
I'm going to try to dig up those old posts and see if they can shed any light.

---

### Post by Sutekh on 2005-12-14
1 meg? That's so strange!  Hope you find what you need.

---

### Post by Sutekh on 2005-12-15
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards")

"Intel i915G Chipset: 2D - Yes, 3D - No"

:(

---

### Post by nalmeth on 2005-12-15
3d - NO
that is also weird. Maybe that was just for Hoary, or I hope at least.
With the i810 driver, 3ddesktop works, and it never has before, but as I said other 3d apps (including OpenGL ones) are pretty choppy.

---

### Post by nalmeth on 2005-12-15
the billiard games are running well now, but when the 3D is too hardcore, the graphics sort of wimp out..
My card should be able to do better than this.

Well I am happy at least that its basically working now! 
And it was 'out-of-the-box' too. :D

---

### Post by localzuk on 2005-12-15
The place to look at video memory assignments is in the BIOS of your motherboard. It will be somewhere under 'Shared Memory' or 'Video Memory' or similar.

Also, please post your /etc/X11/xorg.conf file so we can have a look at it.

---

