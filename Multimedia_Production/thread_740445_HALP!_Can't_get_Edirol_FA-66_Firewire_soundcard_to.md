---
title: "HALP! Can't get Edirol FA-66 Firewire soundcard to work!"
date: 2008-03-30
forum: Multimedia Production
---

### Post by univac on 2008-03-30
I think I have freebob installed already. I can't get the Edirol FA-66 to work.  I've found various forum threads that touch on this issue, but none specifically help me. 

Will someone who knows what they're doing please help?

Here's some info to get started, from the terminal:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault (core dumped)

---

### Post by Stochastic on 2008-03-30
Looks like you don't have permission to use the Firewire port.  This is normal and to get it changed you need to do ```
sudo gedit /ect/udev/rules.d/40-permissions.rules
```
then find the line that reads:

KERNEL=="raw1394",                               GROUP="disk"

and change it to:

KERNEL=="raw1394",                               GROUP="audio"

hit save, maybe do a reboot (don't know if that's needed), and try again.

---

### Post by jenny_thinkpad_t61p on 2008-06-18
> **univac said:**
> I think I have freebob installed already. I can't get the Edirol FA-66 to work.  I've found various forum threads that touch on this issue, but none specifically help me. 

Will someone who knows what they're doing please help?

Here's some info to get started, from the terminal:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault (core dumped)

******Question: Did this work, is the Edirol FA-66 supported by Ubuntu? how well is it supported?, what programs did you load to support it?

---

### Post by Stochastic on 2008-06-20
The Edirol FA-66 and 101 are both well supported by both the (current) freebob and (future) ffado drivers.  These can be loaded via Jack.  That permissions issue was a problem with the default permissions for raw firewire access in Ubuntu - if you use Ubuntu Studio Hardy or later, that permission is easily changable via the UbuntuStudio controls.

---

