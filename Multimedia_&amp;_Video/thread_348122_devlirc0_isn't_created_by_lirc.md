---
title: "/dev/lirc0 isn't created by lirc"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by deviantintegral on 2007-01-28
Hi,

I just switched my kernel from -386 to -generic. I've rebuilt the ivtv and the lirc modules, but for some reason the lirc module doesn't seem to be properly picking up the IR reciever. I have a PVR 350. Here are the lines from dmesg before the upgrade:

```
Jan 21 17:23:48 uberphoenix kernel: [17179594.104000] lirc_dev: IR Remote Control driver registered, at major 61
Jan 21 17:23:48 uberphoenix kernel: [17179594.116000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
Jan 21 17:23:48 uberphoenix kernel: [17179594.420000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
Jan 21 17:23:48 uberphoenix kernel: [17179594.424000] lirc_dev: lirc_register_plugin: sample_rate: 10
Jan 21 17:23:49 uberphoenix lircd-0.8.0[3975]: lircd(userspace) ready
```

And now just...

```
[17179589.524000] lirc_dev: IR Remote Control driver registered, at major 61
[17179589.524000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
```

So it seems like lirc is simply not discovering the IR chip, but I'm not sure how to debug or solve this. So any suggestions would be appreciated :)

Thanks,
--Andrew

---

### Post by superm1 on 2007-01-29
> **deviantintegral said:**
> Hi,

I just switched my kernel from -386 to -generic. I've rebuilt the ivtv and the lirc modules, but for some reason the lirc module doesn't seem to be properly picking up the IR reciever. I have a PVR 350. Here are the lines from dmesg before the upgrade:

```
Jan 21 17:23:48 uberphoenix kernel: [17179594.104000] lirc_dev: IR Remote Control driver registered, at major 61
Jan 21 17:23:48 uberphoenix kernel: [17179594.116000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
Jan 21 17:23:48 uberphoenix kernel: [17179594.420000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
Jan 21 17:23:48 uberphoenix kernel: [17179594.424000] lirc_dev: lirc_register_plugin: sample_rate: 10
Jan 21 17:23:49 uberphoenix lircd-0.8.0[3975]: lircd(userspace) ready
```And now just...

```
[17179589.524000] lirc_dev: IR Remote Control driver registered, at major 61
[17179589.524000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
```So it seems like lirc is simply not discovering the IR chip, but I'm not sure how to debug or solve this. So any suggestions would be appreciated :)

Thanks,
--Andrew
Try to power off the machine and leaving it off ~30s and back on.  A cold boot sometimes resolves these issues.

---

### Post by deviantintegral on 2007-01-29
Well, I found the issue, and it was decidedly low-tech. The PVR card's PCI bracket was too tall, preventing the last few pins from contacting. By removing the bracket, everything showed up again.

Thanks for your help,
--Andrew

---

### Post by Roebi on 2007-02-02
Hi Andrew,

I am also facing issues with lirc and the appropriate device not getting created. I have been looking like h*ll for a solution.
So your post intrigued me quite a bit.
Could you perhaps tape a picture of what you have done/removed?
Or explain more explicitly how the PCI bracket was too tall for you?


Thanks
Roebi

---

### Post by deviantintegral on 2007-02-04
I ended up using a metal file to file down the end of the mounting bracket by about a quarter of a centimetre. The card is currently in my server, but here's a picture of another card. You'll see two screws right near the right-hand side of the card. By removing those, the metal bracket can come off and be modified as needed.

What kind of card are you using? After measuring a few things it looks like the card is actually built properly, it's just the case I'm using isn't. So I doubt that the card your using is actually non-standard in size.

--Andrew

---

### Post by Roebi on 2007-02-05
Hi Andrew.

Thanks for the reply.
I have a Hauppauge WinTV-PVR-150 (non-MCE), built in a Antec NSK2400 case.
Actually, my system is built from an older, second-hand PC. Before I put everything in the Antec case, I had the system up and running, and the remote was working.
Therefore, I thought it could be either driver or hardware related.

I will check tonight if my card is not reallly fitting in the slot.

Roebi.

---

