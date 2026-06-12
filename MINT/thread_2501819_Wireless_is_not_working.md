---
title: "Wireless is not working"
date: 2024-10-21
forum: MINT
---

### Post by oreoiceblended on 2024-10-21
Hello,


I recently tried to install Linux Mint Cinnamon on my PC (B760M GAMING PLUS WIFI DDR4) using a dual boot with Windows 11. The Wi-Fi works normally on Windows, but on Linux, no Wi-Fi connection option appears in the Network Configuration. I attempted to install the rtw89 driver from [https://github.com/lwfinger/rtw89](https://github.com/lwfinger/rtw89), but after rebooting, nothing seems to have changed.


Here is my wireless info script:


[URL="https://termbin.com/xvww"]https://termbin.com/xvww

[/URL]

Any help would be greatly appreciated.


Cheers.

---

### Post by jeremy31 on 2024-10-22
Moved to Mint
try ```
cd rtw89 && sudo make uninstall
```
Then reboot and run the wireless script again

---

### Post by oreoiceblended on 2024-10-23
I've done everything you asked, and here is the script: 

[https://termbin.com/o7vz](https://termbin.com/o7vz)

Thanks for getting back to me.

---

### Post by jeremy31 on 2024-10-23
Results for ```
locate rtw_8851b
```

---

### Post by oreoiceblended on 2024-10-23
Here is the output:
```

/home/danh/rtw89/.rtw_8851b.ko.cmd
/home/danh/rtw89/.rtw_8851b.mod.cmd
/home/danh/rtw89/.rtw_8851b.mod.o.cmd
/home/danh/rtw89/.rtw_8851b.o.cmd
/home/danh/rtw89/.rtw_8851be.ko.cmd
/home/danh/rtw89/.rtw_8851be.mod.cmd
/home/danh/rtw89/.rtw_8851be.mod.o.cmd
/home/danh/rtw89/.rtw_8851be.o.cmd
/home/danh/rtw89/rtw_8851b.ko
/home/danh/rtw89/rtw_8851b.mod
/home/danh/rtw89/rtw_8851b.mod.c
/home/danh/rtw89/rtw_8851b.mod.o
/home/danh/rtw89/rtw_8851b.o
/home/danh/rtw89/rtw_8851be.ko
/home/danh/rtw89/rtw_8851be.mod
/home/danh/rtw89/rtw_8851be.mod.c
/home/danh/rtw89/rtw_8851be.mod.o
/home/danh/rtw89/rtw_8851be.o
/timeshift/snapshots/2024-10-18_11-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/timeshift/snapshots/2024-10-18_11-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/timeshift/snapshots/2024-10-22_10-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/timeshift/snapshots/2024-10-22_10-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/timeshift/snapshots/2024-10-22_10-00-01/localhost/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/timeshift/snapshots/2024-10-22_10-00-01/localhost/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/timeshift/snapshots/2024-10-23_10-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/timeshift/snapshots/2024-10-23_10-00-01/localhost/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/timeshift/snapshots/2024-10-23_10-00-01/localhost/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/timeshift/snapshots/2024-10-23_10-00-01/localhost/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/usr/lib/modules/6.8.0-38-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko
/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851b.ko
/usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_8851be.ko

```

---

### Post by jeremy31 on 2024-10-23
```
sudo rm /usr/lib/modules/6.8.0-47-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw_*.ko
```
Reboot

---

### Post by oreoiceblended on 2024-10-23
I've successfully removed the files and rebooted, but nothing changed. I also ran the 'locate' command again and found that the compressed files are still there.

---

### Post by jeremy31 on 2024-10-23
Do the wireless script again and post results, the compressed ones should be the kernel modules and they should work fine

---

### Post by oreoiceblended on 2024-10-23
Here is the results:

[https://termbin.com/qjz7](https://termbin.com/qjz7)

---

### Post by jeremy31 on 2024-10-23
Do a ```
sudo depmod -a
```
Reboot

---

### Post by oreoiceblended on 2024-10-23
i have ran the command and nothing happened

---

### Post by jeremy31 on 2024-10-23
New script results then

---

### Post by oreoiceblended on 2024-10-23
[https://termbin.com/49af](https://termbin.com/49af)

---

### Post by jeremy31 on 2024-10-24
Power off, unplug power cord, press and hold power button for 30 seconds, reconnect cord and boot

---

### Post by oreoiceblended on 2024-10-24
Bruh, it finally worked! I don&#8217;t know how it worked, but it was so magical. Thank you so much for your help!

---

### Post by jeremy31 on 2024-10-24
It may have been caused by Windows hybrid shutdown as I noticed this is the script dmesg info ```
probe of 0000:03:00.0 failed with error -22
```

---

### Post by oreoiceblended on 2024-10-31
The Wi-Fi still disappears whenever I reboot. Then, I use the trick of 'unplugging and holding the power button' to make it work again. Is there a solution for this?

---

### Post by jeremy31 on 2024-10-31
Disable the hybrid shutdown in Windows

---

