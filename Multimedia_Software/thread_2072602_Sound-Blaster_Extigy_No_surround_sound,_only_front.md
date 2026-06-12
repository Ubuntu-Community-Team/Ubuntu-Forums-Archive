---
title: "Sound-Blaster Extigy: No surround sound, only front left and right"
date: 2012-10-18
forum: Multimedia Software
---

### Post by NHerby on 2012-10-18
Hi,
I have a sound-blaster Extigy sound card with a 5.1 sound system.
For info, the extigy is an external USB sound-card, AC3 and Dolby Digital compatible and coming with an IR remote control. One of the very interesting feature of this card is the ability to work even without the computer. I have my TV (line-in) and a DVD player (S/PDIF coaxial in) attached to the card and, thanks to the remote control, no need to fire up the computer to control the sound card.

I think I have the problem described in this _[COLOR=DeepSkyBlue][bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/518966") [/COLOR]_when I try to use the 5.1 analog output. Anyway, I just need the S/PDIF input, I don't want to use the analog 5.1 on this card but I'm surprised to see that this bug is still there 2 years after.

Since this card works nicely with S/PDIF, I want to use this option for stereo music (from Amarok) and surround sound (from XBMC). For Amarok, I simply select "Stereo analog (IEC958 )" in pulse audio volume control and voila.
In XBMC, I use a custom audio output: hw:Extigy,2 for both stereo and AC3 pass-through. With stereo content, no problem. But with AC3, there is no sound coming out from the rear and center speakers. Only front left and front right are working. There is a LED on the sound-card that lights up whenever a valid AC3 signal gets in and this light comes on so I assume that the audio setting in XBMC is right and the correct signal is sent to the card.

One interesting thing: I made some test with my DVD player. It sends AC3 in the Extigy through a coaxial cable. In this situation, the surround sound works _if the computer is off_. As soon as I switch on Ubuntu, the rear and center speaker stop working and I have to unplug the USB cable or switch off the computer and reset the sound-card (unplug AC adapter and plug back) to get surround sound back.
I made the same test with the optical connection and had the same result.
I did the same test but made my computer boot on a live CD instead of the installed OS and the surround sound from the DVD was still working.

In short, as soon as I plug the sound card in the computer, the 2 rear speakers and the center speaker get muted (or mixed with the front right and left, I dunno exactly).
I've tried many troubleshooting tutorials and spent tons of hours trying to solve this issue, without luck so far.

I also made the alsa-info-script to provide detailed information and attach the result to this post.

---

### Post by NHerby on 2012-10-21
I bump up this thread!
I still cannot find a fix; just made a little step forward:
I made a few test on a freshly installed Ubuntu on the same computer and found that the sound was working perfectly (including the AC3 pass-through) until the installation of LIRC. Once LIRC installed, the same problem comes back and, even after completely removing LIRC, I cannot get the sound working normally anymore. 
LIRC uses the alsa_usb driver as described [here]("http://www.lirc.org/html/alsa-usb.html").
On the last test I made, I even didn't set up LIRC to use the alsa_usb driver. Despite that, the surrond sound disappeared again.
So now, how can I build on this finding? Is there an alternative to LIRC? A place to report this issue to LIRC's developers?

---

### Post by gtippitt on 2012-12-19
The Extigy won't work with 5.1 since PulseAudio replaced OSS in Ubuntu distro.  

For more info, see link below:

[http://ubuntuforums.org/showthread.php?t=1322828]("http://ubuntuforums.org/showthread.php?t=1322828")

---

### Post by NHerby on 2012-12-19
Thanks for the input.
However, I gave up with the extigy. I still use it but it is not plugged to the computer via USB anymore.  I now use an optical cable to pass the sound from my internal soundcard to the extigy. I also use another soundcard (X-Fi 5.1) as IR receiver. The setup is a bit complicated but it works.
What you say sounds a bit strange since, as said in my previous post, I managed to get it work (including 5.1 & AC3 pass-through) until I installed LIRC.

---

