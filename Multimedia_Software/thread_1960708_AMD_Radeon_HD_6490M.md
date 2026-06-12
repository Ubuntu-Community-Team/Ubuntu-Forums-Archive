---
title: "AMD Radeon HD 6490M ??"
date: 2012-04-17
forum: Multimedia Software
---

### Post by Jackhamma on 2012-04-17
Right: I'm having an issue installing the proper video card drivers for my Macbook Pro (I forget which gen it is... either the newest or the 2nd newest generation) on Ubuntu 11.10. Tried installing them via the "Additional Drivers" tool, but when I restarted the menu bar and menu items in the GNOME 3 shell were all glitchy and nasty and such. Tried to log out and log back on to the regular Unity desktop and it only showed the desktop wallpaper and my mouse cursor. I ended up having to go into recovery mode and into the command line from there to fix things. 

My MBP has an Intel card of some sort (not sure what it is, how do I check that?) and that's what's been running everything so far, and it just ain't cuttin' the mustard. I've Googled a bunch trying to find a fix, but I'm only finding either outdated info or people saying "It just doesn't work.". Is there a fix for this or no? If there is: any idea how to implement it?

Possibly related: My lappy runs incredibly hot while watching YouTube videos. Is that a symptom of the graphics card thing or probably a different matter entirely? 

Thanks!

PS: I'm very new to all of this so the simpler the terms the better!!

---

### Post by Jackhamma on 2012-04-18
Figured it out! I followed these instructions to the letter for the 'manual install'. 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Turns out I was misreading one of the commands. I thought it said 'aticonfig --install', but it's 'aticonfig --initial'. Things seem to be working fine now!

---

### Post by seicean on 2012-07-20
same issue here with a Probook 4530s. After following the instructions listed in the wiki, are you able to switch between GPU's??? Thanks in advance.

---

