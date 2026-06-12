---
title: "Disable internal wireless &amp; enable external?"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2010-12-25
Disable internal wireless card & enable external? Can I do this really by network-manager or should I use some other program. If I plug-in external both are connected. If I disable internal by laptop button, I cannot enable wireless anymore in nm-applett (external on).

---

### Post by spiky001 on 2010-12-25
Hi the wireless mst be named something like wlan0 wlan1? can you type in ```
sudo ifconfig wlan0 down
``` or what ever wireless you want down

---

### Post by grahammechanical on 2010-12-25
My motherboard has a BIOS function that lets me disable the built in wireless adapter. It is under USB Configuration. Your motherboard might have the same feature.

Regards.

---

### Post by cd-r80 on 2010-12-25
ifconfig wlan0 down

Network Manager Drives it almost immediately up again.

---

### Post by cd-r80 on 2010-12-25
I also have very poor featured PhoenixBios on my Acer 5520. No options to turn on/ off.

---

### Post by cd-r80 on 2010-12-26
Seems to be easiest to remove Network-Manager.

---

### Post by grahammechanical on 2010-12-26
Assuming that your internal wireless card is called wlan0, then is the wlan0 connection set to automatically connect? If the external wireless card is wlan1 and it is set to automatically connect, then things should work as you want (may be).

regards.

---

### Post by cd-r80 on 2010-12-26
Hmm. Ok if I disable "connect automatically" & then ifconfig wlan0 down. I can then connect & test external wireless interface to same AP. It would just be more nice to have up / down, on / off / interface option in network manager. Perhaps there is no that kind of wireless manager in Linux? Or if different APs I can use that lock by MAC?

---

