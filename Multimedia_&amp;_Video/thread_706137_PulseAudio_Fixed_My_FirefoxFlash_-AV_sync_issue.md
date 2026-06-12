---
title: "PulseAudio Fixed My Firefox/Flash -A/V sync issue"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by CubeXombi on 2008-02-24
Not sure if this is for everyone out there, but I've been noticing a lot of "I had a horrible audio sync problem with flash 9 and this fix seems to make it not as bad but it's still not great".. Hope this helps.


Preamble:

I've tried, I really have to get my audio working for the longest time, 
First it would work GREAT but, only on google video and daily motion, not much else..

On youtube and a few other places I would get sync issues with:
FIREFOX_DSP="none"

I tried installing alsa-oss and going with:
FIREFOX_DSP="aoss", 
but in the end, my sound was iffy, sometimes it would *glitch* for a few ms and then resume off sync, sometimes no sound at all.

Decided to switch to PulseAudio to see.. 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
Followed this ---^ 

Stole the following of it to show what worked for me.

(in short)
> 
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter libflashsupport

Then:
> 
gksu gedit /etc/firefox/firefoxrc
edit:: 
> FIREFOX_DSP="esd"

Next create the asound.conf:
> gksu gedit /etc/asound.conf

and paste in the following:

> pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

Go to System -> Administration -> and click on Users and Groups.
Click on Manage Groups, and scroll all the way to the bottom of the list where you will find:

    * pulse
    * pulse-access
    * pulse-rt

[COLOR="Red"]Make sure[/COLOR] to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound, cause.. well.. otherwise you won't.

---

