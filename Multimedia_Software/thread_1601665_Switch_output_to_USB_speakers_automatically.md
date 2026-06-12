---
title: "Switch output to USB speakers automatically"
date: 2010-10-20
forum: Multimedia Software
---

### Post by edm1 on 2010-10-20
In 10.04 when i plugged my HiFi into a USB port audio would automatically switch to play out of it.

Now in 10.10 i need to plug my hifi in then go to 'sound preferences'>'output' and select USB codec as my output AND unmute the device.

Does anyone know of a way to revert to 10.04 behaviour? Thanks.

---

### Post by robdcraw on 2010-10-20
Possibly related, when I plug in my USB headset the sound switches but
I can't control the volume with either the volume control on the
headset or the volume control on the laptop.  If I go under the volume
control applet on the taskbar I have to switch the hardware used under
the "Output" tab.

Laptop: Dell Latitude e6410
Headset: Logitech Clear Chat Comfort USB headset

---

### Post by edm1 on 2010-11-03
This is starting to get frustrating. The most annoying thing is that the whole rigmarole needs repeating whenever I come out of standby.

---

### Post by boris.abramov on 2010-11-24
> **edm1 said:**
> In 10.04 when i plugged my HiFi into a USB port audio would automatically switch to play out of it.

Now in 10.10 i need to plug my hifi in then go to 'sound preferences'>'output' and select USB codec as my output AND unmute the device.

Does anyone know of a way to revert to 10.04 behaviour? Thanks.

I had such problem on all Ubuntu versions.

After a month of periodically googling I found no simple and fully suitable solution.

Probably, I invented a second wheel but I haven't found first one myself. Please, download it here: [http://files.suntrail.org/soundswitch/](http://files.suntrail.org/soundswitch/)


soundswitch - installs a shell script for sound device choosing, useful for doing it from command line

soundswitch-gnome - gnome applet for the previous package, depends on it

You may also run the script when session starts.

At least this works for me.

---

