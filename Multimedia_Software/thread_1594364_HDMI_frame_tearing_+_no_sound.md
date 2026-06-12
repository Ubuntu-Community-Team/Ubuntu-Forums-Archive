---
title: "HDMI frame tearing + no sound"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Kash88 on 2010-10-12
Hi,

I have a nvidia 330m card with the proprietary driver and am currently on ubuntu 10.10
Every time i play a video via hdmi, I get frame tearing on my tv and no sound. I used to get frame tearing on the primary display of my laptop as well but it stopped when I switched to metacity but it still didn't help with the hdmi output. And when I go to alsamixer, the nvidia card displayed there is different than what I have (It says GT220).

So if anyone can help me out that would be great.

Thanks

---

### Post by Kash88 on 2010-10-15
anyone? And in the sound cards available in alsamixer it shows intel and nvidia.

---

### Post by Kash88 on 2010-10-18
bump

---

### Post by Kash88 on 2010-10-27
final bump

---

### Post by ozzman2 on 2010-10-28
Hi

I had problem of videos tearing with my onboard Nvidia GeForce 8200.

What fixed it was
1. Blacklisting Nouveau
2. Installing latest proprietary driver from Nvidia website
3. Changing a few settings in Compiz
(got the instructions from here: [http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/) )

Sorry, can't help you with the audio (I use toslink in leu of HDMI).

-edit-
One thing I forgot to mention:
After you blacklist Nouveau, you will have to manually re-install the proprietary Nvidia driver whenever a new kernel update comes out.  ie. don't delete the installation package, and write down the command to re-initialize it from a prompt.

I know it sounds like a pain, but it's totally worth it.  It handles HD video flawlessly (sound stays in sync and everything).

---

### Post by Kash88 on 2010-12-20
Never mind fixed it myself by changing the audio source to alsa and  selecting one of many "nvidia hdmi" (only one works) it listed in vlc although i am not  getting sound from anything else, for example in my browser (youtube)  and under sound preferences changing to hdmi has no effect. So how do I  make this change systemwide like in my browser and other media players and not just the vlc media player?

---

### Post by efflandt on 2010-12-20
The front end for alsa is pulse, so you need to tell pulse which card, device works for your HDMI.  For example the working HDMI on my GT 430 it is card 1, device 9, so I added a line after the commented out alsa-sink line in /etc/pulse/default.pa

```
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:1,9
```Then reboot for it to take effect. Note that the speaker test in Sound Preferences may not work for HDMI, maybe because contrary to what you might expect, what is listed as HDMI in Output tab may not work either.  But a new Output appeared that was just something like "HDA Nvidia Digital Stereo" (without any mention of HDMI), and that worked for HDMI.  Once you get it working, you should be able to use Sound Preferences to switch Output on the fly between your internal audio and HDMI audio (even if not called that).

---

