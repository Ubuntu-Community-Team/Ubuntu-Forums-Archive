---
title: "partial lock on mythbuntu 10.04"
date: 2011-10-10
forum: Mythbuntu
---

### Post by linuxhippy on 2011-10-10
I am running mythbuntu 10.04 with all the upgrades.  On a fresh boot it cannot get a lock on the channels I've set up.  I've found that this gets a lock on channels to watch: 

close the mythtv frontend, go into the mythtv backend setup, exit without doing anything, and then re-start the frontend.

The problem is that I have my pc BIOS timer set to turn on while I'm not home, so it may not be able to record programs till I get home and do the above procedure (a password is needed).  

So how do I fix it?  This doesn't happen in mythbuntu 11.04 (I dual boot mythbuntu 10.04 and mythbuntu 11.04).

---

### Post by klc5555 on 2011-10-10
When Ubuntu started pushing toward extra-zippy startup times in recent versions, there began to be an occasional problem in Mythbuntu with mythbackend starting before the tv tuners had managed to load their drivers and initialize properly. You can see if this is your problem by cold booting (as you have been), then just stopping and restarting mythbackend (without touching mythtv-setup at all), and your machine should function normally. 

If this is indeed your issue, you can check old threads in this forum where a couple of different workarounds have been tried. Some have relied on putting a sleep delay in one or another startup script to provide an extra delay for mythbackend's start, so that the tv tuners have more time to load and initialize; while others have preferred a script to stop and restart the backend once the tuners have loaded. The better approach depends on your particular machine.

---

### Post by linuxhippy on 2011-10-10
I was thinking it was something like this-thanks!

---

### Post by shad0w_walker on 2011-10-10
Just as another point to make here. I had a problem with channels only getting a partial lock. My solution ended up being to turn 'use quick tuning' to always and it cleared up nicely.

---

### Post by linuxhippy on 2011-10-10
interesting...I'll try that!

---

### Post by sqeelurgle on 2011-10-13
A few things I have done to fix partial lock problems:

plug in the antenna (I kid you not I have found an unplugged antenna)

Delete all the channels and re-scan

Manually edit the transports (I had one tuner that would tune a channel at frequency 585625000 if the defined frequency was 585625000 in one version of myth, and 585500000 in another version

Add extra time to the timeout lengths in the capture card part of the backend setup (I think the defaults are 1000ms and 3000ms - I increased them a lot with one tuner and it worked

---

### Post by toddk111 on 2012-04-26
> **shad0w_walker said:**
> Just as another point to make here. I had a problem with channels only getting a partial lock. My solution ended up being to turn 'use quick tuning' to always and it cleared up nicely.

I had this problem with some channels and was getting extremely frustrated trying to figure it out.  I'm so grateful for your quick fix!
Thanks!
-Todd

---

