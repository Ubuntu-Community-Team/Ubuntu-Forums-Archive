---
title: "FFMPEG - Transitions"
date: 2012-04-03
forum: Multimedia Software
---

### Post by Rhemat on 2012-04-03
Heya All,

I have been learning to use FFMPEG to create transitions from one video to another, except my web searching has shown that FFMPEG itself is not capable of such.  Are there some commands I'm missing, or is there something I can use to do a transition?

I would use graphical video editors, but they either do not work/install, do not provide the quality I need, or are heavily restricted by formats.

Thanks in advance.

---

### Post by evilsoup on 2012-04-03
FFmpeg isn't really made for this kind of thing. I'm not saying that it can't be done, but I'm sure it would be very complicated.

When you say transitions, you mean... cross-fading? Or something else? What graphical applications did you try?

If you haven't yet tried it, I'd recommend Cinelerra (which is the closest Linux has to a professional-level NLE at the moment). It's not in the repositories, but there is a PPA.

sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra

---

### Post by Rhemat on 2012-04-03
I had thought that might be the case.  I had seen a tutorial with vhooks (libim2), but I found elsewhere that it was deprecated.

I tried OpenShot again last night, and I was able to use it for transitions, without much fuss.

Cinelerra gave me issues, because it heavily restricted what formats I could export in (could only export sound, or video for MPEG4; wouldn't allow YUV for some reason; Quicktime slowed, and deepened the sound, resulting in some nightmare mix).

I do appreciate the help though.  Thanks.

---

