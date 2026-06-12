---
title: "No boot device found - Cr-48"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zachtib on 2011-04-02
I have a Cr-48 running Natty through Luigi (a custom BIOS) that had no trouble running Maverick.

When I first installed Natty Beta the other day, I got a No boot disk found error, which I bypassed by booting into a GRUB console via USB and got into Ubuntu, but even after the latest grub update (and a subsequent grub-install) it's still doing it.

Does anyone have a suggestion?

---

### Post by zachtib on 2011-04-04
*bump*

---

### Post by kerry_s on 2011-04-04
i think you have to add a delay to give the sdcard time to mount. try googling ubuntu slow sdcard mount.

---

### Post by zachtib on 2011-04-04
> **kerry_s said:**
> i think you have to add a delay to give the sdcard time to mount. try googling ubuntu slow sdcard mount.

No, it's installed on the internal solid state drive. Was running Maverick just fine...

---

### Post by zachtib on 2011-04-05
Fixed it by installing grub-pc instead of grub-efi

---

