---
title: "dvd::rip audio/video sync problem?"
date: 2009-06-24
forum: Multimedia Software
---

### Post by lotster on 2009-06-24
Hi!  I installed dvd::rip in Ubuntu Jaunty as an alternative for FlaskMPEG that I always used in Windows (I'm a recent Linux convert :o).  However, the AVI that I created of a DVD recently (no, I'm not pirating, it's a DVD I legally own and I'm allowed to back it up in South Africa) had the sound terribly out of sync.  I used the Xvid codec, with a sound  set at 128kbps and 44100.  Could someone please tell me what I'm doing wrong?

Also, I heard that I'm supposed to be able to convert dual-layer DVD's to the 4.2GB size using dvd::rip.  How can I do that?  I don't see the option anywhere...

Thanks in advance!

---

### Post by lotster on 2009-06-26
Someone? *Anyone?*

---

### Post by kusharan on 2010-01-13
have the same problem with the sync. backing-up another disk at the moment. will let u know the result. I want to check if it happens for all disks. if it does, hopefully it can be fixed by tweaking a setting. Will let u know if I discover a fix.

---

### Post by Domie on 2011-09-20
> **kusharan said:**
> have the same problem with the sync. backing-up another disk at the moment. will let u know the result. I want to check if it happens for all disks. if it does, hopefully it can be fixed by tweaking a setting. Will let u know if I discover a fix.

Some problem here...

---

### Post by Dale61 on 2011-09-21
If you are converting avi to DVD, install DVD Styler and give that a go.  It can be downloaded from the Software Centre.

---

### Post by aeiah on 2011-09-21
are you converting between framerates? if so, this could desync the audio, if you aren't also reencoding it properly

---

### Post by BicyclerBoy on 2011-09-21
This is **not very helpful** if you must use AVI for old DVD players but..

Don't use AVI containers for variable rate audio/video.
Don't use AVI container for out-of-order or B frame video encoding i.e. any modern video codec.

XVid (MPEG4-ASP) in an AVI works by many kludges to pack B frames to preserve presentation order.


If you want to backup DVD for personal/private use then consider MPEG4/10 AVC H264 in a mkv or MPEG4 container. This codec is well supported by video decode h/w.

IMO HandBrake is the most capable transcoding program.

---

