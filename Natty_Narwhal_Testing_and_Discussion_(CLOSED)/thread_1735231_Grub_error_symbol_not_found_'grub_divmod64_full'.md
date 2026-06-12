---
title: "Grub error: symbol not found: 'grub_divmod64_full'"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by deancasino on 2011-04-21
After the most recent updates today, I'm now getting error when I try to boot into Windows:

error: symbol not found: 'grub_divmod64_full'
error: no such device: 16DBE82A41F716A1
error: no such disk

Now I thought I was looking at a HDD failure, but when I boot into faithful ol' Ubuntu, the Windows partition is mounted and can be used as normal.

Any ideas?

---

### Post by dino99 on 2011-04-21
uuid have probably changed: 

sudo blkid will return yours to compare

or boot into ubuntu then:
sudo grub-mkconfig
sudo update-grub

---

### Post by deancasino on 2011-04-21
Yeah I've given  sudo update-grub a spin a few times but no luck. As it turns out, the UUID hasn't changed either.

---

### Post by dino99 on 2011-04-21
dont find a lot about this:

[http://bazaar.launchpad.net/~vcs-imports/grub/grub2-bzr/revision/3221](http://bazaar.launchpad.net/~vcs-imports/grub/grub2-bzr/revision/3221)

maybe: sudo dpkg-reconfigure grub-pc

---

### Post by archangelabove on 2011-04-21
I had the same issue when I just completed updating. 

The GRUB interface is back to the legacy BIOS look, as opposed to the new interface.

And I get that exact error when I choose my Win 7 install.

"Symbol not found grub_divmod64_full"

Kind of a pain in the butt since I need to boot into Windows to access some work programs.

I tried grub-mkconfig, update-grub, the UUID is still the same on my Win7 partition.. :/

---

### Post by der_emu on 2011-04-21
same prob over here...

---

### Post by ArXiLaMaS on 2011-04-21
Same problem here and i can't find any solution anywhere :(

---

### Post by deancasino on 2011-04-21
righto, let's report a bug

---

### Post by deancasino on 2011-04-21
I need everyone that this bug is affecting to marked as "This bug affects you" because my error looks too much like an isolated HDD failure.

[https://bugs.launchpad.net/ubuntu/+bug/768716](https://bugs.launchpad.net/ubuntu/+bug/768716)

---

### Post by Quackers on 2011-04-21
I had a similar error after a grub-pc update last week.
Mine was Grub error: symbol not found: 'grub_env_export` (if I remember correctly).
I purged/re-installed grub and things returned to normal.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by deancasino on 2011-04-21
Cheers bud, I purged and reinstalled and issue resolved!.

---

### Post by Quackers on 2011-04-22
That's good news :-)
It seems one of those grub-pc updates didn't install properly. It may be that something else would have worked too, but if I'm in doubt I usually purge and re-install.

---

### Post by althu on 2011-04-22
I encountered this error yesterday, but after something's (probably grub-pc) updated today the error has gone. So check updates.

---

