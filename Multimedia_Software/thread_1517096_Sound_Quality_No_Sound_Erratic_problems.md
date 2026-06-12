---
title: "Sound Quality/ No Sound Erratic problems"
date: 2010-06-24
forum: Multimedia Software
---

### Post by whispered on 2010-06-24
Hi..

I'm currently running ubuntu 10.04 in the 64 bits version.

My problems with the sound started when i installed Amarok, after being unable to hear anything from it i browsed through the web until a i found a "solution"..

i followed the tutorial and did this in the console:

$ sudo apt-get install amarok

$ sudo aptitude install phonon-backend-xine

$ sudo aptitude install phonon-backend-gstreamer

$ sudo apt-get install language-pack-kde-es-base language-pack-kde-es

$ sudo apt-get install libxine1-ffmpeg





After all this amarok started playing music... but later my problems started, now sometimes i get audio in the rest of the programs (ubuntu system and other software) but not in amarok, or sometimes i get sound in amarok but the rest of the system sound with low quality (there is a continuous background noise).

If that wasn't complex enough... i realized all this has something to do with flash as when the sound is ok for the system it always crashes when i surf on the web. 

I looked everywhere for a similar problem with no success, i would like to return everything to zero (even if i have to leave amarok).

any hints??

thanks!

---

### Post by TRoe on 2010-06-24
Hit <ALT><F2> and type in "gstreamer-properties" (without quotes).

In the window that comes up, switch your output to ALSA or OSS and see if it changes the symptoms. If so, then it's probably a buggy pulse audio server.

(had to do this on mine to get rid of strange audio artifacts... using OSS instead of pulse audio now)

---

### Post by whispered on 2010-06-24
thanks!

I tried what you recommended but all the options available had trouble..

i noticed that the noise is a bit "different" on ALSA and PulseAudio...

there is a remarkably erratic behavior. I mean, when i test them sometimes it works well, but when i test again it fails (using the test functionality included in "gstreamer").

Anyway, thanks a lot!

Pd: sorry for my poor writing, i'm not a native speaker.

---

### Post by Yellow Pasque on 2010-06-24
So which phonon backend are you using? I would remove the xine backend or install the qtconfig app and select the gstreamer backend. Make sure gstreamer is set to use pulseaudio.

Also, make sure alsa apps (like Flash) are routed through pulseaudio so that everything mixes together and apps don't lock the sound device: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

EDIT: You might also want to mute your inputs/microphones to make sure they're not producing noise.

---

### Post by whispered on 2010-06-25
Thanks!!

i fell i'm getting close...

i opted to remove xine and seted gstreamer to pulseaudio (in alt-f2 "gstreamer-properties" (yeah... i'm a newbie))

i also pasted the lines you suggested in asound.conf
but flash is still sounding bad....

(the document was empty before pasting those lines).

i also tried muting the audio inputs with no success.



EDIT: it didn't resist a system restart.... back to the beginning

---

