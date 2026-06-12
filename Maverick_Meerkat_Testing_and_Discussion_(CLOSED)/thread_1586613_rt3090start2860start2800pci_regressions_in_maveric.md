---
title: "rt3090sta/rt2860sta/rt2800pci regressions in maverick?"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by frenkel on 2010-10-02
I'm currently using Lucid on my Netbook (Compaq CQ10) with the rt3090sta module for wifi. This works really great, never have any problems.
Since Maverick development started I've been trying out Maverick and it always gave me problems with wifi. I cannot connect to any network, it keeps asking for the password. When I unload all modules that involve the ralink card:
rt2x00pci
rt2x00usb
rt2x00lib
rt2800pci
rt2800lib
rt2800usb
rt2860sta

And load the rt2860sta or the rt2800pci module again, my laptop hangs.

Is this due to the fact that I actually need a rt3090sta driver for maverick? Is my network card incorrectly identified?

---

### Post by scokem on 2010-10-02
I have 2 devices that use Ralink chipsets (rt2860 and rt2870) and I noticed the regression too. I've had to go back to manually building the module using the driver files from Ralink's site which I haven't had to do for quite a few releases now :-( Luckily I had my old notes on how to do it and it works at least. Let me know if you need help to do it and I'll post some instructions.

---

### Post by frenkel on 2010-10-02
Did you report the bug in Launchpad? I can't find any...

---

### Post by scokem on 2010-10-02
Only tried it for the first time yesterday evening so no.

---

### Post by frenkel on 2010-10-02
Please add yourself as "affects me to" to this bug:
[https://bugs.launchpad.net/ubuntu/+bug/653593](https://bugs.launchpad.net/ubuntu/+bug/653593)

---

### Post by scokem on 2010-10-02
Done. Have you tried building it yourself to at least see if you can get it working?

---

### Post by frenkel on 2010-10-02
No I haven't, but installing the mainline kernel makes it work instantly, so it's probably something ubuntu specific.

---

### Post by scokem on 2010-10-02
Just an update on this for anyone who's interested. I've been doing some reading into it and it appears that only the 64 bit version is affected. I'm currently on my netbook (it has the rt2870) and am running the netbook edition rc which is 32 bit and it's working flawlessly. It's the best Ubuntu experience I've had with it so far! On my laptop I am running the 64 bit desktop build and that is the one seeing issues. If I get chance, I'll download the 32 bit desktop version and see if that has the same problem on my laptop.

Frenkel - can you confirm which version are you seeing issues with?

---

### Post by frenkel on 2010-10-02
I'm seeing these issues on 32bit... :(

---

