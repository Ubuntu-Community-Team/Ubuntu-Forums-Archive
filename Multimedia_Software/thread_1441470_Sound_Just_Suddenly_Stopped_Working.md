---
title: "Sound Just Suddenly Stopped Working"
date: 2010-03-28
forum: Multimedia Software
---

### Post by stwstl5926 on 2010-03-28
This is bad. Very bad.

My sound seems to have just suddenly stopped working. I have NO idea what could have caused it to stop working, but I do know that I NEED sound in order to do my school work (I'm a music composition major, so sound is KINDA important to me). Everything in the ALSAMixer seems fine, and sound works perfectly when I boot up the Live CD. Any ideas?

---

### Post by paulrogers on 2010-03-28
Try in a terminal window:

killall pulseaudio

Then:
sudo alsa force-reload

---

### Post by stwstl5926 on 2010-03-28
> **paulrogers said:**
> Try in a terminal window:

killall pulseaudio

Then:
sudo alsa force-reload
Negative.

Here's something really strange, though. If I try running alsa-utils in the terminal, it says it doesn't exist. However, when I try to apt-get it, it says it's already installed.

EDIT: I found this because I was trying another solution which involved reinstalling that, not because I was trying to randomly run different audio-related things.

---

### Post by stwstl5926 on 2010-03-28
Ok, I've solved the problem... I have NO idea how this happened, but...

I went into the ALSAMixer again, figuring maybe I missed something.

I literally went through all the options, muting and unmuting, no matter how unlikely it seemed that that particular control was related. Problem solved, but also very strange.

---

### Post by weavermount on 2010-04-02
> **paulrogers said:**
> Try in a terminal window:

killall pulseaudio

Then:
sudo alsa force-reload

Hey recently had the OPs problem and your solution did work for me, so thanks. Mostly I'm writing just to let the internet know that it the solution *can* work

---

### Post by ericado800 on 2010-04-04
Thanks for posting this. Had the same thing happen to me. However paulrogers solution did it for me.

---

