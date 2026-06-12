---
title: "Enabling Firewire in 8.10"
date: 2009-03-28
forum: Multimedia Software
---

### Post by waltkerr on 2009-03-28
I recently had to re-install Ubuntu 8.10. Everything is running again except my Presonus Firebox interface. It is connected via Firewire and I've installed Jack. However, when I start Jack, it crashes with the message:

[FONT="Arial Black"]
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
LibFreeBoB ERR: cannot create libfreebob handle
[0mcannot load driver module freebob
[/FONT]

I remember there were a couple things I had to do from the command line to bring the 1394 connection alive.

Can anyone help me out?

Thank you very much!

---

