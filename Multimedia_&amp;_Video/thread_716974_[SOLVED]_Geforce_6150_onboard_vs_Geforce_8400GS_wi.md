---
title: "[SOLVED] Geforce 6150 onboard vs Geforce 8400GS with Flat screen TV problem"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by darkworld on 2008-03-06
My 32" HD TV Sanyo CES32WSD7-B works flawlessly with my onboard geforce 6150 graphics (AMD 64bit Motherboard running Gusty and restricted drivers.) Ive now installed Geforce 8400GS PCI express board which is up and running on LCD Samsung but I hit a problem when I connect my PC to the Sanyo TV. 

Screen stays Blue and reports no signal. Ubuntu is running because I hear the drum roll when it reach login, minus video signal.

Im toying with changing Admin>screen and graphics to plug and play screen before booting down and connecting up to my Flat screen tv. A bit worried about screwing my 32" hd tv! 

Does anybody know what the issue is here or a way forward? Both graphics are nvidia chip sets but obviously different drivers. However it feels to me the PC is not getting info from TV flat screen to PC via 8400GS.

Any ideas? 

If this is the wrong forum for answer perhaps mod's could move it, thanks.

---

### Post by sanddgroper on 2008-03-06
Hi
Only a guess but did you install the drivers for the new card.
If you are using the driver for the onboard card that may not
be helping.
You do have the onboard card disabled.

Cheers
Sandy

---

### Post by darkworld on 2008-03-07
> **sanddgroper said:**
> Hi
Only a guess but did you install the drivers for the new card.
If you are using the driver for the onboard card that may not
be helping.
You do have the onboard card disabled.

Cheers
Sandy

Downloaded and installed nvidia driver from nvidia,

sudo apt-get purge nvidia-glx-new, to remove restricted driver that was being used for onboard.

Loaded driver for card and set up xconfig etc.

I have not looked for a hardware disable on board but in BIOS I changed from onboard graphics to PCIexpress graphics card.

---

### Post by darkworld on 2008-03-08
well my problem is resolved. It now works. I dont know exactly what sorted it.

Removed beta driver and ran latest stable driver. I also added nvtv out to my pc. I also made changes in /etc/initramfs-tools/modules and /etc/modprobe.d/blacklist-framebuffer.

Somewhere in there it started working.

---

