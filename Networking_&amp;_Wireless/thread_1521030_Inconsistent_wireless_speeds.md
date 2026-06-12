---
title: "Inconsistent wireless speeds"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by moveright on 2010-06-30
I've got a compaq laptop running 64 bit lucid.  Though my wireless works, it's extremely inconsistent.  I first noticed this playing world of warcraft, when I noticed that I was intermittently pinging 1100+ MS consequently ruining smooth game play.  That prompted me to repeatedly right click my network status at the top of the desktop and click "connection information" over and over back to back.  What I noticed was sometime 56mbps and sometimes 1mbps.  

Anyhow, I just automatically blamed my actiontec FiOS router for this and the next day, I got rid of that router and ran a cat5e cable directly from my FiOS ONT to a netgear router.  Checked again, and I still have this weird intermittent issue.  So, now I am curious if it is a hardware issue with my wireless on my laptop, or a software issue such as a crumby driver or whatever.

I did a "lspci -v" and here is the wireless information it supplied me with:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

by the way, my wired lan performance seems to be working solid.

Any ideas?

---

### Post by moore.bryan on 2010-10-21
This has been dead a while... have you solved your problem? I know Atheros chipsets can be notoriously finicky; I have the AR9285 giving me some issues in Maverick now.

Any particular reason why you're using the ath5k driver?

---

### Post by CompShrink on 2010-10-23
Hey Bryan, I had the same issue with inconsistent speed, you might want to try the instructions I wrote here:

[http://ubuntuforums.org/showpost.php?p=10017274&postcount=3](http://ubuntuforums.org/showpost.php?p=10017274&postcount=3)

Good luck.

---

### Post by moore.bryan on 2010-10-24
Interesting... working on this now. There's a typo in the directions, though; the package is "build-essential" not "build-essentials."

Why the *regress* on compat?

Right now, everything seemed to work. You may also want to warn people about possible errors being thrown-up with "sudo make install."
> 
Updating Ubuntu's initramfs for 2.6.31-wl under /boot/ ...
grep: /boot/config-2.6.31-wl: No such file or directory
WARNING: missing /lib/modules/2.6.31-wl
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/2.6.31-wl: No such file or directory
FATAL: Could not open /lib/modules/2.6.31-wl/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/2.6.31-wl/modules.dep: No such file or directory


---

### Post by moore.bryan on 2010-10-24
Okay, here's the latest. Using the 2010-09-12 compat-wireless ath9k driver provided **no** relief after working for the requisite thirty minutes. It got to the point disassociating and reassociating didn't work. I cleared all that out, removed backport modules, and downloaded the bleeding-edge compat-wireless package. After installing that, things are slightly better, but not 100%. This seems to be such a silly thing... there were no problems in the ath9k driver in Lucid; why the step backwards?

---

### Post by CompShrink on 2010-10-24
Sorry it didn't work for you. My card wasn't working properly in Lucid either, so we probably have a different revision or something of the card.

Oh and thanks for catching the typo.

---

### Post by moore.bryan on 2010-10-24
> **CompShrink said:**
> Sorry it didn't work for you. My card wasn't working properly in Lucid either, so we probably have a different revision or something of the card.
No worries... I've had good success for today running the bleeding-edge ath9k. Can't figure-out the root of the problem, though.

[quote=CompShrink]Oh and thanks for catching the typo.[/QUOTE]
It's a great how-to; I didn't want anyone getting hung-up! :-)

---

