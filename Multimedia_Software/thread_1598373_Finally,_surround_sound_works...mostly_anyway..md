---
title: "Finally, surround sound works...mostly anyway."
date: 2010-10-16
forum: Multimedia Software
---

### Post by ImageJPEG on 2010-10-16
Well I have upgraded to Ubuntu 10.10 and it seems that surround sound FINALLY works. It doesn't crash PulseAudio anymore.

However, I'm still having issues with surround sound. I have the Logitech Z5500 system and a 5.1 surround sound card. I have music playing through all speakers (the speaker system is set at 6 Ch Direct)...it seems that a random speaker will get staticky and will correct itself anywhere between 5 to 30 seconds then all is great for a few minutes, then another random speaker will do this.

I've gone through alsamixer -c0 and configured everything with the system but no matter what I do it still gets "fuzzy" and staticky. And of course, I enabled 5.1 in the PulseAudio settings in the task bar or whatever you call it.

---

### Post by ImageJPEG on 2010-10-16
Oh, one more thing I forgot to mention.

In the terminal I get this error sometimes after the command:

speaker-test -Dplug:surround51 -c6 -l1 -twav


And the error I get:

Write error: -32,Broken pipe

I have a Hercules Fortissimo III sound card as well

---

### Post by lidex on 2010-10-16
Perhaps changing the default sampling rate would help. 

Open this file for editing:
```
gksudo gedit /etc/pulse/daemon.conf 
```
Look for this line:
```
;default-sample-rate = 44100
```
Change that number to 48000, remove the semi-colon, save and restart pulse:
```
killall pulseaudio
```
If no help, you may need to play with default-fragment/fragment size:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html](http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html)

---

### Post by ImageJPEG on 2010-10-17
Still didn't do anything :(

On the website you posted I noticed that I cannot do this step:

**sudo usermod -a -G audio,pulse-access,pulse-rt**

I get this error:

**usermod: user 'audio,pulse-access,pulse-rt' does not exist**

---

### Post by lidex on 2010-10-17
I don't have a pulse-rt group, you probably don't either.

---

### Post by ImageJPEG on 2010-10-18
I only have a **pulse** group

---

### Post by ImageJPEG on 2010-10-18
I used pulse for the usermod...nothing has changed...still does the static and fuzzy noise...however, it seems like the static/fuzzy noise doesn't happen as often and when it does happen, it doesn't last for long...maybe for 5 seconds usually...

---

### Post by ImageJPEG on 2010-10-18
Sorry for the triple post but I've also noticed that it seems that the center speaker doesn't do it as often as the rear two speakers do. I don't have any issues with the front two speakers though from some reason.

---

### Post by ImageJPEG on 2010-10-20
bump

---

### Post by ImageJPEG on 2010-10-20
Am I just going to have to wait for PulseAudio to mature a bit more?

---

