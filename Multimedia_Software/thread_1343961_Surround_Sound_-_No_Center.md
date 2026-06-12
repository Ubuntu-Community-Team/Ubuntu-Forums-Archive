---
title: "Surround Sound - No Center"
date: 2009-12-02
forum: Multimedia Software
---

### Post by Neremor on 2009-12-02
Hello!

I was trying for the last two months now to get surround sound working in Ubuntu. So I've done almost everything that can be done relating to sound configuration. So here are first

**Some Facts:**

[LIST]
[*]I've a 5.1 Sound System (2x Front, 2x Rear, 1x Center, 1xLFE)
[*]I've an onbard sound card which should support 5.1 sound, but it does so only on windows (there it works perfectly :D)
[*]I've an PCI-Card (by C-Media) which supports 5.1 sound for sure
[*]I'm using PulseAudio as soundserver (I've set the default channels to 6 off course)
[*]Alsa is routing it's input to pulseaudio
[*]As OS I'm using Kubuntu, but I think (except for KMix) this isn't important for my problem
[/LIST]
And now to my problem: I completly gave up to configure the onboard soundcard. Now I try to configure the PCI-Card. I have the front and rear channels working perfectly allright, but the Center speaker isn't addressed by Ubuntu. The Soundcard has four output-jacks:

**1xRear, 1xFront, 1xLine-In, 1xMic-In**

Off course front and rear are working, because they have their own output. But now we come the problem-part: I made KMix show me the channels I have for the soundcard (based on the alsa PCICMI-driver). There is a channel through which I can select how to handel line-in and mic-in. I can select the following:

**Line-In:**

[LIST]
[*]Line-In
[*]Rear Output
[*]Bass Output
[/LIST]
**Mic-In:**

[LIST]
[*]Mic-In
[*]Center/LFE Output
[/LIST]
I plugged the cable for "center/lfe" into the Mic-In slot on my soundcard and set the mode to "Center/LFE Output". But i just hear nothing from the center speaker (by the way, the subwoofer (lfe) isn't that important because it is working hardware-based all the time). So i tried as alternative to Plug-In The Center/LFE-Cable into the Line-In jack and set the mode to bass-output. Then I hear the LFE-Output on the center speaker (this tells me that it isn't impossible to get the center speaker working in ubuntu :))... But I just don't know how it isn't working with the Mic-In jack set to "Center/LFE Output"...

I know this is a bit complicated, but I just don't know what else to try. I don't want to spent another few weeks configuring without any result, then i would have to use Windows. Windows isn't bad (there is everything working), but I would really like to keep using Kubuntu... So thanks a lot in advance for every help!

Greetings,
Jonathan

P.S.: Please excuse my bad english, I'm from Germany and still learing english in school.

---

### Post by Pauly BC on 2009-12-02
Try launching alsa mixer from terminal. When you load that little program you find more options for control than via the settings window. You may find the center LFE output is muted.

---

### Post by Neremor on 2009-12-02
I've done this right now many times before. The Problem is: Neither in Alsamixer nor in KMix (which is at least the same I think) are any channel-proporties available. I can inly configure "Front", there is neither a rear- nur a center/lfe-volume-controler. Any off course I unmuted all channels which have something to do with sound output. So that is not the problem. I thought about the following:

Is it possible to make Pulseaudio send sound for the center-speaker to the bass speaker? because the center-speaker is handled as a bass-(/lfe-)output at the moment. This would only be a workaround, but it should do what i need...

I know this is possible via alsa, but how to do this via pulse?

---

### Post by Neremor on 2009-12-05
I could still need some help with this problem...

Or at least an advice for a cheap 5.1 soundcard which definitely works with kubuntu/ubuntu/alsa/pulseaudio, etc..

Thanks in advance,
Jonathan

---

### Post by alexfish on 2009-12-05
> **Neremor said:**
> I could still need some help with this problem...

Or at least an advice for a cheap 5.1 soundcard which definitely works with kubuntu/ubuntu/alsa/pulseaudio, etc..

Thanks in advance,
Jonathan
Hi
which version of Ubuntu are you using

 then may be I can narrow down to a few ideas  / seams you are almost there

configers well with pulse

   also I can recommend a cheap card/ alsa compliant   


added link to view cheap sound card / ensure it is a CM8738 version  with 5.1 sound

[http://www.tomshardware.com/reviews/entry,495.html](http://www.tomshardware.com/reviews/entry,495.html)

---

### Post by Neremor on 2009-12-09
First, thanks for the answer :)

My System is: Kubuntu 9.10 with KDE 4.3.4

I would prefer not to buy a new soundcard... But my soundcard looks very similar to the one you suggested me via the link above...

It's a C-Media PCI card, CM8738, but it doesn't look exactly like the one on the picture...

Greetings,
Jonathan

---

### Post by alexfish on 2009-12-15
> **Neremor said:**
> First, thanks for the answer :)

My System is: Kubuntu 9.10 with KDE 4.3.4

I would prefer not to buy a new soundcard... But my soundcard looks very similar to the one you suggested me via the link above...

It's a C-Media PCI card, CM8738, but it doesn't look exactly like the one on the picture...

Greetings,
Jonathan

Hi

 Your sound card id looks OK

This is an easy way to set up pulse

[http://ubuntuforums.org/showthread.php?t=1353851](http://ubuntuforums.org/showthread.php?t=1353851)

Check it out / Most of the configs and settings can be done from / from pulse Audio Device Chooser

 Its done Visually with screen shots so Fairly easy if a problem then post there

---

