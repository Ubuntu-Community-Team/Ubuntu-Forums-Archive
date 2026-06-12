---
title: "help getting media to work."
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by ride1226 on 2007-01-21
ok. with the help of a nice person on here i got my windows partition mounted and now have access to my itunes library in my documents on Windoze. i have downloaded amarok becuz from what i understand thats the best media player to use. now my question is how can i play all my media files...i have heard that ubuntu doesnt come with the codecs installed so how do i go about doing this....i have files such as .avi .mp3 .mp4 .wmv .wma and so on....how can i get these to work. thanks to all in advance.

---

### Post by meng on 2007-01-21
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Now instead of doing this, some other folks use Automatix. [www.getautomatix.com](www.getautomatix.com)

---

### Post by ride1226 on 2007-01-21
man....u knew right were to find me and what to tell me. lol. best experience iv had with anything in awhile. thank you. installed automatix and now installing the multimedia codecs package along with gdesklets and a few other things i found interesting. ill post back when done to report if things are working or not. thanks again.

---

### Post by ride1226 on 2007-01-21
ok....automatix finished all my program installs and my music is playing in amaroK....however...things sound slightly distorted...voices are deeper and the music just doesnt sound right...i turned on the equalizer and played with that and nothing changed....any ideas? thanks again.

---

### Post by ride1226 on 2007-01-22
i updated my system in hopes that updates would take care of the distortion....all of my music still sounds vry distorted though unfortunatly...equalizer didnt change anything....its actually really annoying as nothing sounds right...any ideas? also all of my video colors are WAY off and extremly bad quality...any help getting this working corectly would be great. thanks all.

---

### Post by ride1226 on 2007-01-22
i found a guide to get my WMV movies playing however all colors are stil vry distorted and quality is bad...and i cant get my music to sound right....it actually sounds as if its playing the music just a bit to slow....making things sound deeper and distorted...any ideas on what to do as music is a huge part of my day. thanks.

---

### Post by ride1226 on 2007-01-22
anybody?

---

### Post by meng on 2007-01-22
What sort of sound card do you have?

---

### Post by ride1226 on 2007-01-22
i am almost 100% sure it is an integrated sound card...i am running a Dell 4600C that is 3-4 yrs old. only things i personally have changed in it is added ram and HDD....so the soundcard is stock.

---

### Post by meng on 2007-01-22
You can look for your sound card by:
lspci

(but I probably can't advise you more specifically anyway)

Try going to System > Admin > Sound
and changing between oss, alsa and esd

---

### Post by ride1226 on 2007-01-22
when i did lspci this is what it read out for multimedia

 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

in system>pref>sounds it says default sound card Intel ICH5

where do i select oss, alsa, and esd ?

---

### Post by meng on 2007-01-22
System>Pref>Sounds, eh? I thought I might have written that wrongly ...

Anyway, on my computer I have an option for which audio drivers to use with my sound device:
OSS
ALSA
ESD

see if you can find that option somewhere (it's a combo box I believe, possibly on a separate tab).

---

### Post by ride1226 on 2007-01-22
i have a check box to enable ESD and its checked but thats it.

---

### Post by meng on 2007-01-22
deja vu...

---

### Post by ride1226 on 2007-01-22
im lost lol.

---

### Post by ride1226 on 2007-01-22
i played off amarok wit the box checked and with it unchecked and no change in sound. this is  slightly annoying me lol. my music all sounds like crap and my videos look like crap.

---

### Post by meng on 2007-01-22
New thread time?

---

### Post by ride1226 on 2007-01-22
what should i make a new thread for? i am glad atleast u have helped me get the bigger things fixed and working... thank you meng. what would i make a new thread for?

---

### Post by meng on 2007-01-22
You still have a big problem, don't you?
"All my music sounds like crap and videos look like crap"
It's a problem worth solving, I just don't have the answer.

---

### Post by ride1226 on 2007-01-22
lol vry true. should i put it somewhere else or just keep this thread front page in hopes of someone having the answer?

---

