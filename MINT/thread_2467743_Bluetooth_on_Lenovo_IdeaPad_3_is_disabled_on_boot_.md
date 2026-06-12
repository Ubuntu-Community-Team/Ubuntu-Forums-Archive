---
title: "Bluetooth on Lenovo IdeaPad 3 is disabled on boot by default."
date: 2021-10-06
forum: MINT
---

### Post by stchman on 2021-10-06
I recently purchased a new Lenovo IdeaPad 3 with Ryzen 7 5700U, Radeon graphics, NVME, etc.

All works well running Linux Mint 20.2 using the 5.11.0-37 kernel (had  to use it as some devices didn't work properly like screen brightness  control).

When I pair my Bluetooth mouse (it paired no problem), I have to turn on  the Bluetooth using the icon in the system tray.  I have checked the  following.

/etc/bluetooth/main.conf and AutoEnable = true

I them tried:

sudo systemctl is-enabled bluetooth

this command returns enabled


I was able to effect that Bluetooth will be enabled when I log i.  I created a startup with the following:

```

rfkill unblock bluetooth

```

This results in bluetooth being enabled after I log in, can I use the same command in GRUB?


My question is, are there any grub or BIOS settings that can help?

Thanks.

---

### Post by jeremy31 on 2021-10-06
Moved to Mint

---

### Post by stchman on 2021-10-07
I did a little more research and was able to create a service using  systemd.  This allowed the rfkill command to be executed during the boot  process and paired the mouse sooner.

I will mark the thread solved.

---

