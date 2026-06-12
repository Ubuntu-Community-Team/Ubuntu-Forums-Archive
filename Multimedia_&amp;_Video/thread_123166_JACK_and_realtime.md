---
title: "JACK and realtime"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by christhemonkey on 2006-01-29
Hi
i would love to get JACk working with realtime capabilities,
but if i try running it as any other user than root, it says:

```
jack_create_thread: error 1 setting schedular parameters after thread creation:
Operation not permitted
cannot start watchdog thread
cannot load driver module alsa
```

that was for
```
jackd -R -d alsa
```
if i run as su though, it runs fine; although my audio applications cannot connect to it as they are run as my user.

I have the realtime-lsm module installed and loaded.
Help!

---

### Post by FarEast on 2006-01-29
Hi christhemonkey,
Have you installed the package 'realtime-lsm' which contains a script
to load the module 'realtime'? (I ask you just in case.)
Are you a member of the group 'audio' (gid=29)?
If OK, then install 'qjackctl' with apt and try tweaking options with it.
[http://qjackctl.sourceforge.net/](http://qjackctl.sourceforge.net/)

---

### Post by mpvano on 2006-01-30
Your forum personalization information says you're using Ubuntu 5.04. I don't believe that the standard kernels in that distribution will work properly with the realtime-lsm without building a special kernel.

If you've just got an out-of-date info header and are actually using breezy, then it should work, but you may not have everything you need installed correctly.

You need to correctly (!) install:

1. realtime-lsm-source
2. realtime-lsm

Once you install realtime-lsm-source you need to build it. If you haven't done so already, you will need to install the following to build it properly:

1. build-essential
2. module-assistant
3. gcc-3.4
4. any other dependencies that these packages require.

Then, 
run sudo module-assistant and use the menus to
[INDENT]update
prepare
select realtime-lsm
get
build
install[/INDENT]
review /etc/default/realtime settings
restart

I've sometimes had to run module-assistant twice to get everything to work without errors - I think this happens if it needs to download some extra dependencies.

I've followed this procedure on two different systems now and it worked well.

Note again, however this only works on 5.10 - you're out of luck on 5.04 unless you really understand how to build a real-time kernel and manually install realtime-lsm properly.

(Note that you DID ask the question in the "Breezy Badger Hardware help" subforum thread section...)

hope this helps,

Mario

---

### Post by christhemonkey on 2006-01-30
looks like im upgrading to breezy then...(my bad!)

---

### Post by christhemonkey on 2006-01-30
Its all going well, except that it keeps saying things about cant find correct locale for perl bits and bobs, resorting to original (C).
Any thoughts?

---

### Post by mpvano on 2006-01-31
Oops, I should of warned you that doing an upgrade from the mirrors to breezy can be a little painful. I didn't realize you'd apply that direct a solution.

If it's any help, I did that to two machines and both ended up working fine, but it was pretty scary because a lot of the updates appeared to fail. Just keep running update over and over. Each time I did that it would fill in more of the pieces that failed on earlier runs until nearly everything was back to normal.

The only other problem is to make sure you update your mirror lists to catch all the packages that are not in the base repository, or they won't get updated - they may just get REMOVED.

Beware - If something is removed for this kind of reason, Debian distributions will often remember that they need to reinstall the conflicting package once they see a new one that works. Be VERY cautious about trying to solve the problem manually by deleting packages and manually installing them - doing this will break the automatic fix that usually handles the problem later when you add the missing repositories.

I don't know if that made sense, but I wasted a lot of time the first time I did an upgrade to breezy hunting for and fixing broken dependencies that apt-get was perfectly willing to automatically repair if I had just been smart enough to make sure all the repositories I used in the old version had corresponding breezy repositories listed.

Good luck - I'm sure you'll get it sorted out, but do be aware it's not the smoothest update I've ever seen....

Mario

---

### Post by christhemonkey on 2006-01-31
Seems to be doing just about ok now, is setting up everything now (the 2nd time round, very odd!)

I needed to get on the internet though and as usual ubuntu forums was the place to get help :D

by the way, what finally got it to work was to do
sudo apt-get install -f

which fixes all broken dependencies etc, no more downloading package for 2 hours for me!

---

