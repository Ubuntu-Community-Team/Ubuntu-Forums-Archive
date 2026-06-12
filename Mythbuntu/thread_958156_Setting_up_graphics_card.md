---
title: "Setting up graphics card"
date: 2008-10-25
forum: Mythbuntu
---

### Post by 404wanderer on 2008-10-25
Hello all,

sorry if this has already been asked. I've searched but not found any answers.

I've just been through a long and torturous process of getting Mythbuntu installed on my Intel DG45ID motherboard.

How do I set the on-board graphics card up? The board uses an Intel X4500HD, which is apparently supported by linux. I can only get 800x600 output. xserver-xorg-video-intel is installed and is the latest version. What driver should I select under the xorg config tool? Do I need to add additional packages?

Any help appreciated as I'm pretty lost at the moment.

Thanks,
wanderer.

---

### Post by newlinux on 2008-10-25
try selecting the "intel" driver.

---

### Post by 404wanderer on 2008-10-26
I've tried selecting both intel drivers but they both return a message saying they've failed when I apply them.

wanderer

---

### Post by 404wanderer on 2008-10-27
Ok, I'm really stuck now (and so far this mythbuntu build has taken three weeks:( )

I've just done the following -
downloaded xf86-video-intel-2.5.0, downloaded mesa-drm, built and configured both. Went through the full build and install. When I go to the mythbuntu control centre, launch the Xorg config, select graphics card, it gives me two options for graphics cards - Graphics Card (VESA driver (generic)). Selecting the i810 or intel options, then test both come back with "Configuration test failed"

Please can anyone assist as I'm now completely stumped.

Thanks,
wanderer.

---

### Post by suncoolsu on 2008-11-06
how do u install xf86-video-intel - Can you please help - i am unable to do so - Also are you installing the MESA drm as well? 

Thx
B

---

### Post by orduek on 2008-11-12
any solution?

---

### Post by mark467 on 2009-02-25
has anyone solved this?
I was about to do a system with this board

---

