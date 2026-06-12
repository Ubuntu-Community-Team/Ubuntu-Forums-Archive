---
title: "ATI Drivers far from working"
date: 2009-06-24
forum: Multimedia Software
---

### Post by Kieeps on 2009-06-24
Since I installed Kubuntu on the comp (that was at early 8.10) it's been working out of the box with everything, then 9.04 came and i waited for a while before upgrading and STILL everything worked...exept for one thing, i wasnt able to watch any 720p and up quality videos like i once used to be able to so i figured "hmmm...maaaaby i should try installing the drivers from ATI to see if that solves it since i'm currently using the drivers that came with ubuntu"
Said and done....the problem is that they really didn't work at all, I did some googleling (ALOT) and found something called radeonhd and gave those a try. now everything was back to normal...exept the openGL hardware acceretaion didn't work so XBMC refused to start....and that is not ok since thats mainly why i have this comp set up :D anyhow...i wanted to roll back the drivers to what they where by default to never ever tuch this again but....i have no idea how to...i even re-installed kde to see if that did anything....well not just 'cus of that...reinstalled KDE mostly 'cus in my desperation i did a quick:
```
sudo apt-get purge libgl1-mesa-glx
```
and that took alot of packages with it :P

here is some info that might be needed to give some advice:

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
```

And here is the xorg.conf (this is a mess atm and i have no idea if i'm skilled enough to even clean it up, seems like alot of ati crap is still in there)
```

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Module"
        Load    "dri"
        Load    "GLcore"
        #       Disable "dri2"
EndSection

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver  "vesa"
        #       Option      "UseFastTLS" "1"
        #       BusID       "PCI:1:0:0"
EndSection

Section "ServerFlags"
        Option      "DontZap" "True"
EndSection

```

Ofc i will continue to google and try stuff to see if i can solve this on my own but it would be nice if someone had some pointers on what to do since i know i'm just using this as a way to purspone cleaning up my place :P cus this is more important right?

---

