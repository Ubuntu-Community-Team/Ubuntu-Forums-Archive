---
title: "Camcorder or Kino movie maker doesn't work"
date: 2009-03-23
forum: Multimedia Software
---

### Post by Vincenso Andolini on 2009-03-23
Hi all,

I've been trying to import some video footage into Kino video editor, but I cannot get the application to light up the "capture" button, it remains "greyed-out".

I am quoted an error "WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!"

Does anybody know what this means? I assume there's an error with my firewire connection. Does this sound right?

By the way, my camcorder model is Canon ZR850.

All help is appreciated.

Vincenso

---

### Post by suda on 2009-03-23
Kino will only work with firewire. If you have firewire and are uploading through the firewire port, then I suspect something's up with Kino. Have you tried to remove and reinstall Kino with Synaptic? Have you used this camera successfully before with another OS, using firewire, or another version of Ubuntu? Have you gone to the Kino Web site to see what recommendations they have?

---

### Post by Vincenso Andolini on 2009-03-24
I've figured out my problem. It was a firewire recognition error. Kino didn't recognize the firewire. I had to go to terminal and enable it, but before that I had to install packages from Synaptic.

Only thing now is that I seem to have to do this every time I use Kino.

Vincenso

---

