---
title: "can not play music"
date: 2008-10-17
forum: Multimedia Software
---

### Post by odedlo on 2008-10-17
hi
i tried playing my music, which is all in mp3 format,  it just didnt work. recently i had to by a new motherboard so i reinstalled ubuntu on my computer - hardy haron - and had to build a driver for my networking, and a dialller, i guess the setup couldnt automatically install important software.. (i think??).. after that, i also had to configure my soundcard so i installed alsamixer. the jist of it is - i have the start up sounds and i can hear sound when i watch streaming over the internet, BUT i cant hear any music. it started with not working on rhythmbox, so i uninstalled it. after that i installed amarok which also didnt work, and i had to force quit it so i unistaled it also. last i installed exail, which also doesn't work. 
can someone PLEASE help me?

---

### Post by [censored] on 2008-10-17
First off, is the problem actually that your system won't read mp3 format? If so, can it read wav, ogg, flac?

Secondly, don't know if this will help but  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by odedlo on 2008-10-18
it doesn't work for other formats either, just checked ogg, and thythmbox just doesn't reply...

---

### Post by misterfixit on 2008-10-18
> **odedlo said:**
> hi
i tried playing my music, which is all in mp3 format,  it just didnt work. recently i had to by a new motherboard so i reinstalled ubuntu on my computer - hardy haron - and had to build a driver for my networking, and a dialller, i guess the setup couldnt automatically install important software.. (i think??).. after that, i also had to configure my soundcard so i installed alsamixer. the jist of it is - i have the start up sounds and i can hear sound when i watch streaming over the internet, BUT i cant hear any music. it started with not working on rhythmbox, so i uninstalled it. after that i installed amarok which also didnt work, and i had to force quit it so i unistaled it also. last i installed exail, which also doesn't work. 
can someone PLEASE help me?
I've tinkered with Amarok for several years since the first beta.  Amarok is a rather elegant product but it still has many problems.  Did Amarok give you the message "Amarok can't play mp3 files right now" ??  If it did, don't bother to click on the "install button in that window becasue it is usually broken.  However, you can go to Synaptic and install the various mp3 libraries needed for mp3 play.  MP3 support is left out because of the usual "leagal reasons", blah, blah, blah.  If all of your sound is dead during attempts to play back, as you have already described, go to the ALSA control panel and tinker with the various enable and disable settings for sources.  ALSA is another PITA, mainly because of all the different screwed ways that sound is managed by Linux.  I got really tired of all of that and installed PulseAudio and spent several lovely hours getting it to work.  Now I can listen to Insane Clown Party on 7:1 sound with only the neighbors to complain.  Good luck .. and remember, when all else fails, log out and log back in or better yet, reboot, just like Windows.

---

### Post by odedlo on 2008-10-18
thanx i'll try the pulseaudio first thing tomorrow morning...

---

### Post by odedlo on 2008-10-19
no sound what so ever when trying to play music or videos...

---

### Post by mo0on on 2008-10-19
Do you have a Mainboard with ATo 780G or 790G on it? Is there any sound or no sound on everything?
If it's so then you maybe have a problem. There are no drivers out for the Realtek soundchip in bundle with ati only for intel chipsets.
I tried it for myself to get a sound out of the machine but no luck at all.

---

### Post by odedlo on 2008-10-20
> **mo0on said:**
> Do you have a Mainboard with ATo 780G or 790G on it? Is there any sound or no sound on everything?
.

i don't really understand what are you asking.
i have an ASUS motherboard P5KPL-CM Intel G31/CH7 chipset 
there are all the OS sounds and i can watch streaming over the internet. it's just when i want to play something of my own that it doesnt work - mp3, ogg, vidx...

---

### Post by Nidoprince on 2008-10-25
I had this exact problem, but I found the answer on [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/245002](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/245002)
What you have to do is this:  Go into System-Preferences-Sound and change all of the options from Autodetect to ALSA.  Your music should work now.

---

