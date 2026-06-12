---
title: "remove microphone noise"
date: 2014-04-28
forum: Multimedia Software
---

### Post by contremaitre on 2014-04-28
Hi,

I have noise when I record my microphone, using skype, arecord, or others software.
On the same hardware, I have the same noise on windows if I uncheck the noise removal option.
But I would like to be able to supress this noise on linux too.

```
lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

```

Thanks

---

### Post by tgalati4 on 2014-04-28
Is this a laptop or desktop?  If a laptop, try recording when on battery and see if the noise changes.

Is the noise high frequency hiss?  Open a terminal:

```
alsamixer
```

Hit F5 to view all channels.  See if there is a noise reduction switch.  It's possible that it is labeled "microphone boost", which will raise the pickup sensitivity but also raise the hiss noise.

---

### Post by contremaitre on 2014-04-28
It's a desktop.
I don't know what you mean by high frequency hiss?
I already tried to play with microphone boost and all other sound settings.
Mic boost raises the volume and noise, There is no settings where I have a good sound without noise.

---

### Post by tgalati4 on 2014-04-28
High frequency hiss sounds like white noise or a high-pitched squeal.  Low frequency noise would be hum (typically 50 or 60 Hz AC line noise).  What kind of microphone are you using?  Most sound chips supply 3 to 5 VDC on the microphone port to power up a dynamic microphone.  If you are using a cheap, passive microphone, then you will get noise pickup from the wire that connects the microphone to the computer.

It's not clear to me what the Windows driver is doing with "Noise Reduction" enabled.  This is typically a high-cut filter--cutting out 10 kHz and above to reduce the high frequency noise that cheap microphones tend to generate.

The Intel sound chip is OK for sound recording, but the microphone is key to recording quality.  Of course, internal routing of the wires to the microphone port could contribute to noise.  Check how the wires are routed and move them around.

---

### Post by contremaitre on 2014-04-29
Thanks for your help.
It will be more clear with a short sample, recorded with arecord :
[http://www.celeos.eu/tmp/test_linux.wav](http://www.celeos.eu/tmp/test_linux.wav)
This first seconds are with the microphone plugged, then the microphone unplugged, and at the end plugged again.
The noise is a little louder without the microphone, so it seems the issue is not the microphone, but my integrated audio chipset which get interferences.
Then a test sample on windows, the first seconds with noise filtering then without noise filtering :
[http://www.celeos.eu/tmp/test_windows.wma](http://www.celeos.eu/tmp/test_windows.wma)
So I think the only solution would be to have a noise filtering like on windows.

---

### Post by contremaitre on 2014-05-07
Any idea ?

---

### Post by contremaitre on 2014-05-26
still looking for a solution to this

---

### Post by contremaitre on 2014-09-08
Ok there is a solution.
It requires to recompile pulseaudio because of this bug :
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1261666](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1261666)
A tutorial to do it : [http://askubuntu.com/a/497559/270301](http://askubuntu.com/a/497559/270301)
Then it requires to do a little trick to enable noise cancellation on mic input. Bug details and trick here :
[https://bugs.freedesktop.org/show_bug.cgi?id=83557](https://bugs.freedesktop.org/show_bug.cgi?id=83557)

Hope all of this will be fixed and available by default

---

