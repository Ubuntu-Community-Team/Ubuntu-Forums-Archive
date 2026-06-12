---
title: "OSD Sound Widget... that works."
date: 2022-02-04
forum: Multimedia Software
---

### Post by linux-sysop on 2022-02-04
I just installed a fresh Xubuntu 20 on my current system and I was going over the usual tweakage.  I went to put Pnmixer on it and it failed.  I really didn't want to waste hours attempting to configure Pnmixer to work with both Pulse Audio and ALSA. 

I whipped out my [Bash Bible]("http://tldp.org/LDP/abs/html/abs-guide.html") and got to work on the following script.  I custom wrote this to work for my system, but you can probably make it better.  It requires you to "sudo apt install yad" which is the meat of this script.


```
#!/bin/bash
# I named the script vol_OSD without the .sh extension and set it as executable.
# I got a bit lax on this code, using your shortcut keys, I set this to Volume key up - vol_OSD R, Volume key down - vol_OSD L, and Volume key mute - vol_OSD M.  They are all uppercase and the only variable to pass.
# I set the master volume with ALSA, I never cared much for Pulse Audio, it is most likely the cause of more audio errors than the cure. o.O  However you can use PA volume setting if ALSA don't work.

if [ $1 = "M" ]
then
    amixer set Master toggle    
fi
if [ $1 = "L" ]
then
    amixer set Master 1%-    
fi
if [ $1 = "R" ]
then
    amixer set Master 1%+    
fi


# Kill all yad programs running.
pkill yad
# Snag the 2 digit volume percentage from the master channel.
volume=$(amixer get Master | grep % | cut -f 2 -d [ | cut -f 1 -d %)
# Set the volume icon (vion) based on the percentage.
if [ "$volume" == "0" ] 
then 
vion=$HOME"/.icons/v00.png"
fi
if [ "$volume" -gt "1" ] 
then
vion=$HOME"/.icons/v01.png"
fi
if [ "$volume" -gt "5" ] 
then
vion=$HOME"/.icons/v02.png"
fi
if [ "$volume" -gt "10" ] 
then
vion=$HOME"/.icons/v03.png"
fi
if [ "$volume" -gt "15" ] 
then
vion=$HOME"/.icons/v04.png"
fi
if [ "$volume" -gt "20" ] 
then
vion=$HOME"/.icons/v05.png"
fi
if [ "$volume" -gt "25" ] 
then
vion=$HOME"/.icons/v06.png"
fi
if [ "$volume" -gt "30" ] 
then
vion=$HOME"/.icons/v07.png"
fi
if [ "$volume" -gt "35" ] 
then
vion=$HOME"/.icons/v08.png"
fi
if [ "$volume" -gt "40" ] 
then
vion=$HOME"/.icons/v09.png"
fi
if [ "$volume" -gt "45" ] 
then
vion=$HOME"/.icons/v10.png"
fi
if [ "$volume" -gt "50" ] 
then
vion=$HOME"/.icons/v11.png"
fi
if [ "$volume" -gt "55" ] 
then
vion=$HOME"/.icons/v12.png"
fi
if [ "$volume" -gt "60" ] 
then
vion=$HOME"/.icons/v13.png"
fi
if [ "$volume" -gt "65" ] 
then
vion=$HOME"/.icons/v14.png"
fi
if [ "$volume" -gt "70" ] 
then
vion=$HOME"/.icons/v15.png"
fi
if [ "$volume" -gt "75" ] 
then
vion=$HOME"/.icons/v16.png"
fi
if [ "$volume" -gt "80" ] 
then
vion=$HOME"/.icons/v17.png"
fi
if [ "$volume" -gt "85" ] 
then
vion=$HOME"/.icons/v18.png"
fi
if [ "$volume" -gt "90" ] 
then
vion=$HOME"/.icons/v19.png"
fi
if [ "$volume" -gt "95" ] 
then
vion=$HOME"/.icons/v20.png"
fi
# Check for muted and display the final solution using Yad.
muted=$(amixer get Master | grep % | cut -f 4 -d [ | cut -f 1 -d ])
if [ $muted == "on" ] 
then
    yad --posx=25 --posy=25 --image=$vion --text='<span color=\"red\" font="12">'$volume'</span>' --timeout=2 --no-buttons --undecorated --skip-taskbar 
else
    yad --posx=25 --posy=25 --image=$HOME"/.icons/vm.png" --text='<span color=\"red\" font="12">Muted</span>' --timeout=2 --no-buttons --undecorated --skip-taskbar 
fi
```


 It requires you make up 21 icons or you can use mine here.  If you think they are too big just scale them as you see fit.

[https://ibb.co/p1tTmjs](https://ibb.co/p1tTmjs)
[https://ibb.co/MgRnz7g](https://ibb.co/MgRnz7g)
[https://ibb.co/4dWgCDt](https://ibb.co/4dWgCDt)
[https://ibb.co/Bn1YyCc](https://ibb.co/Bn1YyCc)
[https://ibb.co/9GNv4pJ](https://ibb.co/9GNv4pJ)
[https://ibb.co/ZGwSCC0](https://ibb.co/ZGwSCC0)
[https://ibb.co/3d7T3WG](https://ibb.co/3d7T3WG)
[https://ibb.co/qMPVxJf](https://ibb.co/qMPVxJf)
[https://ibb.co/GxNqj0b](https://ibb.co/GxNqj0b)
[https://ibb.co/NNfTXt1](https://ibb.co/NNfTXt1)
[https://ibb.co/xgnvrtD](https://ibb.co/xgnvrtD)
[https://ibb.co/gzH965d](https://ibb.co/gzH965d)
[https://ibb.co/9NWwN2T](https://ibb.co/9NWwN2T)
[https://ibb.co/59bLKGF](https://ibb.co/59bLKGF)
[https://ibb.co/wr2ZYpN](https://ibb.co/wr2ZYpN)
[https://ibb.co/DG423LY](https://ibb.co/DG423LY)
[https://ibb.co/JtBGzrN](https://ibb.co/JtBGzrN)
[https://ibb.co/1sdByNj](https://ibb.co/1sdByNj)
[https://ibb.co/s6gnGnH](https://ibb.co/s6gnGnH)
[https://ibb.co/N2Tkr3v](https://ibb.co/N2Tkr3v)
[https://ibb.co/HHT1dNj](https://ibb.co/HHT1dNj)
[https://ibb.co/hFSC0zH](https://ibb.co/hFSC0zH)

I hope everyone will enjoy the next LTS release coming in April. See you there!

---

