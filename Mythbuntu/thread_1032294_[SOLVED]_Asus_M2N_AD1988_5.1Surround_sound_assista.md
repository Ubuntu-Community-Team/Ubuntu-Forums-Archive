---
title: "[SOLVED] Asus M2N AD1988 5.1/Surround sound assistance please"
date: 2009-01-06
forum: Mythbuntu
---

### Post by bruk on 2009-01-06
I just acquired a nice 5.1 setup cheaply, and so have set about hooking it up to my myth box. But, so far I'm having little or no luck getting it to work, despite trawling through umpteen ubuntu audio/hardware guides. So if there's any person who can answer my questions, I would be very grateful.

Firstly, I'm using the onboard audio from my M/B, which is an Asus M2N nForce 430 MCP, with a SoundMax/Analog Devices AD1988 audio chip, and audio output was already working in 2 channel mode with no issues whatsoever.

Initially I tested the very simple solution at [http://www.newlinuxuser.com/surround-sound-in-ubuntu/](http://www.newlinuxuser.com/surround-sound-in-ubuntu/) which just involves making a .asoundrc file with a 6 channel setup. This gave no joy as far as working, but did make speaker-test generate an error saying that it couldn't open "surround51" for output, running it directly with "-Dplug:surround51" doesn't generate this error, but it doesn't do anything other than 2 channels either.

Then I discovered a number of threads about the ALSA driver snd_hda_intel, and how adding "options snd-hda-intel model=3stack-6ch" to /etc/modprobe.d/alsa-base, should enable surround and all the relevant settings in alsamixer. This seems to work for some people, but not for me, perhaps because the AD1988 isn't explicitly listed as supported by ALSA.

To be sure it wasn't something fixed/added in a newer version, I installed the latest ALSA (1.0.18) using the guide at [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695), this completed successfully and appeared to offer some new options in alsamixer, but not the ones I was looking for. As a quick check, I retested both of the above fixes with the newer ALSA, but no change, still just 2 channels.

So now I'm left with a few questions:

1) My M/B manual purports the sound chip to be surround capable and has 3 jacks, which seems to be all I'd need?

2) The ALSA page doesn't strictly mention the AD1988 as supported, but in the mixer it is listed as AD198x suggesting a certain amount of similarity in the versions, and also the AD1988 is specifically mentioned in changelogs for the ALSA source. What's the story here?

3) Finally, if the soundcard is 5.1 capable and ALSA supports it, where am I going wrong?

---

### Post by bruk on 2009-01-06
Typically I find the solution randomly, shortly after asking for help.

[http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1988](http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1988)

---

