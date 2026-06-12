---
title: "Video chat through Gmail - no mic on camera"
date: 2011-05-25
forum: Multimedia Software
---

### Post by stevovets on 2011-05-25
So, after screwing around a bit, i successfully managed to video chat through GMail with my HP KQ246AA webcam.  I can see the other person perfectly, and they can see me.  However, their microphone is working but mine won't at all.

I went through the Webcams Troubleshooting page on the wikiUbuntu site:
**"6. Fixing Audio problems with USB webcam**

 I installed a Logitech webcam Pro 9000 on a new Karmic/9.10 32bit install. Video worked "out of the box" but there was no audio. After hunting around for a while, I remembered how I had a similar problem trying to get digital audio out over hdmi on another 9.10 box.   The problem was that the alsa settings (not visible under pulseaudio) had the IEC958 device muted (silly setting if you ask me!). 
Anyway, I took the following steps to getting my webcam audio to work: 

[LIST=1]
[*]start a terminal window/xterm window 
[*]type: sudo alsamixer 
[*]using the tab key, make sure to be either in "all" or "capture" mode 
[*]using the left/right arrow key, navitage to the correct "slider" 
[LIST]
[*](I'm not sure if the right one was front mic (left/right) or just plain "mic"  or Mic Boost but I enabled them all) 
[/LIST]
[*]if the value at the bottom of the slider says "M" then your device is on "mute" - Hit the "m" key to togger the mute / un-mute 
[*]using the up/down arrow, adjust the setting to get as much green as possible w/o getting in the red zone. 
[*]repeat for all lables that look like "mic", "front mic" "Mic Boost" etc... 
[*]exit alsamixer 
[*]test  your audio.  I installed Cheese to do a quick audio/video recording  test but you can also test with "sound recorder" or the skype test call  etc... 
[/LIST]
That should do it!" 

...But that didn't do it.  I tried basically every combination of muting and unmuting, switching channels, things of that nature.  Nothing seems to get it.  Does anyone have any other suggestions?

PLEASE!?

---

### Post by IWantFroyo on 2011-05-25
Open a terminal and just type 'alsamixer' without the sudo.

Hit f4 (capture) and bring it all the way up.

Let us know if this fixes it! Good luck!

---

### Post by stevovets on 2011-05-25
eeh, no dice on that :-k

---

### Post by IWantFroyo on 2011-05-25
Does Jockey (Additional Drivers) bring anything up?

---

### Post by stevovets on 2011-05-25
nope, doesn't list anything

---

