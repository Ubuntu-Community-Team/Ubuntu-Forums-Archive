---
title: "Nvidia drivers question"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by uputer on 2007-07-29
I read somewhere that only Nvidia video cards up until 7600 are covered in Linux or in other words, only those ones will work and have drivers.   

I went to Nvidia's site and I thought I read of drivers being available for 8600 and maybe 8800 now?   Anyway, I need to buy a new video card (soon) and I wondered what to get so that I can use Ubuntu.   This is for another computer (build), btw.   Anyway, I just need confirmation of what works and if certain cards pose potential problems or issues (incl. drivers issues).   

I was looking at either 7600 or 8600 cards, btw.   I have found decent deals for either card but I want to know whether they work okay in Linux.   I prefer not having to compile or do complicated 'fixes' since I'm a newbie.   I can do some procedures but I might need assistance for really complicated processes.   

Thanks in advance for any replies and/or info.

---

### Post by MrCuddles on 2007-07-29
My recent experience has shown that, at least in my build, the 8800gts works, and easily, but only one. I can't get SLI going, though I doubt it's impossible. I'm still trying to figure it out. The single card setup worked with both Envy and using the latest driver from nVidia's website, despite the 8800gts not being listed as compatible hardware. As far as related hardware goes, it's plugged into an Asus Striker Extreme with an Intel Conroe dual core cpu. If you're looking for an easy way to do it, using Envy is probably about as easy as it gets, although using the driver from nVidia's website only took 3 commands for me. Turn off X, sudo sh NVIDIA-...-.run, turn on X, and away I went.

---

### Post by mrazster on 2007-07-29
I have used nvidia cards from 7600 all the upp tol 8800GTX...usind driver both from the repos and using Envy script....and it all worked fine.
Currently using a 7900GTO 512mb with kernel 2.6.22 and nvidia driver ver. 100.14.11 installd with Envy script....works like a peach.

---

