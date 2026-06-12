---
title: "Dell Inspiron 1526 - No Sound"
date: 2008-12-26
forum: Multimedia Software
---

### Post by VaguelySauntered on 2008-12-26
Hello all,

I recently purchased a laptop for school and installed Ubuntu 8.10.  Everything works great, except for my sound card.  No matter what I try, I can't seem to get it working.  I've been through all the "sticky's" and the forums trying to find the solution myself to no avail.  Here's some information:

> 
erica@EricaDell:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


When I run AlsaMixer, all the levels are at 100% and my sound preferences are all set to PulseAudio.  There's a screen shot of my audio configs attached to this post.  Any help would be greatly appreciated!

---

### Post by LegoAddict on 2008-12-26
It looks to be that 1526s are refurbished.  Did it have Windows installed previously and was sound working then?

And I'm just going to throw a random one at it, but have  you looked at the restricted drivers manager?

I have a 1525 running Intrepid x64 and sound worked no issue for me.  Only problem was wireless card which needed a prop. driver.  After that, no problem (except webcam).

On a completely unrelated note, is you webcam working under Ubuntu?

---

### Post by VaguelySauntered on 2008-12-30
Solved it...just needed a reboot after following the guide!

---

### Post by duanedesign on 2009-01-02
I am helping some onr with sound problems. What solved your problem, what is "the guide" that worked for you?

---

### Post by VaguelySauntered on 2009-01-03
duanedesign,

Here's [the thread]("http://ubuntuforums.org/showthread.php?t=205449") I was talking about.

VS

---

