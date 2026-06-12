---
title: "Trying to connect my Sansa mp3 player."
date: 2009-10-10
forum: Multimedia Software
---

### Post by Zerocool10482 on 2009-10-10
I used an older version of ubuntu to sync with my Sansa. Now with the new one. I have no MTP support of any kind. Ubuntu 8.04 had it working out great. What happened to it?

Tried Rhythmbox, Songbird and installing MTP again. HELP!!

---

### Post by sgosnell on 2009-10-10
Can you access the files from Nautilus?  If not, are you sure the Sansa is set to MTP mode?  My Fuze has a setting to select which mode it uses, and the default should be autoselect, but it may be set to MSC.

---

### Post by RollerJ on 2009-10-11
This is from the Rhythmbox 0.12.0 help contents

If Rhythmbox Music Player do not detect your device as
    an portable audio player, you can create an empty file
    .is_audio_player at the top level hierarchy of the
    filesystem of your player.

I have a Sansa Clip plus. That is how I  got it working with Rhythmbox and Jaunty.
Make sure the file name is exactly: 

.is_audio_player

---

### Post by HDave on 2009-10-24
WOW -- thanks so much for this tip...worked like a charm.  Hey OP -- you should mark this thread as "solved"...

These kinds of regressions are really killing me....

---

### Post by sgosnell on 2009-10-24
BTW, there is newer firmware available for both the Clip and Fuze.  You can download it from the SanDisk website, and install it on your player.  Older versions don't allow selecting the USB mode, and there are other enhancements included.

---

### Post by LisaO on 2009-10-31
After installing ubuntu 9.10 my Sansa Clip stopped opening up on the desktop and in RhythmBox too. I was able to get it to show up in RhythmBox finally by checking a plugin's checkbox for mtp but I liked loading it by opening a folder of music and dragging and dropping.

I found my answer in a post on the net. My Sansa Clip has the settings menu he spoke of in the article and it worked just like he said it would. I can now drag and drop music both ways again from computer to sansa clip and sansa clip to computer. I can do likewise in RhythmBox too just like I used to do.  [http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)

---

### Post by Zerocool10482 on 2010-01-11
Thanks for the help but I've been really mad at the new release of Ubuntu. I really hate it. I haven't really used it in months. That's why I didn't see your replys. Sorry. But I'm really waiting for a new release or something else.

---

### Post by Arazu on 2010-01-12
> **Zerocool10482 said:**
> Thanks for the help but I've been really mad at the new release of Ubuntu. I really hate it. I haven't really used it in months. That's why I didn't see your replys. Sorry. But I'm really waiting for a new release or something else.

I'm getting a little more than upset as well. I was finally able to get my Fuze to show up by switching the USB mode to MTC. It shows up fine but IT'S READ ONLY!!! *face head desk*

I'm seriously considering dropping back to 8.10 as I'm not liking many things about 9.10.

---

### Post by sgosnell on 2010-01-13
9.10 is an anomaly, I think.  9.04 works well, as does the alpha release of 10.04, but 9.10 seems to have been rushed out, and has many problems.  I'm skipping it, and will probably upgrade from 9.04 directly to 10.04.

---

### Post by Arazu on 2010-01-13
> **sgosnell said:**
> 9.10 is an anomaly, I think.  9.04 works well, as does the alpha release of 10.04, but 9.10 seems to have been rushed out, and has many problems.  I'm skipping it, and will probably upgrade from 9.04 directly to 10.04.
I didn't spend much time with 9.04 but it seemed to work pretty well for me while I used it. I think I'll try that before reverting to 8.10. Perhaps I should stick to the x.04 releases. They seem to work better.

I can't remember if I actually used my Fuze with 9.04. It's been a long time since I wanted to change media. I guess we'll see.

BTW: "Out of the box" 9.10 wouldn't even play my music. I had install other GStreamer plugins. 8.10 played it right away.

I'm also having flash trouble on websites. But, that's another topic.

I agree, 9.10 seems more than a little borked. I'm going to revert tomorrow night.

P.S.: "Safely Remove Device"??? Did I just boot a Windows system? Now I have no clue if I should "Eject", "Unmount", or "Safely..." =|

---

### Post by sgosnell on 2010-01-13
Unmount works for me.  There is a long thread on that subject on this forum, and I'm not sure a consensus was ever reached.

---

