---
title: "Skype incoming video is white"
date: 2012-01-03
forum: Multimedia Software
---

### Post by habdien on 2012-01-03
Hi all,
 
Seems like the linux community is facing issues with skype.
 
Ok  my issue after solving all the usual problems is that I am getting a  blank/white image from the other side when I am using video.
 
My  cam works fine, I see myself, others can see me, al is ok on my side,  on the other side, my friends can see me, see themselves normally, but I  see only white white screen. is it a happy new year thing?
 
I  am using a Fujitsu-Siemens scenic N320 with AMD 64 bit Athelon  processor and OS is Ubuntu & Debian (32 bit + 64 bit), I tried it  with all that...

---

### Post by xc3RnbFO8P on 2012-01-03
Try in Terminal:
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

---

### Post by ExemplarUbuntu on 2012-01-03
I have had this problem for about 18months, the incoming video is not being rendered, just a white box replaces the static icon image of the sender.

I've tried everything. Updates, fresh installs, all manner of patches and bodges and nothing works.

It's the same story with Pulseaudio, which hogs about 40% of the cpu.  The only thing to do is remove it and install Alsa which at least allows the audio to work normally.

---

### Post by mörgæs on 2012-01-03
Considering the new owner I doubt Skype for Linux will ever get past beta stage. 

Have you looked into alternatives, for example Google Talk?

---

### Post by scubascooby on 2012-01-05
I've had to change my username due to a change of job, I am no longer ExemplarUbuntu, now Scubascooby.

I have been using skype because many friends and family use it but I am now going to try a SIP client like Ekiga or Empathy.

I am not clear which services support video calls with these clients but I hope it does at least provide a solution. I used to use Yahoo for IM but I gather their video protocol is proprietary too.

---

### Post by Iowan on 2012-01-09
> **scubascooby said:**
> I've had to change my username due to a change of job, I am no longer ExemplarUbuntu, now Scubascooby.Ordinarily, that's done with a request in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") for a name change - or account disable. I've disabled ExemplarUbuntu for you.

---

### Post by scubascooby on 2012-03-04
Not what I wanted, I would much rather someone fixed Pulesaudio. I daresay my old colleagues will be puzzled. Resolution Centre is a strange name.

---

