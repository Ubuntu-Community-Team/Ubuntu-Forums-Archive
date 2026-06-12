---
title: "intel integrated + nvidia problems"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by RAKninja on 2007-04-26
hello all, really love how efficient ubuntu is and everything, but i'd like it even more if i could make use of my gfx card.  I am forced to select "integrated" for my GFX controller in BIOS, otherwise linux will not even boot to a CLI (page faults at almost exactally 3 bars loaded on the splash screen.  

on top of that, I'm having the typical NVIDIA driver problems with my GeForce 6200 (pci).  though much work and tweaking, i got X to recognize the card, and even start transmitting to it, but the GFX controller is still integrated, and I'm not showing GLX.  the main reason i selected ubuntu as my GNU/Linux distro is its compatibility with beryl, but i cannot run beryl without my card bieng installed correctly first.

oh yes, i've been at this for about 5 days now, almost non-stop.  i have tryed EVERY english language fix that you can get from google. nothing so far.

i even went so far as to burn a 6.10 disk, and try that.... turned out worse than 7.04 (because at least 7.04 documentation pops up on internet seaches.

Well i just reinstalled 7.04 again.. im done untill someone has a fix.

---

### Post by RAKninja on 2007-04-27
allright, i got my machine recognizing and using Nvidia drivers, am using the card, but still i am set in BIOS to integrated graphics control, and setting it to "PCI" causes linux to crash (just at three full bars on ubuntu splash, its before the command prompt if started in recovery.  is there a file with a log created for a failed boot to post here?

also is there a standard fix to get the integrated disabled?

it's a intel 845G motherboard (originally part of a dell dimension 2350, still using dell A1 bios) and am using a geforce 6200 on PCI slot 1:4:0 (integrated graphics is pci  0:2:0)

---

### Post by RAKninja on 2007-04-27
just to reiterate, the fix at [http://ubuntuforums.org/showthread.php?t=192677&highlight=nvidia+intel](http://ubuntuforums.org/showthread.php?t=192677&highlight=nvidia+intel) did not work.

---

### Post by RAKninja on 2007-04-28
any thoughts or ideas?

---

### Post by RAKninja on 2007-04-28
no one knows why its overriding my blacklist or where to find a crash log? thats really wierd.

---

### Post by RAKninja on 2007-04-28
hello? anyone? where to find a crash log? it really shouldent be this hard to find, and im not seeing how to find it...

---

### Post by RAKninja on 2007-04-28
another bump

---

