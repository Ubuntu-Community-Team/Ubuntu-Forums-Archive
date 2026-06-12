---
title: "Fatal error starting wine second X server"
date: 2009-07-19
forum: Multimedia Software
---

### Post by stratman1988 on 2009-07-19
Hey I'm using this script to get wine running on a separate X server:
```
#!/bin/sh
# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/WineBottles/Steam/drive_c/Program Files/Steam/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEPREFIX=~/WineBottles/Steam/ wine "C:/Program Files/Steam/steam.exe"
```
Worked fine on my old 32 bit Hardy machine, but on my new 64 bit machine with 64 bit hardy the script crashes my main desktop as soon as the second server comes up and fails to start any app on the new server. Debug output shows ```
nvidia-settings: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
``` (full debug attached)
I've tinkered with nvidia-settings and researched the error but can't seem to find any solution  :confused: 
Ideas anyone?
My hardware:
Hardy Heron 64 Bit
Intel Core 2 Duo P9700 "Montevina" 2.8GHz
nVidia GeForce GTX 260M
4GB RAM

---

