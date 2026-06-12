---
title: "a quick question, rythem box"
date: 2009-07-24
forum: Multimedia Software
---

### Post by mr_x408 on 2009-07-24
hey everyone,
i have started playing my wine games in a separate xsession to improve the game performance i am useing a script to do this
 eg.
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac -terminate & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Steam/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "/home/game/.wine/dosdevices/c:/Program Files/Steam/Steam.exe"

this is working great so far but i enjoy playing with music in the background i was wondering what i would have to add into this script to start rythem box and steam in the same x session

---

