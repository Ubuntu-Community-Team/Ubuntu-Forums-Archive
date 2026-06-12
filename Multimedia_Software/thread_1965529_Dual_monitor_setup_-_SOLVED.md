---
title: "Dual monitor setup - SOLVED"
date: 2012-04-25
forum: Multimedia Software
---

### Post by scottbomb on 2012-04-25
First, some background. Comp is 3-core Athlon with an ATI Radeon HD4350 card. I use a 24" monitor at 1920x1080 and a 19" at 1280x1024. I was using the ATI proprietary driver that's recommended on install. I spent a week trying to get this to work as well as it does in Windows. Googling, experimenting, using grandr, and arandr. No matter what I did, I couldn't get the 19" into 1280x1024 mode. My virtual desktop resolution was the culprit. It was just way too small to support both monitors in the modes I wanted. Persistence across sessions was also troublesome.

Solution: Just to see what would change, I uninstalled the ATI drivers. The naive open-source driver built into Xubuntu (I don't know what it's called) allows me to have my virtual desktop set with MUCH higher resolutions. I then used arandr and saved the config to a file. All the file does is make some calls to xrandr. So I copied them into a bash script that runs at the beginning of the session. Keep in mind, you may need to replace "VGA-0" and "DVI-0" with whatever name xrandr has for your monitors. Just run xrandr to see them.

Edit: This script works better than the one I had up here before. They're both very similar, but the new version works better and is more reliable across sessions.

#!/bin/bash

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
sleep 1
xrandr --addmode VGA-0 1280x1024_60.00
sleep 1
xrandr --output VGA-0 --mode 1280x1024_60.00 --pos 1920x312 --rotate normal --output DVI-0 --mode 1920x1080

Save it, then make it executable with: sudo chmod +x <your file name>.
Then, going to Menu -> Settings -> Settings Manager -> Session and Startup. Create a new task in the Appliacation Autostart tab. Inthe command field, just give the loction of your file ... mine is called monitors.sh and is saved in /etc so the command is: /etc/monitors.sh.

And in case you were wondering, compositing works just fine without the prop driver and everything else looks fine, incl open arena.

---

