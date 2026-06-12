---
title: "unable to record with microphone"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by vulcanoo on 2007-01-29
Hello.
I am unable to record with my microphone with both sound recorder and audacity.

My inputs seem to be ok.

My sound cjip is crystal clear sound fusion 46xx

I can listen music.

I use alsamixer.

---

### Post by swamytk on 2007-01-29
Have you selected your Mic as recording source in alsamixer? Please ensure it.

---

### Post by sloggerkhan on 2007-01-29
might check under the sound control panel. I assume you did.

---

### Post by vulcanoo on 2007-01-29
yes i did

---

### Post by vulcanoo on 2007-01-30
i also removed alsa-base with apt-get --purge remove and i reinstalled it...
but i still have the problem.

---

### Post by deadgobby on 2007-01-30
Lets try installing Audacity using Synaptic. Audacity is a sound editing program. Once that is installed. Click on the record button and start talking. If it is not grabbing any audio. YOu may need to check your setttings.

Gobby

---

### Post by vulcanoo on 2007-01-30
I have done...all these things.

I think do the tuto :[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by deadgobby on 2007-01-30
[http://ubuntuforums.org/showthread.php?t=258878&page=2](http://ubuntuforums.org/showthread.php?t=258878&page=2)

Gobby

---

### Post by BoomShaka on 2008-07-06
Microphone
The microphone works, but it has to be configured:
   1. Double-click the volume control icon in the top right of the screen.
   2. Select Edit / Preferences.
   3. Add "Digital" and "Digital Input Source" to the list of visible tracks.
   4. On the Options tab, select "Digital Mic 1" for "Digital Input Source".
   5. On the Recording tab, set the input volume of the microphone.

Obtained from:
[http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

---

