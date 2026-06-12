---
title: "ASUS EB1012 HDMI sound not working"
date: 2010-07-16
forum: Multimedia Software
---

### Post by Karmalicious on 2010-07-16
I have a bit of problem and have been trying generic fixes and searching the net, including this forum for a guide/help

I have a Asus EEEBOX EB1012 and everything except the sound is fine. I can use a normal 3,5mm stero plug and get sound, but neither optical och HDMI sound will work. HDMI picture is no problem.


[LIST]
[*]I have made sure nothing is muted/not turned on in alsamixer
[*]I have tried every "profile" under Sound Preferences
[*]I have tried Alsa upgrade script
[*]I have tried getting rid of pulse
[*]I have tried getting different drivers for the Nvidia card
[*]I have tried Ubuntu 10.04 and 9.10
[/LIST]

At this point I'm at a loss and don't know what else to do. Has anyone had any luck with HDMI sound on a EB1012 or the ALC662 card?

I have several other devices hooked up via HDMI, Xbox 360, Playstation 3, PC (Windows) and none of them are problematic so I'm pretty sure it's related to the ASUS/Ubuntu somehow.

---

### Post by lidex on 2010-07-17
Have a look here:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
[http://ubuntuforums.org/showthread.php?t=1466111]("http://ubuntuforums.org/showthread.php?t=1466111")
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

---

### Post by Karmalicious on 2010-07-17
First of all, thank you for the links lidex. They got it to work, but  not like they thought it would
After some fiddling around I at last got it all to work. I can't really  see the logic in it but whatever works, right?

In case someone else get this weird "problem" this might help them too,  so I'll write down my experience.


[LIST]
[*]I made a fresh install of Ubuntu Desktop AMD64 10.04
[*]I let it install the proprietary NVidia driver it prompts you to after starting up for the first time, and installed all the update.
[*]I restarted the computer
[*]I downloaded the surround test file from  [http://sverigesradio.se/laddahem/multikanal/dts/surroundtest_011212.zip](http://sverigesradio.se/laddahem/multikanal/dts/surroundtest_011212.zip) and unpacked it
[*]I then played the file with aplay -D hdmi:CARD=NVidia,DEV=0 ./SURROUNDTEST_011212.wav and successfully heard the voice from the correct speakers (It's in swedish, but it goes left front, center, right front, left back, right back). To get the device (flag -D) I typed aplay -L and looked for HDMI.
[/LIST]
After doing that the HDMI sound started working for some reason.

I have literally tried loads of things like forcing the output in mplayer to no avail, but this for some reason did the trick. I tried other things as well but as they got me nowhere I won't bother writing them down, I just did it all over and went straight to the "solution" this time to make sure that was what helped.

Perhaps someone else will benefit from this, and I must point out that the links that lidex posted is very well written and worth reading and probably solves more common problems. This one is just weird imo. :)

---

### Post by lidex on 2010-07-18
Good news indeed. Thanks for following up here with your fix.

---

### Post by empoulator on 2010-09-13
It didn't work for me :(, but thanks for the remark !

> **Karmalicious said:**
> First of all, thank you for the links lidex. They got it to work, but  not like they thought it would
After some fiddling around I at last got it all to work. I can't really  see the logic in it but whatever works, right?

In case someone else get this weird "problem" this might help them too,  so I'll write down my experience.


[LIST]
[*]I made a fresh install of Ubuntu Desktop AMD64 10.04
[*]I let it install the proprietary NVidia driver it prompts you to after starting up for the first time, and installed all the update.
[*]I restarted the computer
[*]I downloaded the surround test file from  [http://sverigesradio.se/laddahem/multikanal/dts/surroundtest_011212.zip](http://sverigesradio.se/laddahem/multikanal/dts/surroundtest_011212.zip) and unpacked it
[*]I then played the file with aplay -D hdmi:CARD=NVidia,DEV=0 ./SURROUNDTEST_011212.wav and successfully heard the voice from the correct speakers (It's in swedish, but it goes left front, center, right front, left back, right back). To get the device (flag -D) I typed aplay -L and looked for HDMI.
[/LIST]
After doing that the HDMI sound started working for some reason.

I have literally tried loads of things like forcing the output in mplayer to no avail, but this for some reason did the trick. I tried other things as well but as they got me nowhere I won't bother writing them down, I just did it all over and went straight to the "solution" this time to make sure that was what helped.

Perhaps someone else will benefit from this, and I must point out that the links that lidex posted is very well written and worth reading and probably solves more common problems. This one is just weird imo. :)

---

