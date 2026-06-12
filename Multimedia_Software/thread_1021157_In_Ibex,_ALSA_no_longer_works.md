---
title: "In Ibex, ALSA no longer works"
date: 2008-12-25
forum: Multimedia Software
---

### Post by DinkyDogg on 2008-12-25
I just upgraded Hardy to Ibex, and ALSA no longer works. I don't get any obvious errors, but I just don't get sound. I have two sound cards in my comp, and neither outputs sound under ALSA. When I switch to OSS, my onboard sound works, but my Soundblaster Audigy 2 Platinum still does not. I've made sure that the volume for playback on all of them is at max.

Any ideas? Is there a log I can look at for more information?

Thanks for any help.

---

### Post by norbs on 2008-12-25
Hi there.
I had almost the same problem. My sound actually worked, but I had no 5.1 playback (at least no sound coming out from my back speakers and sub).
As I found out, PulseAudio was guilty.

First try this command

alsamixer

If PulseAudio appears instead of alsamixer then go to 

System/Preferences/Sessions  then disable PulseAudio session manager and 

add a new program, adding this script in after pressing "add"

killall pulseaudio

This stops PulseAudio at boot. 

Thread that helped me: [http://ubuntuforums.org/showthread.php?t=771108&page=3](http://ubuntuforums.org/showthread.php?t=771108&page=3)

P.S. Whit some other modifications my 5.1 sound works finally :guitar:

---

### Post by neu2buntu on 2008-12-25
goto >system>preferences>sound and choose alsa for all devices

---

### Post by norbs on 2008-12-25
> **chrissy.mc.1@hotmail.co.u said:**
> goto >system>preferences>sound and choose alsa for all devices

this dose not worked for me, because alsa was overridden. Maybe it will help the poster.

---

### Post by smuggly on 2008-12-25
I think intrepid does pulse audio.One of the reasons i havent upgraded yet.

---

### Post by neu2buntu on 2008-12-25
intrepid messes up a lot of stuff especiallly wifi and sound ,that is prob why it is betteer to stick with hardy as it is long support....but i made the jump but got my wifi sorted (acer aspire 1)

---

### Post by 2hot6ft2 on 2008-12-25
Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

no sound
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
if so and you still have no sound try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by wolfen69 on 2008-12-25
> **smuggly said:**
> I think intrepid does pulse audio.One of the reasons i havent upgraded yet.

pulse audio is easy to remove.

---

### Post by neu2buntu on 2008-12-25
is there a terminal code to show what is using your sound card...ie alsa oss or pulseaudio or whatever...this woulkd be usefull!!

---

