---
title: "Wifi problem with Broadcom card"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Sakarakas on 2010-05-28
Hi guys,

i recently moved from XP to UNR 10.04 on my Lenovo s10e. Spent hours and hours to setup my wireless and still nothing. My adapter is the all time classic Broadcom BCM4312 (14e4:4315). Tried the Broadcom STA in Hardware drivers, tried a million commands in terminal, tried Ndiswrapper. The only thing i manage to get is the Network Manager to show WIFI enabled. But no blue light on the front of the netbook, no wifi detected and of course no connection. There is always the possibility i do something wrong in the wireless settings, however wifi should be detected at least. Please help...i feel desperate :confused:, but don't want to get back to XP. My lenovo was shipped with Suse Enterprise Desktop 10 on disc. Never tried it though....you think it could work???

---

### Post by dorothykinder on 2010-05-28
You might have tries with the higher version of the Broadcom card, that might solve the problem.

---

### Post by ublintu on 2010-05-28
Hi,
Did you try cable internet and than system - administration - hardware drivers  like in here:
[http://ubuntuforums.org/showthread.php?t=1494893&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1494893&highlight=broadcom)
or install ubuntu like in here:
[http://ubuntuforums.org/showthread.php?t=1474008&highlight=bcmwl](http://ubuntuforums.org/showthread.php?t=1474008&highlight=bcmwl)

---

### Post by derekslife on 2010-05-28
I had a similar issue with my s10e. Here's what I did to resolve it.

1) Hook the netbook up to a ethernet connection. You'll need access to the internet

2) Run the update manager (System->Update Manager) and bring your system up to date. Reboot if needed

3) (Optional Step - Information Only). After a fresh reboot, open up a terminal (Accessories -> Terminal). Enter this command:
```
dmesg | grep b43
```You should notice some error messages:
```

[   11.108380] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   11.112248] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   11.118107] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   11.118301] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   11.118491] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```I suppose due to license restrictions, the firmware can't be included as part of the distro.

4) Run the following command in the terminal. This will grab the firmware from your device as part of the installation
```
sudo apt-get install b43-fwcutter
```5) Reboot, and you should be good to go.

---

### Post by derekslife on 2010-05-28
Also, make sure that your wireless card is enabled. There is a green wireless button right above the F10 key. It toggles your wireless.

---

