---
title: "Hardy: M-Audio Transit"
date: 2008-07-19
forum: Multimedia Software
---

### Post by klss on 2008-07-19
Hi folks.

I got my M-Audio Transit to work under Hardy with the madfuload generic driver as I described over here. It needed a udev workaround to get it going.

[http://www.diyaudio.com/wiki/index.php?page=LINUX+Audio+MAudioTransit](http://www.diyaudio.com/wiki/index.php?page=LINUX+Audio+MAudioTransit)

After this it works in a default configuration mode.

Now. What I am really lacking is the knowledge of how to set the cards
parameters, such as buffersize, samplerate asf. for improving it's performance and changing certain modes. 
The actual host-application is just working under Windows.

Does anybody know how to tackle this problem?

Cheers
KLS

---

### Post by peterdines on 2009-02-12
Hi klss, thanks for the write-up on the udev workaround. Between that and disabling pulseaudio I finally got my Transit working nicely in Ubuntu.

I believe setting it up for different bit depths, sampling rates and buffer sizes will require use of the Jack server and qjackctl - at least that was my experience last time I took a run at audio in Linux. 

Now that I have the dang thing working at all, Jack's the next step for me, so I can start making some low latency noise.

---

### Post by soundcheck on 2009-02-19
> **peterdines said:**
> Hi klss, thanks for the write-up on the udev workaround. Between that and disabling pulseaudio I finally got my Transit working nicely in Ubuntu.

I believe setting it up for different bit depths, sampling rates and buffer sizes will require use of the Jack server and qjackctl - at least that was my experience last time I took a run at audio in Linux. 

Now that I have the dang thing working at all, Jack's the next step for me, so I can start making some low latency noise.

Hi there.

( I have been klss ;) ).  

The problem with the M-Audio is that there is no particular driver. It is using the standard snd-usb-audio driver. Thus only basic features are supported. There won't be any configuration options. Under Windows you can set different output modes (e.g. nr of channels) and
buffer. I think this is really needed to tweak  resp. strip down the config to e.g. stereo. Otherwise you might run into performance problems (Xruns)
 
Since the Transit is loading firmware on OS startup, you can't do the configs under Windows and then boot into Linux ( as it is possible with e.g. EMU 0404USB)
 

However. At least I got all supported samplerates running. 
 
Cheers

---

