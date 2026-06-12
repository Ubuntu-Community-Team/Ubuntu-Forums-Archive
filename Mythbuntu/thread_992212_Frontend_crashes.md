---
title: "Frontend crashes"
date: 2008-11-24
forum: Mythbuntu
---

### Post by EdLesMann on 2008-11-24
Hello,
I was using an old 7.04 installation of MythTV and never really had a problem. However, I really needed more hard drive space so I thought I would upgrade. I did fresh installations. My hardware should be listed in the log files below.

I bought a new AMD X2 system and put 64bit 8.10 Mythbuntu (backend & frontend). It worked well for about a week, I saw no major problems. I named this NightWing.

After the rebuild I had not been using the old frontend in the living room so I decided to upgrade and add it (fresh install); it is now a 32bit 8.10 Mythbuntu install. I named this one DarkWatch.

Since I added DarkWatch, I have issues. Two big ones.

The first is with DarkWatch. Every once in a while (meaning I can not easily duplicate it, but if I mess with it long enough I can) when I am browsing the recordings I get messages that it can not find some shows. For example, there was a 2 part episode of the Unit. It couldn't find the first part, but the second played just fine. NightWing had no issues playing the files. Another example is a South Park episode that I could watch but if I tried to delete or view the other options I got a message saying it couldn't be found. I looked in the logs and the only thing I saw of interest to me was that Network Manager was making DHCP requests about every 15 minutes. I have no idea why. So I set reservations in the router (they are working), and I un-installed network-manager for both systems. It made no difference although it is no longer asking for DHCP all of the time. Again, I have not been able to duplicate these issues on NightWing, just DarkWatch.

The second problem is while watching a show. This happens on both systems now. It will be playing the video just fine, then the frame freezes and the frontend will either be completely locked up or after a few minutes it will just die (kicks me back out to the desktop). In both cases, I am still able to SSH into the system or Ctrl-Alt-F1 to a terminal. The system is not locked up.

A few minutes ago I was watching a South Park recording when the frontend on DarkWatch froze. I went to check on NightWing and found it sitting at the desktop ( I had checked before I started watching. The frontend and backend had been running). I gathered the log files with the log grabber utility:

NightWing is the frontend/backend: [http://mythbuntu.pastebin.com/f74b51517](http://mythbuntu.pastebin.com/f74b51517)
DarkWatch is the frontend in the Living Room: [http://mythbuntu.pastebin.com/f59cea667](http://mythbuntu.pastebin.com/f59cea667)

I have done everything I can think of and just about everything I have found on the net that I think it related. Spent all of yesterday working on it. I just don't know where to go from here. I am hoping a fresh set of eyes can spot something I am missing.

Can anyone help me please?

Thanks!

---

### Post by ian dobson on 2008-11-24
Hi,

What are your temperatures like?

The "when I am browsing the recordings " error sounds like a network problem. Try reducing the network speed to 100mbit using 

sudo ethtool -s eth0 speed 100 duplex full

when eth0 is your network card.


Regards
Ian Dobson

---

### Post by EdLesMann on 2008-11-24
The temperature range in the box is between 37-45C.

Also, I just caught it happening again and was able to grab the logs within seconds of it happening. 

[http://mythbuntu.pastebin.com/f6f0c83bb](http://mythbuntu.pastebin.com/f6f0c83bb)

It is the first time I have caught a segfault with these problems. Here is one of the messages.

kernel: [ 5224.884144] mythbackend[5341]: segfault at 20 ip 0000000000427578 sp 00007fffdd5456e0 error 4 in mythbackend[400000+111000]

Thanks for responding!

[Edit] The temperature range is for the case, the 2 CPU monitors, and all of the hard drives. So I am pretty sure that it isn't over heating.

---

### Post by EdLesMann on 2008-11-24
Got something else that I had not caught before. I don't think this is a frontend problem after all. I am now thinking it is a backend problem that I just overlooked before.

It just happened again and I caught this in the mythbackend.log but it doesn't show up in the log grabber.

[http://mythbuntu.pastebin.com/m5fd6ac46](http://mythbuntu.pastebin.com/m5fd6ac46)

It looks like glibc is causing the problem. Any ideas?

Thanks!

[EDIT] It seems to be happening more frequently (EG: easier to trigger now). I also found this in the log files:
*** glibc detected *** /usr/bin/mythfrontend.real: malloc(): memory corruption (fast): 0x00007f2e30096def ***

I have already started running memcheck.

---

### Post by EdLesMann on 2008-11-24
2 passes with Memtest v2.01.
No errors found.

I am running out of ideas. Can anyone help me please?

Thanks!

---

### Post by EdLesMann on 2008-11-27
I have disabled the Nvidia drivers and it is happening less often, but it still happens.

Any ideas please?

---

### Post by EdLesMann on 2008-12-03
Wow! Thanks for all the help guys!!

Anyway, if anyone else happens to have the same issues here is what I found.

I had formatted my recordings drive as JFS with the mythbuntu 8.10 install. I did nothing special with that drive. Just simply selected JFS at the install screen. I found that it was /extremely/ slow. I mean way way /WAY/ slow on reading, writing, deleting, and everything. So I reformatted it manually as ext3 and that solved /all/ of the latency problems with the recordings. Frontends stopped crashing as well. I am guessing there were timeouts or something. Not sure. But a good chunk of my problems went away right off the bat.

However, I still had the crashing of the backend. This was sporadic and I couldn't reproduce it as easily once I changed file systems (I think JFS was screwing with it too). However, it was still happening with enough frequency that it really bothered me. So I backed up the SQL and recordings and I wiped the drive clean. Started over with a fresh install. Same thing. So then I wiped the drive again and started over with 8.04.1 and for the last ~week it has been rock solid on the backend.

The only "problem" I have now is every once in a while when I try to play a recording I get a (paraphrased) "This recording is not available. It may have been deleted." Error message. If I back out of the menu and go back to the recording it plays just fine. I have not had a chance to research this error yet.

I sent log files of the front and back end crashes to a couple of lists and forums. No one seemed to care. So if your backend keeps crashing on 8.10, go back to 8.04.1 cause apparently no one cares about 8.10...oh and stay away from JFS!

[EDIT] Clarification on time. 
Right after my last post above, I waited several hours and got no reply from anyone that I asked for help. That is when I started experimenting. I did the 8.04.1 install, worked on that for a while and now I have a 4 day uptime on the current install. So my ~week is really only like 5 days, but that is still 5 days working compared to the hourly crashes from before. Significant difference in my book.

---

