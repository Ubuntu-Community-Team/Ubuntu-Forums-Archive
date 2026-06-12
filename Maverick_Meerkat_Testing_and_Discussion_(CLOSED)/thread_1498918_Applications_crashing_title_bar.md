---
title: "Applications crashing title bar"
date: 2010-06-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by davideotape on 2010-06-01
Just wondering whether anyone is experiencing [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/587192"). I've had it for about a week now, and I'm quite baffled because firefox hasn't been updated since lucid (even though the bug isn't just with firefox). Finally does anyone know what common component of firefox, thunderbird and openoffice could be causing this?

Cheers,
David

---

### Post by ranch hand on 2010-06-01
Not really that particular problem but similar.

I would really try changing your desktop effects to "normal" and see what happens.

---

### Post by davideotape on 2010-06-01
> **ranch hand said:**
> Not really that particular problem but similar.

I would really try changing your desktop effects to "normal" and see what happens.

I haven't got desktop effects on, because I'm using the free nvidia driver

---

### Post by ranch hand on 2010-06-01
I use the open ATI driver and have no trouble with effects even if set on "extra".  I prefer the buggers on none but firefox flickers rapidly and is unusable set there.

I would give it a try if it will handle it at all.  If not you may want to try the xorg.edgers ppa.  They give you open drivers that are a little more advanced.

---

### Post by SevenMachines on 2010-06-01
Is this perhaps the gtk rgba update bug? theres a thread in here somewhere about downgrading gtk. i believe these applications need an update to stop crashing the window manager

---

### Post by davideotape on 2010-06-01
Nope, looks like you need the proprietary driver for desktop effects to run on nvidia cards. But I haven't got desktop effects enabled, so I don't see why that should affect my bug?

---

### Post by davideotape on 2010-06-01
[Here we go.]("http://ubuntuforums.org/showthread.php?t=1490105&highlight=gtk") Feel free to merge

---

### Post by null_pointer_us on 2010-06-01
Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/584287](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/584287)

Temporary Fix:
[https://edge.launchpad.net/~fta/+archive/sandbox/+packages](https://edge.launchpad.net/~fta/+archive/sandbox/+packages)
(grab metacity and metacity-common .debs from that page)

It seems my system upgraded past those fta .debs, so I'm back on the main repository metacity and metacity-common; the problem no longer occurs with Firefox on my system.

---

### Post by rubenverweij on 2010-06-02
They have released that patch too, now, so I hope it's going to work again.

---

### Post by ronacc on 2010-06-02
I was seeing that with metacity but not with compiz and also not just FF OO and TB , for me a nautilus window would do it , seems to be cured now though .

---

