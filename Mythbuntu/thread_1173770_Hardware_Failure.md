---
title: "Hardware Failure?"
date: 2009-05-30
forum: Mythbuntu
---

### Post by nasha on 2009-05-30
Hi Guys,
I've a feeling my tuner card has died, but i want to make sure i explore all possibilities before replacing.
I use a Dvico Dual Digital 4, which was previously working fine. Sometime within the past few days it stopped working after a reboot (no changes made).
I deleted the tuners from within mythtv-setup and reconfigured them fine. However when i attempt to scan in channels it says failed to open the card.

Output seems fine from the kernel...
Any advice would be greatly appreciated!!

Nasha
```

dmesg|grep DVB
nasha@MythTV:~$ dmesg|grep DVB
[    8.785396] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[    8.816654] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[    8.928529] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[    8.958777] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[    8.958793] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[    8.990058] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[    9.036547] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[    9.037288] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.

```

---

### Post by nasha on 2009-05-30
Bump! Anyone have any input please? I've been without Myth for a week now, it's killing me :(

---

### Post by ian dobson on 2009-05-31
Hi,

It looks as if the card is recognised correcly and the correct firmware is loaded. If myth says that it can't open the tuner, it could be a permissions problem, or the device name could have changed.

Do you have a device node in /dev/ for your card (/dev/dvb*) ? what permissions does the device have (ls /dev/dvb* -o -a)?

Regards
Ian Dobson

---

### Post by nasha on 2009-05-31
Thanks for the response Ian. Permissions shouldn't be the issue as nothing was changed, and everything seems ok there, see output below.

```
nasha@MythTV:~$ ls -l /dev/dvb
total 0
drwxr-xr-x 2 root root 120 2009-05-31 19:10 adapter0
drwxr-xr-x 2 root root 120 2009-05-31 19:10 adapter1

```

---

