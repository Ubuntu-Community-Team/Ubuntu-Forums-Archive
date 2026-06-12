---
title: "no sound after update"
date: 2009-03-18
forum: Mythbuntu
---

### Post by dragoster on 2009-03-18
I have Mythbuntu 8.10 running on a Nvidia 7050 motherboard with integrated sound. I've had the system for about 1.5 yrs, with the sound working flawlessly. 

After a recent synaptic update the sound stopped working. I followed every troubleshooting guide under the sun, reinstalled, and recompiled alsa, uninstalled pulseaudio, esd, and gdm with absolutely no luck. Everything seems to be in order and all the important channels are unmuted in alsamixer. 

Here's a snapshot of the audio system as produced by alsa information script. 
[http://www.alsa-project.org/db/?f=62eef39d059efc64b0fa504c60107cf9f3568022]("http://www.alsa-project.org/db/?f=62eef39d059efc64b0fa504c60107cf9f3568022")
Since I have run this script I have uninstalled esd and reinstalled pulseaudio, but still no luck.

I don't know if this helps, but immediately after the update that caused this problem, I was able to get the sound to work if I started playing something via the mpd client that I have installed on the system. After the first restart that trick didn't work anymore. As of now the mpd client gives the following error 

Warning: fsockopen() [function.fsockopen]: unable to connect to 127.0.0.1:6600 (Connection refused) in /var/www/relaxx/include/mpd/Common.php on line 96

It feels like the audio stream is redirected somewhere else. Are there any services or programs which could lead to this if misconfigured?

Although it has served me well for so long, my MythBox is now totally useless with no sound.

Thanks,
-D

---

### Post by D3ath on 2009-03-18
> **dragoster said:**
> I have Mythbuntu 8.10 running on a Nvidia 7050 motherboard with integrated sound. I've had the system for about 1.5 yrs, with the sound working flawlessly. 

After a recent synaptic update the sound stopped working. I followed every troubleshooting guide under the sun, reinstalled, and recompiled alsa, uninstalled pulseaudio, esd, and gdm with absolutely no luck. Everything seems to be in order and all the important channels are unmuted in alsamixer. 

Here's a snapshot of the audio system as produced by alsa information script. 
[http://www.alsa-project.org/db/?f=62eef39d059efc64b0fa504c60107cf9f3568022]("http://www.alsa-project.org/db/?f=62eef39d059efc64b0fa504c60107cf9f3568022")
Since I have run this script I have uninstalled esd and reinstalled pulseaudio, but still no luck.

I don't know if this helps, but immediately after the update that caused this problem, I was able to get the sound to work if I started playing something via the mpd client that I have installed on the system. After the first restart that trick didn't work anymore. As of now the mpd client gives the following error 

Warning: fsockopen() [function.fsockopen]: unable to connect to 127.0.0.1:6600 (Connection refused) in /var/www/relaxx/include/mpd/Common.php on line 96

It feels like the audio stream is redirected somewhere else. Are there any services or programs which could lead to this if misconfigured?

Although it has served me well for so long, my MythBox is now totally useless with no sound.

Thanks,
-D
Hey there never used mythbuntu before but have you tried uninstalling and reinstalling mythbuntu?
[http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
I was looking at that and you don't have to install it from a disc or anything and maybe a fresh install would clear something up.

---

### Post by dragoster on 2009-03-19
There should be no reason to reinstall the entire mythbuntu just for a sound problem. I would also hate to lose my database and all the personal settings that have accumulated after a year of up time. 

Has anybody experienced the same problem with no sound with the snd-hda-intel driver? Is it gstreamer or other server program that is redirecting the audio stream somewhere else?

Thanks,
-D

---

### Post by nickrout on 2009-03-19
have you checked via alsamixer that the update hasn't muted or zeroed the sound?

---

### Post by maculata on 2009-03-19
Have you reinstalled the audio driver yet?

---

### Post by nelskurian on 2009-03-19
R you checked the below guide..

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by D3ath on 2009-03-19
> **dragoster said:**
> There should be no reason to reinstall the entire mythbuntu just for a sound problem. I would also hate to lose my database and all the personal settings that have accumulated after a year of up time. 

Has anybody experienced the same problem with no sound with the snd-hda-intel driver? Is it gstreamer or other server program that is redirecting the audio stream somewhere else?

Thanks,
-D

I don't understand why you think you have to reinstall mythbuntu. Its the same as ubuntu studio.  There are add-on programs to make it look and act the way it does.  Its just ubuntu. Are you having issues with just mythbuntu as in the media program or ubuntu itself?

---

### Post by dragoster on 2009-03-19
Thanks for the reply.

I have followed the guide above, recompiled and reinstalled the driver, have the correct modules loading, etc. There are no errors after each step and I still have no sound. Maybe I should have mentioned, but this is a system wide problem, i.e. no sound when I try to play mplayer, vlc, or xine. Alsamixer has the relevant channels maxed out and unmuted. 

Other (i)relevant information:

after the synaptic update that caused this sound problem the usb wireless ir keyboard I was using stopped working. Also the analog tv tuner card started recording black with no sound on all channels. The pcHDTV card still records with no problems. Can it be some codec that is causing both the analog video and audio problem? 

Is there a way to reinstall / repair a mythbuntu install without wiping my database, video, music and pictures folders and all the other nice settings I have on the system now. Although they are no technically part of myth I am concerned about videos and music because I am running two hard drives in LVM.

Any help from you myth gurus will be highly appreciated.
-D

---

### Post by D3ath on 2009-03-19
> **dragoster said:**
> Thanks for the reply.

I have followed the guide above, recompiled and reinstalled the driver, have the correct modules loading, etc. There are no errors after each step and I still have no sound. Maybe I should have mentioned, but this is a system wide problem, i.e. no sound when I try to play mplayer, vlc, or xine. Alsamixer has the relevant channels maxed out and unmuted. 

Other (i)relevant information:

after the synaptic update that caused this sound problem the usb wireless ir keyboard I was using stopped working. Also the analog tv tuner card started recording black with no sound on all channels. The pcHDTV card still records with no problems. Can it be some codec that is causing both the analog video and audio problem? 

Is there a way to reinstall / repair a mythbuntu install without wiping my database, video, music and pictures folders and all the other nice settings I have on the system now. Although they are no technically part of myth I am concerned about videos and music because I am running two hard drives in LVM.

Any help from you myth gurus will be highly appreciated.
-D
Not to say anything about quiting but if your not worry about the data what are you worried about? you can back-up documents and your theme/icons/settings. re-install and everything should be back to normal. I'm just saying. Or find a forum that deals with more on mythbuntu. I don't think many people here are using that.

---

### Post by boof1988 on 2009-03-19
> **D3ath said:**
> Not to say anything about quiting but if your not worry about the data what are you worried about? you can back-up documents and your theme/icons/settings. re-install and everything should be back to normal. I'm just saying. Or find a forum that deals with more on mythbuntu. I don't think many people here are using that.

This *is* the Mythbuntu sub-forum.  And do you want to post where all the important "theme/icons/settings" are?

---

### Post by D3ath on 2009-03-19
> **boof1988 said:**
> This *is* the Mythbuntu sub-forum.  And do you want to post where all the important "theme/icons/settings" are?

yea sure backup the 
```
mv ~/home
```

Then where ever you need to back it up. that is your home folder with all your setting and app information.

---

### Post by dragoster on 2009-03-20
I sorted out the video problems, but still no sound. The last resort is using the alsa reinstall script from [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810"). I will try that tonight.

---

### Post by dragoster on 2009-03-21
[Solved]!!

I installed the newest alsa driver using the script above.

After a fresh reboot aplay would give output for wav files but would give this error after opening up vlc, xine, and firefox:

```
aplay: main:590: audio open error: Device or resource busy
```

The only program using any /dev/snd at that moment was xfce4-mixer. Anyhow, I restarted and I had to made one more change in mythtv:

under
>Setup>General>
device alsa:surround5.1
output 5.1

Any other settings in mythtv will not give any sound.

Again I have Mythbuntu 8.10, on a Nvidia 7050 card with integrated audio.

Thannks everyone,
D

---

### Post by D3ath on 2009-03-21
> **dragoster said:**
> [Solved]!!

I installed the newest alsa driver using the script above.

After a fresh reboot aplay would give output for wav files but would give this error after opening up vlc, xine, and firefox:

```
aplay: main:590: audio open error: Device or resource busy
```

The only program using any /dev/snd at that moment was xfce4-mixer. Anyhow, I restarted and I had to made one more change in mythtv:

under
>Setup>General>
device alsa:surround5.1
output 5.1

Any other settings in mythtv will not give any sound.

Again I have Mythbuntu 8.10, on a Nvidia 7050 card with integrated audio.

Thannks everyone,
D

You Rock!

---

### Post by dragoster on 2009-03-21
I just figured out which program was hogging audio card: MPD. I tried remove --purge and then reinstall but even with a fresh install it does the same thing. 

Does anyone have some experience with MPD? Should it use only the OSS output? Or maybe the pulseaudio? When I set it up to use alsa it gives fail on /etc/init.d/mpd restart and then one of the /dev/snd devices is in use. After starting mpd aplay gives the "device in use" error.

Thanks,
-D

---

