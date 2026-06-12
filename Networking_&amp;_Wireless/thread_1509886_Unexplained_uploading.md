---
title: "Unexplained uploading"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by julian.irwin on 2010-06-14
Hey, Ive been running Lucid since it came out and everything was very smooth until a few days ago when I noticed a major slowdown in my internet speeds (I used speedtest.net and a few others to confirm my slow speeds).

I noticed that  when i open up the system resources window, my upload indicator is showing consistent usage between 60 and 80 Kb/s. Even if restart the computer and open no applications, I still see the upload speeds.

Is this spyware or a virus? I havent been using protection software. 

Is there a utility that would allow me to see what programs are hogging my connection with these mysterious uploads?

---

### Post by wilee-nilee on 2010-06-14
> **julian.irwin said:**
> Hey, Ive been running Lucid since it came out and everything was very smooth until a few days ago when I noticed a major slowdown in my internet speeds (I used speedtest.net and a few others to confirm my slow speeds).

I noticed that  when i open up the system resources window, my upload indicator is showing consistent usage between 60 and 80 Kb/s. Even if restart the computer and open no applications, I still see the upload speeds.

Is this spyware or a virus? I havent been using protection software. 

Is there a utility that would allow me to see what programs are hogging my connection with these mysterious uploads?

Top in the terminal will give some info, install htop and see more and be able to control it. As far as virus or malware, run the live cd and see if it does the same upload, after checking with htop.

---

### Post by mikewhatever on 2010-06-14
You could try **sudo netstat -tupn**

---

### Post by donato roque on 2010-06-16
hi. 
also check the list of startup applications.  Applications like dropbox and sync apps might be starting at boot.  
Another program to watch is UbuntuOne.  It is integrated with Rhythmbox so if you are running this player it could be connecting to its servers.
Question is-- Is it uncontrollable?  If you disconnect from the network and then connect back, does it continue on?

---

### Post by julian.irwin on 2010-06-19
It was UbuntuOne! I just signed up for it a week ago. I checked online and my whole 2 gigs were filled with part of my music library. I never told it to sync my music though. Does it do that automatically? It shouldn't, as that is useless and confusing. I would rather put important documents up there, not music.

---

