---
title: "Upgrade 12.04 to 14.04.1 TBS tuners drivers fail."
date: 2014-08-18
forum: Mythbuntu
---

### Post by drifting on 2014-08-18
So far upgrade went well, seems much slower, but nothing else it seemed was wrong.
Tuners as expected were not there, as with any kernel change the usual, distclean, make, make install. Even went so far as to download the latest driver from TBS.
Quick dmesg | grep frontend

[   23.055715] saa716x_core: Unknown symbol dvb_unregister_frontend (err -22)
[   23.055723] saa716x_core: disagrees about version of symbol dvb_register_frontend
[   23.055725] saa716x_core: Unknown symbol dvb_register_frontend (err -22)
[   23.055733] saa716x_core: disagrees about version of symbol dvb_unregister_ad

[   23.051988] saa716x_core: disagrees about version of symbol dvb_frontend_detach
[   23.051990] saa716x_core: Unknown symbol dvb_frontend_detach (err -22)
[   23.052004] saa716x_core: disagrees about version of symbol dvb_unregister_frontend
[   23.052006] saa716x_core: Unknown symbol dvb_unregister_frontend (err -22)
[   23.052014] saa716x_core: disagrees about version of symbol dvb_register_frontend
[   23.052016] saa716x_core: Unknown symbol dvb_register_frontend (err -22)
[   23.055697] saa716x_core: disagrees about version of symbol dvb_frontend_detach
[   23.055699] saa716x_core: Unknown symbol dvb_frontend_detach (err -22)
[   23.055713] saa716x_core: disagrees about version of symbol dvb_unregister_frontend
[   23.055715] saa716x_core: Unknown symbol dvb_unregister_frontend (err -22)
[   23.055723] saa716x_core: disagrees about version of symbol dvb_register_frontend


ARGH !

Recompiled the drivers for the earlier version, reboot, try again, same thing?

Luckily I clonezilla was my friend, and restored the backup I made before upgrading. Anyone any idea what the problem is? This is rather beyond me. Seems the driver has not loaded at all, as there are no tuners in the DVB directory.

Regards
Paul.
[   23.055725] saa716x_core: Unknown symbol dvb_register_frontend (err -22)

---

### Post by Gillingham on 2014-08-18
Hi I can't remember what the error message I encountered, but I found that I need to add an extra step to the process of recompiling on the upgrade to 14.04

So to reinstall the drivers I now need to do:
```

sudo rm -R /lib/modules/3.13.0-24-generic/kernel/drivers/media/
cd tbs-linux-drivers_v140323/linux-tbs-drivers/
make distclean
./v4l/tbs-x86_64.sh
make -j5
sudo make install

```

where 3.13.0-24-generic is the current kernel.

I have TBS 6220 card.

David

---

### Post by drifting on 2014-08-20
Brilliant!
Thanks that did the trick. Note duly made for later use.

Paul.

---

