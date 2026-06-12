---
title: "Lucid 3g"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Hippytaff on 2011-02-13
I have been installing ubuntu on the families laptops. I thought it best to stick with the LTS versions for obvious reasons, but for some reason a ZTEC wireless dongle on the 3 network isn't recognised on lucid but is on my maverick. Is there a was to tweak lucid or is it just easier to upgrade my brothers laptop to maverick, which I am reluctant to do as the support (therefore stability and security) runs out a lot quicker.

All opinions and ideas welcome

Cheers

---

### Post by SaintDanBert on 2011-02-13
Each *-buntu release relies on a specific kernel, so Maverick has a newer kernel than does Lucid.

Each kernel, relies on its own suite of modules (aka, "device drivers").
Since your hardware works with Maverick (newer) and not Lucid (older) that likely explains what is going on. 

I suggest that you discover the name of the driver module and it version identifier. Then look to see whether (a)this module exists for Lucid, and (b) which module version is supported. You might investigate the Lucid "backports" repository.  I think these packages are newer parts that have been implemented for 10.04 LTS in spite of the fact that they were developed and released for 10.10 or newer. Based on what you learn, you might be able to load a more recent module with your Lucid kernel or you may need to compile that newer module for your Lucid kernel.

Since all of the Lucid packages presume the LTS kernel, taking steps to deploy the Maverick kernel might pose serious problems.

Bonne chance,
~~~ 0;-Dan

---

### Post by Hippytaff on 2011-02-13
thanks for the rely.

A quick search for the module and 10.04 returned the fact (fact?) that 10.04 should be able to deal with it out of the box. It was at the end of a long day so maybe I was doing something wrong. Failing the possibility that it was me malfunctioning, I'll certainly look into the hardcore suggestions you made (and maybe progress from the n00b I've been for such a long time)

Cheers SaintDanBert

---

### Post by SaintDanBert on 2011-02-14
The only **dumb question** is one that you fail to ask.

The only **dumb mistake** is one that you fail to learn from.

Cheers,
~~~ 0;-Dan

---

### Post by Hippytaff on 2011-02-14
I took the easy way out and upgraded him to 10.10.

Cheers for the support

---

