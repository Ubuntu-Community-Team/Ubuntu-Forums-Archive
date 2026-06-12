---
title: "Wifi takes a minute before it tries to connect after boot/suspend"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Felliph3 on 2010-10-16
Hello there, this is a problem that I had before and fixed it but I can't find out how again.

Basically when I login back from a suspend or after I boot the pc, the wifi takes 30seconds to a minute before it starts to connect. This makes it very annoying to have to wait for no reason.

Basically the issue is caused by the wifi not having a script to search for a network after a suspend.

Any one can help?

HP Pavillion DV9000 Fresh install of Maverick 10.10

You guys rock :guitar:

---

### Post by TheSe7enthSin on 2010-10-17
I seem to be having the same issue. I have to right-click the wifi icon & disable wireless. Once I re-enable it, the connection will work correctly. It's annoying having to do this. Any solutions?

---

### Post by Felliph3 on 2010-10-18
Yeah, bump!

---

### Post by Felliph3 on 2010-11-19
upppp

---

### Post by grahammechanical on 2010-11-19
Try System>Preferences>Startup Applications. Select the Options tab and click Remember Currently Running Applications. This may work. This suggestion was discovered by another forum member. I have tested it on my desktop machine with suspend and hibernate. Without it network manager does not list Available wireless networks.

regards.

---

### Post by Felliph3 on 2010-12-03
Does not work either but thank you for the suggestion. Any one else?

---

### Post by TiBaal89 on 2010-12-03
I've got the same issue in Fedora 14 on my MBP... I don't find it ridiculously annoying, but it would be nice if it wouldn't do that.  ;)

---

### Post by Felliph3 on 2010-12-04
Yeah it sux.

---

### Post by Felliph3 on 2010-12-24
Upppppp. Im pretty sure Im not the only one having this issue. It has always been there regardless of which computer I use and it makes every other OS seem that much better. This is a big letdown that I have to wait a minute before using the internet everytime I get back from a suspend or a boot.

---

### Post by ottosykora on 2010-12-26
I have it on 3 laptops, operating more then two OS each and it is in every OS so. w7, XP, w2k, ubuntu, fedora, debian

So I got used to that.

---

### Post by Felliph3 on 2011-01-03
upppp

---

### Post by movieman on 2011-01-03
I seem to be having the same problem, starting a few days ago. The worst part is that when this happens, some of the gnome applets crash, I get switched from ondemand to performance mode, and a whole bunch of services don't seem to get started... setkey, portmap and cupsd, for a start.

So after it finally does connect I have to restart setkey, racoon, portmap, autofs and cupsd in order to have a usable network.

---

### Post by Felliph3 on 2011-01-03
Interesting. I always had problems with the cpu frequency scaling not doing what I told it to and they finally fixed that in Maverick. This sounds like a laptop specific problem. Google results don't really show anything about this.

---

### Post by walt.smith1960 on 2011-01-03
Something easy to try.  I sometimes see this when resuming after suspend, I don't think I've ever seen it after a cold boot.  Once the notebook resumes and the wireless doesn't connect, try logging out then logging right back in. Frequently that works for me and might help to isolate the problem.

---

### Post by movieman on 2011-01-06
I seem to have solved mine: I noticed the battery applet was claiming the battery voltage was 67V, which was clearly nonsense, so I shut down and pulled the battery out for a couple of minutes to ensure the laptop got a complete power down, and now it seems to be working. I guess something had got screwed up which couldn't be fixed without a hard power down.

---

### Post by Felliph3 on 2011-01-07
Funny symptoms! My battery applet works but it doesnt show the battery % or time remaining. 

I also fixed sorta fixed mine. I installed a 32bit version on a test partition I have and the wifi just works once I installed it connected to the internet. I did the same thing before when I installed mt 64bit but it doesn't work(let it install while connected to the internet).

On the 32bit I can turn off, suspend, etc and the wifi fires up madd quick. The way it should be. Takes less than 1-2 seconds to connect.

I'm just going to scrape my current 64bit installation and install a 32bit on my big partition.

---

