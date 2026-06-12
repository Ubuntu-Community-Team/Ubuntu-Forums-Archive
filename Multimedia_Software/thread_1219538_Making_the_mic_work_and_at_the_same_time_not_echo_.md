---
title: "Making the mic work and at the same time not echo in the headphones"
date: 2009-07-21
forum: Multimedia Software
---

### Post by siddartha on 2009-07-21
So I finally solved the micboost problem with alsa mixer. Now I'm lost. There is a way to make the mic not echo in the headphones while it can still record. But which?

---

### Post by igorzwx on 2009-07-22
perhaps, some meditation...
do you have pulse?

---

### Post by siddartha on 2009-07-22
9.04 w pulse

---

### Post by igorzwx on 2009-07-22
if you feel very experimental, you can try this.

install another Ubuntu 9.04 in dual boot.
remove pulse
blacklist alsa modules
install OSS4

[http://ubuntuforums.org/showthread.php?t=1139404&page=6](http://ubuntuforums.org/showthread.php?t=1139404&page=6)

---

### Post by siddartha on 2009-07-23
Hehehe
Nice idea, but I won't go that far for Skype. Anyway it's faster to go to the nearest shop and buy Windows in order to have multimedia working.
I've been single boot on Linux before Win'98 was out. Lately I see all the problems of programming that were in the Windows camp back in '95 are all in the Linux camp.

I thank you for your answer, because I almost forgot the two bit decisions made by Ubuntu. This is the essence of Linux alltogether. Back in the 90s NFS support was broken because the Linux team made some cool changes and broke the compatibility with the rest of the *nix world, a respectable world I might add. Working their way on the same path Ubuntu drops OSS to ALSA, drops esd to Pulse and everything new and cool just for the sake of mindless change. PDF output is castrated, but hey! we have a nice bubble popping up with the news. The tablet support is broken, but you don't need that, after all all the pros work with 16bit color use other platforms. This is the system that caters for cheap Chinese systems made on some boat... but remember to check with great attention the driver list as we probably won't support all you have.

Sorry for the long answer. So the solution is NO. And enabling mic boost is also something for the pro who is able to start the terminal, install the alsa mixer and mess with the curses interface. Come to think about it MacOS is not that expensive and offers a true "task bar" not 20 half-baked projects who mimic it badly without adding anything new.

---

### Post by igorzwx on 2009-07-23
nothing is perfect in this world, you know.

I solved my problems by OSS4.
Tomorrow, might be other problems.

Both Windows and Mac are not perfect too.

---

### Post by siddartha on 2009-09-05
> **igorzwx said:**
> Both Windows and Mac are not perfect too.

Actually they work. Win95 was less stable than Linux. The recent ones are of comparable strenght. People forget the fact that a decade ago it was "us vs them". Some apps cross-compile. And the ones that don't usually are on the Windows side.

---

