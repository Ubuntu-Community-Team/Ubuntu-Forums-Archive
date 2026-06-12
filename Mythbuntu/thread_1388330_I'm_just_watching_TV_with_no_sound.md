---
title: "I'm just watching TV with no sound"
date: 2010-01-23
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-23
I finally have my capture card capturing images to my pc...images with no sound that is.  I can listen to audio streams in mplayer, so I know my soundcard works.  Does mythubuntu mute the sound on the first play or is this something that the Pinnacle 800i capture card does (it has a remote that doesn't work...maybe the remote is on mute?)???

---

### Post by linuxhippy on 2010-01-23
Well, still no sound on tv-radio streams sound great on mplayer.  I installed xawtv.  It says that audio is muted but I'm not sure how to unmute it.  

Back to mythbuntu.  The F9 key mutes/unmutes TV shows.  It indicates that nothing is muted and I've adusted the volume to 70% with F10/F11.

But still no sound.  I have a soundblaster audigy sound card.  alsamixer has a lot of sliders for that card.  I put all those about 70% up.

TV looks good-maybe I'll turn on closed captioning and read it!

---

### Post by linuxhippy on 2010-01-23
I figured out what's going on but cannot fix it yet.  2 soundcards are being configured...1 for the sound card (0) and 1 for the capture card (1).  You can see each by doing:

alsamixer -c0
OR
alsamixer -c1

I also added my user to audio in /etc/group and then restarted.  My user can make changes to c0 with alsamixer.  However, my capture audio is muted as I see on c1 and when unmuted the changes don't stick.

So, how do I unmute my capture card with changes that will save?

---

### Post by linuxhippy on 2010-01-24
I just came across this page for the Pinnacle 800i card that I have:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

It takes you to a page where you can build v4l-dvb-2a50a0a1c951.  This is done with make and then make install.  I am thinking that mythbuntu already provided me with v4l-dvb so how do I upgrade to the most recent build?  Do I have to remove v4l-dvb first with synaptic?

---

### Post by linuxhippy on 2010-01-24
figured it out-I had to switch audio on the backend to /dev/dsp1.  I figured this out after seeing that alsamixer was seeing that I had 2 sound devices (c0 and c1)...the mythtv default setup puts audio at /dev/dsp and that has to change to /dev/dsp1.

---

