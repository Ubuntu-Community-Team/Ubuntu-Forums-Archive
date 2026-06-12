---
title: "Trouble with Nvidia drivers on a Geforce Go 7900 GS"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by tootubular on 2007-11-02
Ok, I've got a Dell E1705 in my possession and decided to give Ubuntu a shot; it's been awhile since I tinkered with Linux. Well, for the most part everything went smoothly aside the blooper PM8 made by hiding the NTFS partition making me sweat... this is my girlfriend's PC! Fixed, swell. So I'm a bit of a fanatic when it comes to graphics drivers and understandably, the jiggles and animations Compiz and Beryl provide are highly desired and proper drivers are a must, as I understand it anyway. On to the problem.

I've been hacking away at every attempt Google and this forum offered, reading each step and understanding the process as much as I could. Even after a full wipe and the Restricted drivers way only, no dice. 

The problem: Anytime I try to load 'nvidia' in my xorg, the screen flashes three times and the failsafe  ensues. I've dug through the log file and found no EE entries. I've tried the official drivers with all other nvidia packages cleaned out, I've tried the restricted driver install approach from a clean install, I've tried nvidia-glx-new. No matter what, the problem ends up being the same, a failsafe xorg loading when the normal xorg loads 'nvidia'. A simple change to 'nv' or 'vesa' fixes the problem naturally, but then I'm at a loss of desktop effects.

At the moment I can't offer any specific log entries or commands I'm using since the computer is being used by its rightful owner, but I'm dying to fix this problem. I've got about 6 hours invested with no solution so it would be glorious to conquer this. I'm willing to try just about anything and know that I rarely post a topic since most data can be found. Perhaps I've missed a spot? I'll be on shortly, hacking away at any file that lends itself to a possible solution.

---

### Post by teknorah on 2007-11-02
Have you tried envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

