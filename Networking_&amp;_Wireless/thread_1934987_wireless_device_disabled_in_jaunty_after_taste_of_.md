---
title: "wireless device disabled in jaunty after taste of mint"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by nbloomis on 2012-03-03
hello,
i have an acer netbook that i got handed down to me in a bunch of pieces.  i drive it with a seagate freeagent external hard drive velcroed to the back.  i started using ubuntu a few years ago because i needed an OS that i could run externally.  I love the Jaunty Jackalope, and have tried other updates but I don't use the computer very often and version 9.04 is low on bells-and-whistles and high on usability for me.

-to the point----i recently heard about linux mint, and thought i would check it out because of what i read about its usability.  i burned the dvd, booted from my external dvd drive, and poked around a little.  i didn't care much for it, so i just went back to booting normally (ext hdd) and BAM! my wireless device stopped detecting any networks!  and it was perfect before my 'taste of mint', and now im screwed because i want to keep using an unsupported version of ubuntu but i am not skillful enough to manage the kernel? or something down deep in the guts of my duct-taped hardware.

i didn't change any settings when i was in Mint (Lisa 12).  i even reformatted the entire partition and reinstalled Jaunty to no effect.  any ideas on what happened?? and has my proto-technological pirated free-source world been destroyed forever?

Peace and love to all,
Nathan

---

### Post by chili555 on 2012-03-03
> i drive it with a seagate freeagent external hard drive velcroed to the back.I love it!!! 

This sounds, believe it or not, fairly simple. Let's see what wireless device you have. Open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep acer
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by mörgæs on 2012-03-03
9.04 is out of support and hence a security risk. I would recommend that you begin installing 11.10.

If Ubuntu is too bloated for you, L/Xubuntu are worth trying.

---

### Post by nbloomis on 2012-03-03
wow thanks chili555 for trying to help me out!
here is the cut and paste:

nathan@nathan-laptop:~$ lspci -nn | grep 0280
nathan@nathan-laptop:~$ rfkill list all
bash: rfkill: command not found
nathan@nathan-laptop:~$ lsmod | grep acer
acer_wmi               24260  0 
led_class              12036  2 ath5k,acer_wmi
nathan@nathan-laptop:~$ 

the rfkill i guess i dont understand, ive tried that before after reading other threads and i always get command not found.

if im not mistaken the ath5k driver looks good, so what's next?

morgaes i might have to go that road eventually but security isnt a huge priority for me and i would like to return to my previous status quo if possible.  what is Xbuntu, like a bare-bones version?

thanks three times to all

---

### Post by nbloomis on 2012-03-03
whoa ok im back in  business.  all my networks are back up and im connected. what a slap in the face, thanks chili!
so what happened?

---

### Post by mörgæs on 2012-03-03
> **nbloomis said:**
> what is Xbuntu, like a bare-bones version?



Yes, basically. Same applications, just a lighter desktop environment.

You can get the ISO from the link in my signature or see a demo on Youtube.

---

### Post by chili555 on 2012-03-03
> **nbloomis said:**
> whoa ok im back in  business.  all my networks are back up and im connected. what a slap in the face, thanks chili!
so what happened?I haven't any idea, but a solved is a solved by whatever means. Post back if it doesn't stay fixed.

---

### Post by mörgæs on 2012-03-03
- and if it does, please mark the thread 'solved'.

---

### Post by nbloomis on 2012-03-04
thanks ...how do i mark 'solved'.?   duh..

---

### Post by chili555 on 2012-03-04
Go up to the top and use [COLOR="Red"]**Thread Tools**[/COLOR] to Mark Solved.

---

### Post by nbloomis on 2012-03-04
ok all set. thank you mr morgaes and mr 'wilder'.  see you next crash.

---

