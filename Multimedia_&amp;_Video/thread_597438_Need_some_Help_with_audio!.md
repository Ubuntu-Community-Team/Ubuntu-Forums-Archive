---
title: "Need some Help with audio!"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by popocus on 2007-10-30
i have done fresh install of ubuntu gutsy from feisty where i had sound but once i installed gutsy nothing happens i have tried eveything when i try to see if ubuntu is detecting my integrated audio it does nothing it says USB audio which feisty never did that and if i go to sound preferences and change the music and audio playback settings to USB audio only music wokrs but no sound from system or video and recently  my video went berserk it just shows me a rainbow of colors no audio or anything the audio and video are my only problem with gutsy at the moment ...if anyone has any suggestion at what i should please tell me it would be greatly appreciated...thank you.

---

### Post by DeadToad on 2007-10-30
Can you play DVD with video and sound working correctly?
You may need a codec update.
DeadToad

---

### Post by popocus on 2007-10-30
no nothing no sound im using vlc at the beiginning everything was fine then reboot and gone mainly i want to fix the audio. any steps at what i should i am using a M2N32-SLI DELUXE motherboard from ASUS  thanks for the prompt reply.

---

### Post by DeadToad on 2007-10-30
Sounds like you need to reinstall your soundcard drivers.  Try this:

Open Synaptic (System -> Administration -> Synaptic Package Manager).
In Settings -> Repositories, make sure you have a "universe" repository activated.
Search for "audio".  Audio will be shown in the left window.
In the right window, click the audio files for your system.
Then click "Mark for Installation".
When finished, hit "Apply" to download/install the files.
Hope this helps.
DeadToad

---

### Post by DeadToad on 2007-10-30
pop, check out this thread:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)

Good luck, Brother.
DeadToad

---

### Post by DeadToad on 2007-10-30
pop, if the first 2 don't work, try this thread:
[http://ubuntuforums.org/showthread.php?t=524506](http://ubuntuforums.org/showthread.php?t=524506)

The new ALSA drivers seem to work for most everyone.
DeadToad

---

