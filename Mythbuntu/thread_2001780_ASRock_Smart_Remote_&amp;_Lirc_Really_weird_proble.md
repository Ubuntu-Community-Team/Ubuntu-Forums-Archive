---
title: "ASRock Smart Remote &amp; Lirc: Really weird problem... any ideas?"
date: 2012-06-11
forum: Mythbuntu
---

### Post by mastixmc on 2012-06-11
Hi guys,

I alway thought that the batteries of my new ASRock Smart Remote were crap... ehhrm... I mean empty and therefore replaced them with new ones... but then I realized that I have a different problem... and that's really weird and I hope that someone could tell what's going on here... 

OS: Ubuntu 12.04 (minimal)
Remote: AS Rock Smart Remote (CIR)
IR-Tool: Lirc

I can switch on my HTPC from about 4-5 meters with the remote and without any problems. That's cool. But as soon as my machine is up and running, I have to go very very close to receiver to send signals (about 20-30cm).

I'm running a tool called irw to see the keys being sent from the remote... and it only receives keys when I'm 20-30 cm away from the receiver... as soon as I leave that range, no signals are being received anymore. That's really weird... if I switched off the HTPC, it would be possible to power it on again from 4-5 meters away... 

Do you have any idea what might be wrong here? It's not the power button itself, because when the machine is running, it also works only from within a range of 20-30 cm. I've exchanged the batteries 2 times already, just to make sure they are not the problem.

Any ideas?! This is really driving me nuts... :?

Update: If I stop the lirc service and run the following command, I can see that the signals arrive from a much wider range!

sudo mode2 -d /dev/lirc0

So what does that mean? What setting in my lircd.conf is wrong?!

Ok... so when LIRC service is not running I can control my HTPC from 3-4 meters. But then only some basic keys work (up, down,...) due to the inactive LIRC mappings. So it's definitely LIRC.

But how can I fix it? Any ideas?

Greetz,

Sascha

---

### Post by alien878 on 2012-06-11
Actually, I've found the kernel IR support is much better than lirc.  Keypress recognition is much better since I changed.  It requires you to remap the keys, but if you can do this in the mythtv frontend keymappings, it is probably the easiest.

See my post here on my experiences and what needs to be done:

[http://ubuntuforums.org/showthread.php?t=1975559](http://ubuntuforums.org/showthread.php?t=1975559)

---

### Post by mastixmc on 2012-06-12
Hi,

thanks for that hint. You're right... if LIRC doesn't work then using the kernel-ir support will be the last solution. LIRC helps some much... but if that doesn't work, then I'd have to go with the native solution.

mastix

---

