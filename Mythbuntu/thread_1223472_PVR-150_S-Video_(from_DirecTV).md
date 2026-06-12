---
title: "PVR-150 S-Video (from DirecTV)"
date: 2009-07-26
forum: Mythbuntu
---

### Post by dsbw on 2009-07-26
Hi, guys!

Just switched to a satellite receiver and am trying to get it going with my PVR-150. Right now it's hooked up via S-Video cable (no audio, haven't figured that out yet...) and if I do a:

cat /dev/video1 >whatever.mpg

I can play whatever.mpg with VLC. (Aspect ratio off of HD channels has to be manually set. Meh. But it looks pretty good!)

But I've set up /dev/video1 as a V4L capture and an IVTV MPEG2 Encoder, on both S-Video 1 and S-Video 2 with no luck. (There isn't an S-Video 2 but I figured I should try it.)

Not sure how to proceed. Any thoughts?:popcorn:

---

### Post by dsbw on 2009-07-29
Nobody's got nothin' on this? Nohow?

---

### Post by tgm4883 on 2009-07-29
Your PVR-150 needs to be setup as an MPEG device (not V4L), you will need to use a blaster to change the channel as well. Once that is setup (use S-VIDEO 1), if you are still having problems, post your /var/log/mythtv/mythbackend.log file after it fails.

---

### Post by dsbw on 2009-07-30
Pretty sure I've done all this, but yeah, let me try again.

---

### Post by dsbw on 2009-07-31
Damn. Worked just fine now. 

MPEG-2 IVTV and S-Video 1 input. Guess I hadn't hit that combination.

Now to change channels.

---

### Post by tgm4883 on 2009-07-31
Glad I could help.

---

### Post by dsbw on 2009-07-31
Not so fast there, TGM. Heh. It's intermittently working? It sometimes thinks there's two S-Video inputs? 

Error logs:

[http://mythbuntu.pastebin.com/f307b50](http://mythbuntu.pastebin.com/f307b50)

---

### Post by dsbw on 2009-07-31
OK, now it's working again.

lol

Let me see if it happens again and narrow down what's causing it.

---

### Post by dsbw on 2009-08-02
Stumped. Something is happening to stop the channel switching from even being attempted, and it doesn't alway tune when I start it up, either. Bleah!

---

### Post by tgm4883 on 2009-08-03
> **dsbw said:**
> Stumped. Something is happening to stop the channel switching from even being attempted, and it doesn't alway tune when I start it up, either. Bleah!

I won't really be available the next couple weeks, but if you let us know how you are changing channels, how you set it up and post any scripts you are using that would be great.

---

### Post by dsbw on 2009-08-08
I fixed it by deleting the tuners and re-doing them.

It worked, though the next time I rebooted the tuner went from video1 to video0. It seems to be holding there, though.

Thanks.

---

