---
title: "M-Audio Fast Track Pro &amp; ALSA recording issue"
date: 2011-01-08
forum: Multimedia Software
---

### Post by BattlePanic on 2011-01-08
I have recently been trying use my M-Audio Fast Track Pro usb sound card with Ubuntu and I am having problems recording audio input using this device.

I have tried doing a test recording with the following command:

```
arecord -f cd -D hw:1,1 test.wav
```

This usually works, and test.wav sounds fine on playback.  However, on some invocations, things will go wrong and the recording will be extremely loud and distorted even though I didn't do anything differently.  Further audio recording will remain distorted until I turn off the Fast Track Pro and turn it back on.  I'm not able to predict when this is going to happen but I'd guess that it happens maybe five percent of the time.

I've tested this on Ubuntu as well as Arch Linux and I've run into the exact same loud distorted recording in both cases.  Has anyone using a Fast Track Pro experienced this problem?  I'm not sure if this is a driver issue or an ALSA configuration issue.  Are there any ALSA gurus out there who have an idea of what might be causing this apparent bug?

---

### Post by cchhrriiss121212 on 2011-01-08
I'm no guru, but these things could be checked:
Varify your input source is OK
Try using another USB port - you could be getting interference from other devices on the same bus
Try something other than arecord, jack + timemachine or audacity

I have looked around and have not seen any similar issues, so I would not think this is a driver issue.

---

### Post by BattlePanic on 2011-01-09
Ok to start, I've disconnected all of my other external usb devices.

This time around I tried recording using audacity.  After working through some issues with audacity freezing I was eventually able to get it to record but with the very same problem.  The recorded input is sometimes loud and distorted and will remain so until the Fast Track Pro is reset.  I tried this under Ubuntu as well as Arch Linux and got the same results.

On top of this, another problem I'm noticing is that even when I'm able to record audio at a normal volume the recording quality is pretty bad.  I've been recording an electric guitar signal straight into the device and there is a noticeable hiss when playing the guitar, it doesn't persist when I'm not playing anything.  I tested the Fast Track Pro under windows and I'm not getting this hiss when recording using Sound Forge.

The fact that I can only hear this hiss on top of audible sounds suggests that it isn't due to environmental noise but rather some sort of digitial distortion.  To my ears it sounds like the signal is being recorded at a low bit depth.  I noticed this when recording both in audacity and arecord.  For arecord, I know that I passed the "-f cd" parameters which should mean that it records at a 44.1kHz sampling rate and a bit depth of 16 bits.

The Fast Track Pro has been on the market for a few years now so it's surprising that I haven't seen any posts describing similar problems.  Any other ideas?

---

### Post by cchhrriiss121212 on 2011-01-09
It seems like a system config thing to me, but I wouldn't know where to start. I'd recommend starting a thread here:
[http://www.linuxmusicians.com/viewforum.php?f=6&sid=aaf75912cb12da1a42f2bf0e862fb58b](http://www.linuxmusicians.com/viewforum.php?f=6&sid=aaf75912cb12da1a42f2bf0e862fb58b)
I have seen similar issues posted on this forum and most of the users will know more than I do about how to isolate the issue. 

Good luck with it, I don't think this will be a simple fix.

---

### Post by BattlePanic on 2011-01-09
Thanks for the pointer to the other forum.

As for my two issues, I'm beginning to think they are actually variations on a single problem.

As it turns out, the hiss I've been hearing only shows up on some recordings.  I did some more testing, and this time around I only used audacity for my test recordings.  I'm finding that after resetting the Fast Track Pro, my recordings sound clean, but it is only a matter of time before either one of two things happens:

- Recordings become extremely loud and distorted.
- Recordings sound like they were recorded in 8-bit.

In both cases the problem persists until I reset the device.  I can't predict when this will happen, but I do notice that if I switch the playback device in audacity's preferences between each recording, it seems to greatly increase the chances that either of these problems will occur.

I'm by no means an expert on digital audio, but both of these problems seem to somehow involve the issue of bit depth.

---

### Post by tjajab on 2011-03-21
Hi,

did you find any solution on this issue?

---

### Post by BattlePanic on 2011-07-30
tjajab,

I still haven't arrived at a solution to my issues although I've come across some resources which may prove helpful.  Are you a Fast Track Pro user as well?  I've yet to come across another user reporting similar problems.

Code exists to enable recording at higher bit depths and sampling frequencies but you must patch the ALSA driver.  I'm not interested in enabling 24bit recording, but it's possible that this patch corrects some issues at lower bit depths.  I have yet to test this.

The patch in question is available, linked from the [unofficial ALSA wiki]("http://alsa.opensrc.org/M-Audio_FastTrack_Pro").

There's also [Joe Giampoli's Blog]("http://webcache.googleusercontent.com/search?q=cache:9TMkDCRMj3MJ:www.joegiampaoli.com/blog/%3Fp%3D462%26replytocom%3D406+joe+giampaoli+blog&cd=4&hl=en&ct=clnk&gl=au&source=www.google.com.au") (that's the google cache version), which provides a HOWTO on applying this patch.  Joe's blog seems to no longer be available and I'm not sure how long this page will be kept in google's cache.  I've made a local copy of his guide for my own reference and I can send it to you if you are unable locate a copy online.

---

### Post by joegiampaoli on 2011-08-29
Here's the new link if you are still looking for it...

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html]("http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html")

---

### Post by noisemaker? on 2011-09-24
i have tried to apply this patch? i have now a m-audio-fast-track pro.conf file in the modprobe.d Verzeichnis, but in qjackctl there is no device number 5 or anything like that

---

### Post by noisemaker? on 2011-09-24
i have now the fkn hw5 entries in jack, but still the jack server dont start... ihave choosen the exact same settings as on the screenshot.. i still can only open up 2 playback channels but no input and no 4 outs ore what ever, the only diffrent is, before patch the card was shown as hw:1 and now as hw:5 but the problem ist still the same

---

### Post by joegiampaoli on 2011-09-24
What happens if you power down the FTP, issue the following commands:

```
[B]modprobe -r snd-usb-audio
sudo modprobe snd-usb-audio[/B]
```

and then power the FTP up again?

---

