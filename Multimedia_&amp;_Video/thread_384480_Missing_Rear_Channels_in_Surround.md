---
title: "Missing Rear Channels in Surround"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by Kubular on 2007-03-14
I'm new to linux/ubuntu use the Karajan audio module/card that came with my DFI nForce 4 motherboard. I [COLOR="Red"]can[/COLOR] get sound out my rear speakers when I dublicate the stereo signal through ALSA mixer, but I don't get the rear channels when I'm running apps like Quake4. 

I have to admit that Quake4 is the only surround source I've tried atm, I haven't tested any DVDs... though I guess that could raise plenty of questions on it's own. I've been reading tutorials and FAQs for the last couple of days and I have to admit I've lost track of what I have and haven't done. I'm tempted to reinstall just to make sure I'm back to defaults. :P Though I'd rather not. ;)

Oh, my audio card is being reported as Realtek ALC850 rev 0 through the GNOME ALSA Mixer, I've been assuming that's right... Another thing I should point out that I've jsut thought of is that I don't actually now that Quake even works properly in windows with this device. I use my X-Fi Elite Pro usually, I had to stick the Karajan card in especially for my ubuntu install. Which I did _before_ my install, just to make sure it detected everything as defaults.

Sorry if none of this makes sense, I'm coming down off a coffee high. I'll link some of the tutorials I can remember flicking through, if there's anything else that might be handy let me know. 

Btw, when I tried [B]speaker-test -Dplug:surround51 -c6 -l1 -twav
[/B] 
I got this:
Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5461
Periods = 4
was set period_size = 5461
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Input/output error
Setting of swparams failed: Input/output error

Thanks for your help anyway.

:)


**Some tutorials/threads I've scanned over/used:**

[http://www.ubuntuforums.org/showthread.php?t=381076&highlight=alsa+sound](http://www.ubuntuforums.org/showthread.php?t=381076&highlight=alsa+sound)
[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)
ttp://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA

I've prolly kept doing the same things over and over again. I'll keep fiddling and if I fix it I'll post. 

Thanks again though.

---

### Post by kipriano on 2007-03-24
Hello all, 
I also am quite new in ubuntu. i have a similar problem. my soun dcard doesn't work properly. my surround sistem is working in stereo and i can't find a way to install the realtec alc850 driver on my ubuntu 6.10. could someone help me?

---

