---
title: "No TV, only green screen (Mythbuntu)"
date: 2007-10-30
forum: Mythbuntu
---

### Post by harvey186 on 2007-10-30
Hi, I have installed Unbutu 7.01 gutsy and than I have installed Mythbuntu. 
After alot of trouble during the installation, I get MythTV running. But when I try watching TV on with the frontend I only get a green screen (no audio). It's the same with KdeTV.
I'm using a PVR350 (Germany Version with a Philips  Chip).
I have a Matrox Parhelia DL256 graphic card on a Tyan Tiger s2882 Mainboard with 2 Opteron 250.

Can some help me ?

Thanks
Harvey

---

### Post by axelsvag on 2007-10-30
It looks like the problem many have had that they call "pink of death" or as it sometimes look like a lot of green colours. Does it behave the same if you restart the computer and just try to start "watch TV"?

---

### Post by harvey186 on 2007-10-30
Yes, it's always green. After restarts, after reconfigurations, allways.

---

### Post by axelsvag on 2007-10-31
Is it only in the same colour green or do you see many difefrent colours of green. Have you tried to choose another seession with example gnome or xfce instead of mythbuntu session.

---

### Post by dmfrey on 2007-10-31
I believe to resolve this you have to uninstall your nvidia-glx-new and install nvidia-glx.

Others have reported a but with the nvidia driver and XV.  I too have to do this, but have been kind of strapped for time.  Ususally a reboot fixes it for me; even just restarting gdm has worked as well.

BTW, it doesn't appear to affect viewing recordings, etc. with XVMC.

---

