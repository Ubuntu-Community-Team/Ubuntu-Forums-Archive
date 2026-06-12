---
title: "Handy startup script for HTPC/Web PC"
date: 2010-06-12
forum: Multimedia Software
---

### Post by bakegoodz on 2010-06-12
I use my Livingroom computer for both browsing the web and as HTPC.
When I watch a movie I want grab the remote, and I don't want to mess with the keyboard/touchpad.
This is a simple GUI script that starts XBMC, but gives you time to cancel it if you don't want to run it.
It uses the GUI script program Zenity. If you don't already have it, you can just do: sudo apt-get install zenity 
You can add a startup item in the startup preferences.  I use Lubuntu, so I had to do it another way. I added the script to the bottom line of /etc/xdg/lxsession/Lubuntu/autostart

#!/bin/bash
# DO Whatever YOU WANT TO PUBLIC LICENSE
#  Version Whatever, June 2010
#
# Everyone is permitted to copy and distribute verbatim or modified
# copies of this license document.
# 
#           DO Whatever YOU WANT TO PUBLIC LICENSE
#  TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION
# 
#  0. You just DO whatever YOU WANT TO.

 
# Second to count down
seconds=15
 
#While-loop to show progress of time passed.
 
elapsedtime=1
(
while [ $elapsedtime -lt $seconds ]
do
    sleep 1s
    echo "$(echo "scale=4; ($elapsedtime/$seconds)*100" | bc)"
    elapsedtime=$(($elapsedtime+1))
done
) | zenity --progress --auto-kill --auto-close --title="XBMC" --text="Will start. Press cancel to abort."
 
xbmc # You could substitute this for any program
  
exit

---

