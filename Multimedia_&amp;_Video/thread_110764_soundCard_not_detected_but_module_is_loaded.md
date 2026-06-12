---
title: "soundCard not detected but module is loaded"
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by gnosio on 2005-12-31
i installed ubuntu on my new system. with onboard soundcard 	
Asus R5D1-VM
[http://www.asus.com/products4.aspx?l1=3&l2=11&l3=179&model=770&modelmenu=1](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=179&model=770&modelmenu=1)

the problem is i cannot get the sound started 
i fixed the ati graphics card with the flgrx.

the problem is the sound card is listed as atiixp in the ALSA doc
and when i try to test using the media selection utility .. it comes up with a no pipeline error.[both the src n sink r disabled ]

the hardware doesn't show up in the device list
but the module atiixp is loaded [shows up in lsmod]

so guys help me out ..
wat is that i am missing out on

rgds,
bob

---

### Post by FarEast on 2006-01-07
Hello gnosio,

> the hardware doesn't show up in the device list
> but the module atiixp is loaded [shows up in lsmod]

It is 'snd-atiixp.ko' that has to be loaded.  So it seems that
the system does not recognize your chipset as a sound device.

I recommend you to check BIOS setting.
Is the item 'on-board sound' (or something like that) enabled?

Regards,
FarEast;)

---

