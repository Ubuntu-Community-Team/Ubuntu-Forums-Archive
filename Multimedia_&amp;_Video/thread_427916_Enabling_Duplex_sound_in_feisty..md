---
title: "Enabling Duplex sound in feisty."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by amlucent23 on 2007-04-29
Just came over from the darkside of the nightmare of opensuse 10.2 to the new ubuntu 7.04 and I have to admitt, I am very impressed! So impressed i felt comfertable enough to even ditch the dual boot XP for good. But I have just a couple of small minor annoyances that i have found after a week of use.

First my sound card can only play audio from one source at a time, for example i can not hear audio from a website while listening to banshee, or hear audio in teamspeak while listening to in game audio. its strange. I believe this is called duplex audio, right? my sound card (driver) is an onboard nvidia CK8S.

Also I cannot seem to have more than one app access the internet at the same time. Evolution fails to download  mail until I close Firefox, banshee will not download album art while firefox is up.. strange

at any rate could anyone point me at any system files that I could edit or any tricks to point me down the right path to solving any of these errors I would be appreciative.

---

### Post by amlucent23 on 2007-04-30
BUMP.. Anyone have any experience with this? 

I guess my formatting sucks. I am saying that if i launch an app that uses sound, then I launch a second app that uses sound, I can only get sound from the first one. Example I launch firefox and go to youtube turn on a video, then launch a video or mp3 and i cannot hear it. Even if i turn the you tube sound all the way down and turn the mp3 volume all the way up. As soon as I close the app I opened first the sound from the second app comes through loud and clear.

---

### Post by amlucent23 on 2007-05-01
BUMP

echo, can anyone hear me?

---

### Post by capran on 2007-05-09
I was just wondering the same thing. I've used various flavors of Linux on and off over the years, and I'm currently running Feisty on my gaming PC. I have a Creative Xmod and it works great except for having to un/replug it on boot to get it to work, and this issue.

I know in the past I had a similar complaint, and I think the solution was to set programs up so the ran within a wrapper program instead of directly, that way sound was tunneled through the audio wrapper so everything that was run that way could do sound.

I might be out of date with that idea, and I can't remember off the top of my head what it was called! Alsa wrapper or something? It was a couple of years ago when I used Gentoo and KDE.

***EDIT:***

D'oh! You and I should have just f'in googled it! Well here's the answer, dude:

[http://doc.gwos.org/index.php/ALSA_OSS_ESD_with_Duplex](http://doc.gwos.org/index.php/ALSA_OSS_ESD_with_Duplex)

Works for me!

---

