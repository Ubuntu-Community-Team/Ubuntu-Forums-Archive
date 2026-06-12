---
title: "alsa/pcm problem with signalink"
date: 2009-05-04
forum: Multimedia Software
---

### Post by jcblacker on 2009-05-04
I'm using a signalink usb in ubuntu 8.10 and everytime I try to send something to my device I get the error:
snd_pcm_writei: file descriptor in bad state
I'm using Tom Sailer's soundmodem to emulate a tnc and xastir for aprs display.  When xastir transmits (or attempts to) I get the above error - lots of times.  I have soundmodem configured to use alsa at plughw:1,0 and everything works fine when I test PTT from soundmodem; but xastir transmit produces the above errors.  I don't know what to do next.  I tried both the binary distribution of xastir and also rebuilt it from the sources.
Can anyone shed any light on this or perhaps provide me with some steps to isolate the problem?  By the way, I use fldigi and it works just fine...no errors whatsoever.
 
Thanks.

---

### Post by andrewc6l on 2009-07-02
I get the same issue - even when using the latest soundmodem (0.14?) instead of the version that comes with Ubuntu (0.10_2?) It's interesting that you don't see that except for on Xastir. I haven't tried anything except for Xastir, so I can't say if it's the same for me.

My next guess at something to try is to take ALSA out and just go direct to the soundcard if possible. I'm not sure how to do that, though... gotta do some googling.

---

### Post by NJ0E on 2009-07-05
Guys,  I don't use aprs, I do use FLDigi with the Signalink USB.  I found that yuou don't use the alsa -- use "dev0" this will use the soundcard onboard the signalink module.

Hope this helps.

Joe
NJ0E

---

### Post by andrewc6l on 2009-07-15
I just realized that Soundmodem 0.14 really does solve my ALSA transmit problem - I just wasn't running it :-( Now that I am, I can transmit without crashing the driver.

On the downside, -v5 no longer shows the packets as they come in - guess I need to hack it to see those again.

(There's a big difference between sudo soundmodem -v5 and sudo ./soundmodem -v5 :-) )

---

