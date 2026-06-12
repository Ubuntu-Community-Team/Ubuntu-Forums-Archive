---
title: "Belkin N1 and Ubuntu 64 not working."
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-10-18
I had a quick search to solve this whichc turned up verry little, only that Belkin provide ONE driver for both 32 and 64 versions.

It's a PCI Belkin N1 (F5D8001v2)

I've set it up on ndiswrapper about 5 times on 32 bit machines and it usually works with very little hassle.

Now when I install the driver through ndiswrapper it says
"Unable to locate NetMW146x.sys make sure all driver files are present including inf and sys files"

There has never been a "16" in all of this... just 14,15 and "x"
Is there ANY possible way of getting this card working in Ubuntu64 atleast until I pop for a cheap wireless card known to support ubuntu?

Thankyou for the help, if it's down much longer my girlfriend may kill me so this is atleast a little urgent.

---

### Post by ironic.demise on 2010-10-18
ah ok, now I tried renaming the netmw145 to netmw146 and it seems to have worked, ndiswrapper -l shows the driver and that the device is present, but after a modprobe, nothing happens and I still cant do wireless.

---

### Post by ironic.demise on 2010-10-19
I'm using 32 for the time being, anybody else have this problem?

---

### Post by wojox on 2010-10-19
> **ironic.demise said:**
> I'm using 32 for the time being, anybody else have this problem?

Your not alone. I ended up installing 32 bit on my sister's AMD 64 just to connect to her Belkin router. :(

---

### Post by ironic.demise on 2010-10-21
> **wojox said:**
> Your not alone. I ended up installing 32 bit on my sister's AMD 64 just to connect to her Belkin router. :(

I think that the only way you can really (sort of) rely on 64-bit is with know linux support...
as in no ndiswrapper...

Ever tried passy's?

---

