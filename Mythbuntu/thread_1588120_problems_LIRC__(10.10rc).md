---
title: "problems LIRC  (10.10rc)"
date: 2010-10-04
forum: Mythbuntu
---

### Post by xinix on 2010-10-04
My HD crashed this weekend (came home to the tick of death and scrolling I/O errors) so I figured I'd jump on the 10.10rc wagon since I was doing a fresh install anyways.

For the most part things are working as expected except for LIRC.  I can get it to work but there are a couple problems.  

The main one makes it almost unusable.  I have to wait about a second between key presses.  This makes scrolling menus a real pain.  IRW responds instantly so I'm guessing it's a mythtv thing.

The second is that irrecord will only work if I force raw mode.  The lircd.conf file this generates will work but it would be nice to have the cleaner file.  Especially since it seems that something is off with lirc.  Last time I used it to generate the conf file I had no problems and did not have to force raw mode.

---

### Post by LowSky on 2010-10-04
downgrade or upgrade the verison of LIRC...

sorry can't help much on beta software.. it still has kinks in it.

---

### Post by xinix on 2010-10-04
> **LowSky said:**
> downgrade or upgrade the verison of LIRC...
.

I've tried to use an older version but I cannot get it to build.  I did a "apt-get build-dep lirc" to get all the dependencies but I still get build errors.  I get build error with anything though so I that's another issue.

I'm going to pop in an old livecd and will use that to generate a better conf file. We'll see if that makes a difference.

---

### Post by xinix on 2010-10-04
So it seems that the conf file that the current version of LIRC generates was the problem.

I booted off an 8.04.4 Live cd, downloaded and built from source LIRC 0.8.3pre1 (because I knew for a fact that this gave me a good file) and got a working lircd.conf.

I don't have to pause between button presses anymore.

---

### Post by tgm4883 on 2010-10-04
> **xinix said:**
> So it seems that the conf file that the current version of LIRC generates was the problem.

I booted off an 8.04.4 Live cd, downloaded and built from source LIRC 0.8.3pre1 (because I knew for a fact that this gave me a good file) and got a working lircd.conf.

I don't have to pause between button presses anymore.

Hmm. Would you mind filing a bug against mythbuntu on launchpad

---

### Post by superm1 on 2010-10-04
> **xinix said:**
> So it seems that the conf file that the current version of LIRC generates was the problem.

I booted off an 8.04.4 Live cd, downloaded and built from source LIRC 0.8.3pre1 (because I knew for a fact that this gave me a good file) and got a working lircd.conf.

I don't have to pause between button presses anymore.

I think it would be beneficial if you could file a bug as follows:

1) Run this command:
# ubuntu-bug lirc
2) Attach the lircd.conf that was broken
3) Attach the lircd.conf that was working
4) Make sure to mention the details of the hardware in question

We can try to help review what happened here that things got busted for your particular remote.

I wouldn't say this is a general lirc problem, I know i've personally tested 10.10's support for mceusb2 with no problems whatsoever.

---

### Post by xinix on 2010-10-04
> **superm1 said:**
> I think it would be beneficial if you could file a bug as follows:

1) Run this command:
# ubuntu-bug lirc
2) Attach the lircd.conf that was broken
3) Attach the lircd.conf that was working
4) Make sure to mention the details of the hardware in question

We can try to help review what happened here that things got busted for your particular remote.

I wouldn't say this is a general lirc problem, I know i've personally tested 10.10's support for mceusb2 with no problems whatsoever.

Done, hope it helps.

---

