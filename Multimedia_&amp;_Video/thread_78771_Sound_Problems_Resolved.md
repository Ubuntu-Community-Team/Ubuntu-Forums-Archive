---
title: "Sound Problems Resolved"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by twisting_logic on 2005-10-18
I am running Breezy on a Tecra 8100 laptop, having upgraded from Hoary. I have had significant problems getting the sound card working properly. 

With help from the forums I got the sound working but could not get the microphone working. I tried everything I could find and nothing worked, in fact things were getting worse, until ...... out of desperation I simply reinstalled all the relevant sound packages with Synaptic and everything works fine now.

This worked also on my desktop after I managed to wreck the sound while I was fiddling with the settings. (Both laptop and desktop have yamaha sound cards, and use the ymfpci driver)

For information I reinstalled the following packages:
alsa-base (1.0.9b-4)
alsa-source (1.0.9b-4)
alsa-utils (1.0.9a-4ubuntu5)
esound (0.2.36-1ubuntu5)
esound-common (0.2.36-1ubuntu5)
libasound2 (1.0.9-2)
libesd-alsa0 (0.2.36-1ubuntu5)
libpt-plugins-alsa (1.8.7-1ubuntu1)
libsndfile1 (1.0.10-2)
linux-sound-base (1.0.9b-4)


I hope that this will help someone.

---

