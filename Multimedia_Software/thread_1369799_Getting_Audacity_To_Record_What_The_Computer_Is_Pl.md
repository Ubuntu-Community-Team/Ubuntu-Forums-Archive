---
title: "Getting Audacity To Record What The Computer Is Playing"
date: 2010-01-01
forum: Multimedia Software
---

### Post by ..::| Dave89 |::.. on 2010-01-01
How do I get Audacity to record what the computer is playing?  For instance, if I have a YouTube video open in Firefox and I want to record the audio, what would I have to do?  I've played around with the audio setting in Ubuntu and Audacity 1.3.9 but I couldn't get it to work.

---

### Post by lessmemorelove on 2010-01-02
I just got this to work yesterday. I found the fix in another spot on the forum but I don't remember where. This is all assuming you have karmic.

1. Edit Audacity pref. under "Devices" and change everything to pulse. My host choices were only oss and alsa so i left it alone but make sure you change everything else to pulse.

2. Install pavucontrol in Ubuntu. The first time you ever use a recording program you will have to use pavucontrol to edit the recording settings. It seems to remember your choices after reboots so that is good.

3. pavucontrol should be in your menu as PulseAudio Volume Control. Open it and under the recording tab you will not see anything. leave it open and open up audacity. hit record in audacity. while audacity is recording, check pavucontrol and under the recording tab you should see audacity now. It will say alsa capture from and then show a box. click on that box and select monitor of internal audio. check audacity. you should be recording now.

---

### Post by ..::| Dave89 |::.. on 2010-01-02
That worked perfectly, thanks.

---

