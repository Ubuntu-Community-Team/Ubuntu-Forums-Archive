---
title: "No sound in Amarok, sound ok elsewhere"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by alwiap on 2007-09-13
I have a sound problem in Amarok. I was using Rhythmbox Media Player and it can play anything fine, I get sound, and I've been wanting to use Amarok.

Just to be sure, I made sure that the packages 'packages amarok-xine, libxine-extracodecs, libxine-main1' were installed in Synaptic Pkg Manager, they all were, but I reinstalled them to be sure. Xine was the engine that was in use in the Amarok Preferences. I still get no sound in Amarok and sound everywhere else. Help!

I've also typed about every command I could find in similar threads.

Help!

:(

---

### Post by kubilaycan on 2007-09-15
when i first installed ubuntu i had the same problem.. although i had all the codecs and were able to play anything on other media players, amarok just kept silent, but i knew it was actually able to play too, cuz i saw the equalizer moving. there was just no sound.. 

i found out the problem was to set the default sound card to my main soundcard, my audigy. i have 2 other soundcards (usbphone, onboard), and at each reboot, it would choose a random one as default. i figured that out because after many reboots sometimes amarok would actually play, but then after a reboot it wouldnt anymore..

anyways, i dont know if this is the same problem as yours, but if it is you should to go synaptic package manager and search for "default sound card" and install the package. then in system>>pref u will see default soundcard, and just choose the right one.

hope this helps

---

### Post by monkiewithpants on 2007-10-29
Thanks for this solution. I had the same problem. I am using a Sound Blaster Audigy but I also have onboard sound I don't use. Installing the default chooser solved all my problems: system startup sounds, Youtube, and Amarok.

---

### Post by cleopete on 2008-07-12
Thank you for ending three days of madness.  It works! It doesn't work! It works! It doesn't work. I think I will shoot my self in the head.  

This is the first time I've installed Ubuntu on a system with a discreet sound card.  I just could not comprehend how the problem could come and go without changing a freakin' thing.  I've not been that long free of Windows, sure the registry is a nightmare but the Device Manager is a sugary teat to give up.

By the by, can anyone explain why the other players weren't hosed too? 

I still have no system sounds. Not a big deal now- I mostly installed Hardy on this box for Amarok.  As long as that works I'm happy... though I'm sure the system silences will begin to gnaw at me eventually.

---

