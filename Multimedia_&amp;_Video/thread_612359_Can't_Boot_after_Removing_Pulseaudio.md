---
title: "Can't Boot after Removing Pulseaudio"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Aikon- on 2007-11-13
Hi everyone,

Recently I gave Pulseaudio a whirl since I've been hearing good things about it. So, I installed the packages and the configuration tools etc.

It took me a fair amount of time to even get sound working again, and once I finally did, there wasn't much difference in the sound from before (i.e. I couldn't tell the difference), except that now Amarok hangs when I pause music and I can't hear the audio in flash videos.

So, I decided to remove Pulseaudio. Apparently, this is not allowed; I went through synaptic and removed all the packages I had installed the previous day and then rebooted.

My system hangs about 30%, and just shows a blinking cursor in the top left corner of the screen.

**edit** I can't even tell what's going on at boot; if I remove the "quiet splash" from the boot command in grub, it doesn't display any text to me at all, just a black screen **/edit**

Any ideas?

-Aikon

---

### Post by Aikon- on 2007-11-13
OH WOW!!!

I don't think it /is/ PulseAudio related. Turns out, the problem was that my hard drives were having forced fsck checks based on number of times mounted. Because the boot text wasn't displaying (I finally got it to work.. apparently vga=791 doesn't work anymore, even though it used to), it appeared to me as if the system was just hanging. Sorry for bothering you guys.

--- Of course, I hope this is the problem.. I hope that once it runs the check and I reboot all will be well.

Aikon-

---

