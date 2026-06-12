---
title: "Freeze after RTL8185 Wireless adapter installation."
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by gasto on 2011-05-12
Hello mates,

I have installed the driver for the Realtek RTL8185 Wireless LAN adapter as specified in the "Readme" :

```
<<Method 1>>
Running the scripts can finish all operations of building up modules from source code and start the nic:
    1. Build up the drivers from the source code
        make

    2. Install the driver to the kernel
        make install
        reboot

    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
        ifconfig wlan0 up

        Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name,
        since it may change wlan0 to wlan1,etc.

```
I also executed this commands dictated by the "Readme":
```

iwlist wlan0

iwconfig wlan0 AP ESSID

```

I executed other commands that I don't remember but that was about it. Rebooted.

But to no avail. Now my Ubuntu 9.10 installation is not booting properly(it freezes at the load of the Gnome interface's desktop). What can I do?

---

### Post by gasto on 2011-05-23
Has anybody any idea what steps to follow. First time a driver or configuration modification causes this to the normal Ubuntu boot.

---

### Post by gasto on 2011-05-23
By the way, my wireless internet connection works on the same computer while running the Windows XP SP3 service pack and it's respective driver.

---

