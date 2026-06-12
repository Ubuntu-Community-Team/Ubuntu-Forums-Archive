---
title: "VLC Closes unexpectedly"
date: 2009-09-30
forum: Multimedia Software
---

### Post by sbelz79 on 2009-09-30
When I am watching videos in VLC (version 0.9.9a Grishenko), the player closes unexpectedly.  Its closing is usually associated with an event such as maximizing or manually resizing the window.

I'm running Ubuntu 9.04 on a machine with a 2.0 GHz AMD Athelon XP 2400+, 1 GB of RAM, and an ASUS V7100 PRO 32-bit video card with 128mb of RAM and an nVidia GeForce MX 400 GPU

---

### Post by ajgreeny on 2009-09-30
You suggest that you have two graphics cards, or perhaps you mean that the ASUS card has an nvidia chip.

If you do really have two cards available, I suggest you disable one of them in the BIOS if possible, as it may be that the system is being confused by the hardware choice in some way.

---

### Post by sbelz79 on 2009-09-30
> **ajgreeny said:**
> You suggest that you have two graphics cards, or perhaps you mean that the ASUS card has an nvidia chip.

If you do really have two cards available, I suggest you disable one of them in the BIOS if possible, as it may be that the system is being confused by the hardware choice in some way.

Sorry, my wording wasn't too clear.  My ASUS card has an nvidia chip.

---

### Post by andrew.46 on 2009-10-01
Hi sbelz,

> **sbelz79 said:**
> When I am watching videos in VLC (version 0.9.9a Grishenko), the player closes unexpectedly.  Its closing is usually associated with an event such as maximizing or manually resizing the window.

Have you tried changing the video output device to something other than default? Often sudden closure of programs like vlc or MPlayer is related to innapropriate video or sound settings. I attach a screenshot to illustrate the section in the preferences that I am referring to. Although I am using a different version of vlc there will be a similar setting in your copy.

All the best,

Andrew

---

### Post by sbelz79 on 2009-10-01
> **andrew.46 said:**
> Hi sbelz,



Have you tried changing the video output device to something other than default? Often sudden closure of programs like vlc or MPlayer is related to innapropriate video or sound settings. I attach a screenshot to illustrate the section in the preferences that I am referring to. Although I am using a different version of vlc there will be a similar setting in your copy.

All the best,

Andrew

How do I know the right output setting?

---

### Post by andrew.46 on 2009-10-01
Hi sbell,

> **sbelz79 said:**
> How do I know the right output setting?

I suspect that you should get best success with the x11 video output, otherwise trial and error will probably have to be your guide I am afraid.

Andrew

---

### Post by sbelz79 on 2009-10-01
> **andrew.46 said:**
> Hi sbell,



I suspect that you should get best success with the x11 video output, otherwise trial and error will probably have to be your guide I am afraid.

Andrew

I tried x11 and wasn't able to get it to fail.  Thanks- I hope it keeps working.

---

### Post by andrew.46 on 2009-10-01
Hi sbelz,

> **sbelz79 said:**
> I tried x11 and wasn't able to get it to fail.  Thanks- I hope it keeps working.

Great news! 

Andrew

---

