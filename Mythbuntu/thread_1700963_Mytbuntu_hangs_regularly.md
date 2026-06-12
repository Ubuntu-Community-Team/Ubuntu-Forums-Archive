---
title: "Mytbuntu hangs regularly"
date: 2011-03-05
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2011-03-05
mythbuntu 10.10 + backports + avernard repos, Combined Back/Frontend

As in every couple of days - usually overnight, I check it in the morning and it will be completely unresponsive, needing a hard reset.

Hard to tell if the server stuff is frozen. I cannot ssh in from another machine.

Here the real odd thing - it kills the network, the Mythbox is plugged into my neatgear router (DG834G) and its port will be flashing furiously. The other PC, also plugged into the Router is unable to access anything, not even the router itself. If I unplug the mythbox from the router I can access the net again.

But I need to hard reset the mythbox before I can access it.

This started happening since I upgraded from 10.04 to 10.10. I've since purged myth off the box and reinstalled from the avenard repos. I'm using the Nvidia 256 drivers.

I've disabled all the network apps I can think of, BT server (deluge) and my mailserver. Made no difference.

Any ideas where to start hunting next?

Thanks - Lindsay

---

### Post by Lindsay.Mathieson on 2011-03-14
I think I've resolved this one, 4 days uptime now. Two things seem to have fixed - *both* are needed.

[LIST]
[*]Set the NVIDIA Driver version to 256 (nvidia-glx-256)
[*]Set vmalloc=256M in the kernal options
[/LIST]

The last one is interesting - appears to be a regression to this:
  [https://bugs.launchpad.net/ubuntu/+bug/306664](https://bugs.launchpad.net/ubuntu/+bug/306664)

I was getting the nvidia module not loading problem about 30% of the time when booting.

---

