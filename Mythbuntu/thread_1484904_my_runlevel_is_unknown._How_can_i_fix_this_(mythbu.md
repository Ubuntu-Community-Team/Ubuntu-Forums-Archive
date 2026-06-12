---
title: "my runlevel is unknown. How can i fix this (mythbuntu 10.04)"
date: 2010-05-16
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-05-16
Hi guys, apache doesnt always start on my system and i think the reason is because my runlevel is 'unknown' according to /sbin/runlevel. Is there a way i can fix this permanently, i can change the runlevel for that session, but it goes back to unknown when i reboot. What runlevel should it be?

---

### Post by spacebug on 2010-05-16
Hi!

I'm running ubuntu 10.04 Lucid and today I saw I also was in runlevel unkown.
I tried to reboot but still came to runlevel unknown.
I don't know if this was after a "aptitude safe-upgrade" I did, but to fix this I did:

1) Switched to runlevel 2 by issuing "init 2" in a console.
2) Reinstalled my kernel by issuing "aptitude reinstall linux-image-2.6.32-22-generic-pae".
3) Then I restarted my system from within gnome and then I was back in runlevel 2.

---

### Post by bergqvistjl on 2010-05-18
> **spacebug said:**
> Hi!

I'm running ubuntu 10.04 Lucid and today I saw I also was in runlevel unkown.
I tried to reboot but still came to runlevel unknown.
I don't know if this was after a "aptitude safe-upgrade" I did, but to fix this I did:

1) Switched to runlevel 2 by issuing "init 2" in a console.
2) Reinstalled my kernel by issuing "aptitude reinstall linux-image-2.6.32-22-generic-pae".
3) Then I restarted my system from within gnome and then I was back in runlevel 2.
OK, why pae on the kernel, though, (not sure what pae means, i assumed we were using the generic kernel).

---

### Post by bergqvistjl on 2010-05-19
OK well for other reasons i've done a reformat, first thing i typed in when it booted up for the first time was to check my runlevel and it still says 'unknown', so its obviously a more major problem than i thought.

---

### Post by jonas_t on 2010-06-03
> **spacebug said:**
> 
I'm running ubuntu 10.04 Lucid and today I saw I also was in runlevel unkown.
I tried to reboot but still came to runlevel unknown.
I don't know if this was after a "aptitude safe-upgrade" I did, but to fix this I did:


I clean installed today from wubi and also had this problem. dunno what messed the config up in my case as the system is just fresh (except some package installing to get all macbook features).

> **spacebug said:**
> 
1) Switched to runlevel 2 by issuing "init 2" in a console.
2) Reinstalled my kernel by issuing "aptitude reinstall linux-image-2.6.32-22-generic-pae".
3) Then I restarted my system from within gnome and then I was back in runlevel 2.


I ommitted step 1, just reinstalled the current kernel and rebooted. all is fine now. So from my perspective this thread could be marked as RESOLVED. :)

---

### Post by jonas_t on 2010-06-03
> **bergqvistjl said:**
> OK, why pae on the kernel, though, (not sure what pae means, i assumed we were using the generic kernel).

"pae" stands for "physical address extension" and can be used when running a 32bit os with more than 3gb of ram...(if the hardware suppports it). user processes then still can use only 32bit address space but the whole system can address more ram.

---

### Post by slamhound on 2010-06-03
If it is the same problem that I had, then there is an upstart bug that is responsible:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

If it is due to this, the problem may come back for you, as it seems to be intermittent.  There is a workaround in the bug thread.

---

### Post by xinix on 2010-06-10
I was having a similar problem booting into an unknown runlevel.

It seems to have something to do with the network interface not loading.  In my case I had a typo that needed correcting in the /etc/network/interfaces file.  Make sure you have these line in that file```
auto lo
iface lo inet loopback
```

---

### Post by jonas_t on 2010-06-19
hum... the problem just re-appeared so slamhound seems to be right: reinstalled the kernel was  just an intermittent fix. however, the thread on launchpad does not seem to include a real fix - there are several persons still having problems after applying the "fix". sigh... seems that we have to wait for a fix from the devs.

---

### Post by Tteddo on 2010-06-19
I had a disappearing printer problem caused by the same thing. 
This post fixed it for me:
[http://ubuntuforums.org/showpost.php?p=9213567&postcount=7]("http://ubuntuforums.org/showpost.php?p=9213567&postcount=7")
Here's the whole thread:
[http://ubuntuforums.org/showthread.php?p=9213567]("http://ubuntuforums.org/showthread.php?p=9213567")
My runlevel comes back N2 now.

---

