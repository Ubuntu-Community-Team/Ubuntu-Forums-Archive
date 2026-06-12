---
title: "Can't kill pulseaudio."
date: 2010-05-04
forum: Multimedia Software
---

### Post by mgroat on 2010-05-04
I've always had issues with getting my USB headset to work with skype.  Under 8.04, I was able to kill pulseaudio, then launch Skype and everything would be good.

Lucid Lynx won't let me kill pulseaudio, though.  I've tried killall and I've tried kill - 9; in both cases a new pulseaudio process starts as soon as I kill the old one.

I found guides that suggest replacing pulsaudio with esound, but I don't think I need to go that far.  I just need to not have pulseaudio running when I launch Skype.  My current fix is:

```

sudo apt-get remove pulseaudio
killall pulseaudio
skype
sudo apt-get install pulseaudio

```

Is there a better way?

---

### Post by kostkon on 2010-05-04
The latest version of Skype works just fine with PulseAudio. You only need to install the *PulseAudio Device Chooser* utility and in the pulseaudio volume control send the audio stream of Skype to your USB audio device. PulseAudio will remember your choice from now on.

---

### Post by matteosistisette on 2010-07-06
Hi,

I am interested to the original problem which is "how to kill pulseaudio" and which did not get answered (wonder why it was marked as "solved").
I understand the original poster just wanted to use Skype and has been able to do that without killing pulseaudio, but his question how to kill pulseaudio was not solved.
I need to kill pulseaudio without uninstalling it.

I tried with
pulseaudio -k
which according to documentation should kill the pulseaudio server, however it doesn't do anything, nor even print an error message. Maybe another server starts as soon as I kill the first one just as the original poster describes? If so how do I avoid that?

---

### Post by Yellow Pasque on 2010-07-06
Yeah, pulse autospawns. You can use pasuspender (man pasuspender) to "pause" it, or you can set autospawn=no (either create a ~/.pulse/client.conf for your user, or uncomment the autospawn= line in /etc/pulse/client.conf).

---

### Post by matteosistisette on 2010-07-06
Thank you!!

Now this thread is really SOLVED :)

---

