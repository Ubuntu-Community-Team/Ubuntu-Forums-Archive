---
title: "optical out surround sound - what worked for me"
date: 2008-12-31
forum: Multimedia Software
---

### Post by zenryou on 2008-12-31
ok, I read through about 800 threads and edited various pulse config files until my fingers bled and it just didn't work.  Here's what I did from a fresh install and the surround, flash sound, amarok etc worked freaking awesome.

Install all codecs, including everything starting with xmms2.  Install flash and video card drivers and all that.  The following is exactly what I did, whether or not everything is 100% necessary is another thing.  I'd try everything first(that relates to your soundcard at least) just to be safe.

I made a file in my /home/zen directory called .asoundrc
A few ubuntu installs earlier this file was magically there already, this time it wasn't so I had to make it.  The only thing in the file is the following:

pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

I did chmod 777 .asoundrc just because I did to make sure I wouldn't have problems with it or something.  I've used linux about week this might be totally unnecessary.

Install vlc and mplayer and smplayer the gui for it, if only to test with different programs and make sure surround is working.

go to system>preferences>sound
I have everything on autodetect, and my default mixer track is hda nvidia(alsa mixer).  You can change these settings from auto to whatever you think is best, hda nvidia alc885 digital (alsa) also works for me.

click on the sound icon in the top panel. click preferences in the bottom right.  IMPORTANT: check IEC958 and IEC958 Default PCM.  These are right after the headphone option in case your card lists something different there.  This is the optical playback options that will be under the switches tab in system>prefs>sound switches tab. 
Check both of the checkboxes with iec958 next to it.

For the device pulldown field I have HDA Nvidia (alsa miser), choose the relevant option for your card.  Mine is onboard btw and it works awesome.

Also in preferences where you chose iec958 check all the boxes relating to stuff like surround, center, side.  I just checked them all and turned them all up in the playback tab.

play a file in vlc you know for a fact has a surround track, if you're not sure use mediainfo on the file.

right click on the video go to audio choose the dts 5.1 track or whatever surround track is there.  right click and go to audio device and choose A/52 over S/PDIF.  You should hear surround sound in all its glory now.

Still in vlc go to tools>preferences>audio
check use s/pdif when available.  this enables surround through optical out.

now open a vid with surround sound in smplayer.  go to options>preferences>audio tab

click on channels by default make it 6 for 5.1 surround or whatever is relevant to you.  check the box beside AC3/DTS pass-through S/PDIF.  In other programs you might need to check or enable this option for stuff to play through optical correctly, at least I did.

In the general tab I have selected alsa for audio and it works like a champ. video output driver I have a xv.  Let me say that smplayer is THE best player I have ever used.  I have an 8800gtx and in winxp I couldn't play 1080p.  I play 1080p like it's standard definition on linux it truly is amazing.

Whenever you play a video make sure it's set to 5.1 channels if it doesn't sound right, these should auto detect the digital track though.

now open up amarok, the music application.

go to settings>configure amarok>engine

for output plugin I chose alsa and under speaker arrangement I chose passthrough.  This sends it through the optical out and from there I can choose how it plays through the speakers on my surround sound settings.

Everything works for me now, if some of my explanations are technically inaccurate forgive me, I'm new to linux and having to actually configure things manually.

I have no doubt this won't work for everyone, I can certainly relate to that.  Hopefully it helps a few people at least.  I have an evga 680i mobo which I believe is fairly common so it may work for others with nvidia onboard sound.

---

### Post by Eniigmaa on 2009-01-20
> **zenryou said:**
> ok, I read through about 800 threads and edited various pulse config files until my fingers bled and it just didn't work.  Here's what I did from a fresh install and the surround, flash sound, amarok etc worked freaking awesome.

Install all codecs, including everything starting with xmms2.  Install flash and video card drivers and all that.  The following is exactly what I did, whether or not everything is 100% necessary is another thing.  I'd try everything first(that relates to your soundcard at least) just to be safe.

I made a file in my /home/zen directory called .asoundrc
A few ubuntu installs earlier this file was magically there already, this time it wasn't so I had to make it.  The only thing in the file is the following:

pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

I did chmod 777 .asoundrc just because I did to make sure I wouldn't have problems with it or something.  I've used linux about week this might be totally unnecessary.

Install vlc and mplayer and smplayer the gui for it, if only to test with different programs and make sure surround is working.

go to system>preferences>sound
I have everything on autodetect, and my default mixer track is hda nvidia(alsa mixer).  You can change these settings from auto to whatever you think is best, hda nvidia alc885 digital (alsa) also works for me.

click on the sound icon in the top panel. click preferences in the bottom right.  IMPORTANT: check IEC958 and IEC958 Default PCM.  These are right after the headphone option in case your card lists something different there.  This is the optical playback options that will be under the switches tab in system>prefs>sound switches tab. 
Check both of the checkboxes with iec958 next to it.

For the device pulldown field I have HDA Nvidia (alsa miser), choose the relevant option for your card.  Mine is onboard btw and it works awesome.

Also in preferences where you chose iec958 check all the boxes relating to stuff like surround, center, side.  I just checked them all and turned them all up in the playback tab.

play a file in vlc you know for a fact has a surround track, if you're not sure use mediainfo on the file.

right click on the video go to audio choose the dts 5.1 track or whatever surround track is there.  right click and go to audio device and choose A/52 over S/PDIF.  You should hear surround sound in all its glory now.

Still in vlc go to tools>preferences>audio
check use s/pdif when available.  this enables surround through optical out.

now open a vid with surround sound in smplayer.  go to options>preferences>audio tab

click on channels by default make it 6 for 5.1 surround or whatever is relevant to you.  check the box beside AC3/DTS pass-through S/PDIF.  In other programs you might need to check or enable this option for stuff to play through optical correctly, at least I did.

In the general tab I have selected alsa for audio and it works like a champ. video output driver I have a xv.  Let me say that smplayer is THE best player I have ever used.  I have an 8800gtx and in winxp I couldn't play 1080p.  I play 1080p like it's standard definition on linux it truly is amazing.

Whenever you play a video make sure it's set to 5.1 channels if it doesn't sound right, these should auto detect the digital track though.

now open up amarok, the music application.

go to settings>configure amarok>engine

for output plugin I chose alsa and under speaker arrangement I chose passthrough.  This sends it through the optical out and from there I can choose how it plays through the speakers on my surround sound settings.

Everything works for me now, if some of my explanations are technically inaccurate forgive me, I'm new to linux and having to actually configure things manually.

I have no doubt this won't work for everyone, I can certainly relate to that.  Hopefully it helps a few people at least.  I have an evga 680i mobo which I believe is fairly common so it may work for others with nvidia onboard sound.


You are the man!!!!!!!!!!!  Worked Perfectly

---

### Post by poetj on 2009-02-28
Hi... 

well, I tried following what you wrote but when I tried to create the folder (I'm running 8.10) it wouldn't let me as it has a file with the same name. 

I really want to be able to play directly from the optical in order to play 5.1 whenever i want to :) 

but for some reason optical don't seem to work. 

Any ideas? 

Thank you

---

### Post by kingsleyben on 2009-08-18
You are AWESOME!!! I've been trying forever and FINALLY this worked!!!!

:)

---

### Post by Gen2ly on 2009-08-18
You don't need the xmms stuff.  Xmms is a pretty much depracted music player.  Your .asoundrc it the big thing here (think you have to logout/login to get it recognized) and permissions as 644 is just fine.  Nice job getting it going.

---

