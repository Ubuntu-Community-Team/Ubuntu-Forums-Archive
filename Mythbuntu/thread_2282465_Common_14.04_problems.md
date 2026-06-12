---
title: "Common 14.04 problems"
date: 2015-06-14
forum: Mythbuntu
---

### Post by khPWXxF on 2015-06-14
This is a list of frequent problems experienced with Mythbuntu 14.04 and Mythtv 0.27 which have surfaced in the forums.
It is neither an exhaustive list nor particularly authoritative, but it may help you! 
Corrections and additions welcomed.

**Unstable Nvidia graphics**

There are two issues here:

1.  Frontend code incompatibility with 334.21 drivers.
see this:   [https://forum.mythtv.org/viewtopic.php?f=36&t=98](https://forum.mythtv.org/viewtopic.php?f=36&t=98)

2.  Later drivers do not support ‘legacy’ GPUs such as 8200, 8300 and 8400.  This occurred at some point between 304 and 331.

You can list the drivers in use with:
```
ubuntu-drivers list

```
Regression to an earlier version is necessary – version 304 seems stable with nVidia 8300 and UK standard definition DVB-T recordings (though not as good as version 295 with the HD demo!).  With Ubuntu do this:
```
sudo apt-get update
sudo apt-get install nvidia-304

```
If the system is not stable enough to even run a terminal session without screen fireworks then either ssh from another system to downgrade it or try safe mode:

**Safe mode**

Tap the left shift key repeatedly as it is booting to get the recovery mode menu.  

The ‘Root’ option seems entirely logical here but you may find that it will only give you ‘read’ access to the filesystem. 

Instead, choose “Network option”.  It may well give a fatal warning and put you back at the safe options menu but in doing so will switch you to read/write mode.

Now choose “Root” option and you will be in read/write mode.

**The picture size does not match my screen**

There may be two issues here:

1. The screen resolution may not be matched.  For example, the computer is outputting 1920x1080 but the screen expects 1360x768 so only the top left of the picture shows.  If vice-versa, the picture gets compressed into the top left of the screen with empty areas to the right and below

Adjusting pixel counts in Mythtv frontend > setup > appearance > gui sizes all to zero may fix this.  Failing that:

You can ascertain the resolutions which your screen will accept with
```
xrandr

```
This will show you the signal presently being sent to the screen, and the preferred resolution for the screen.  You can alter the output with randr eg:
```
xrandr --display HDMI-0  --mode 1920x1080

```The setting are not remembered over a reboot so will need to be in a script executed at each startup.
      
You may prefer to try out arandr for a graphical interface to xrandr.  This will export a suitable script.
    
2. Overscanning.  In the early days of TV with analogue CRT screens, screen geometry tolerances were poor and TV manufactures would deliberately ‘lose’ picture around the edge to prevent unpleasant artefacts.  Modern TV sets often maintain this practice, and it will typically result in lost picture at the edges.  This might result in (say) the ‘next’ button on setup screens being partially lost.  The converse (underscan) may also apply with for example a flickering line at the top of the screen.

Many sets can be adjusted to eliminate this problem and show the full picture.  See appendix 1 below for a list of sets and steps to be taken.

Failing that, adjusting pixel counts in Mythtv frontend > setup > appearance > gui sizes may help, or using xrandr with the 
–scale parameter
Eg
```
xrandr –display HDMI-0 –mode 1920x1080 –scale 1.1x1.1

```
Values of scale greater than 1 will shrink the image, those less will expand it.

**Intrusive Toolbar across top of screen.**

Early releases of Mythbuntu 14.04 and Mythtv 0.27 had an issue that the xfce toolbar would remain at the top of the screen after the frontend started.  

See 
[http://ubuntuforums.org/showthread.php?t=2222438&](http://ubuntuforums.org/showthread.php?t=2222438&)

This was fixed by 0.27.1 for most but for a few it remained.  Having non zero (ie non default) values of screen pixels in the frontend>setup>appearance page is one cause, though separate gui and video sizes may resolve it.

If all else fails, the xfce bar can be eliminated by including a line at the start of /usr/bin/mythfrontend to spawn a script:  
```
/usr/bin/fullscreenfrontend.sh&

```    
The file /usr/bin/fullscreenfrontend.sh should be executable and contain:
```
#!/bin/bash
#get rid of junk at top of screen
#this script called from /usr/bin/mythfrontend
#wait for frontend to start
for kip in 3 1 1 1 1 1 1 1 5
do
       sleep $kip
      [ "$(wmctrl -l | grep 'MythTV Frontend')" ] && break
done
#make it full screen
DISPLAY=:0 wmctrl -r "MythTV Frontend" -b add,fullscreen
exit

```or (more simply)
```
#!/bin/bash
sleep 10
DISPLAY=:0 wmctrl -r "MythTV Frontend" -b add,fullscreen
exit

```
Note however that the mythfrontend script changes may be lost over an update.
   
**Blank screen if HDMI TV turned on after computer.**

This bug is not straightforward and there seem to be a variety of solutions. See here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

Some have found that a suitably crafted xorg.conf will fix this problem (others report that is does not).  Recent Nvidia drivers have been written to operate without the configuration file /etc/X11/xorg.conf.  However, a suitable configuration file is required to prevent blank screens if the TV is powered on after the computer.
See:  [http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)

You will need a copy of a good working /etc/X11/xorg.conf as a start.  If this does not exist but a file 
/etc/X11/xorg.conf.<date> does exist then use that and copy it.  

Otherwise create one with the nvidia-xconfig utility, then edit it (with your favourite editor) and include in the ‘devices’ section 
```
Option   "UseHotplugEvents"   "false" 

```
xorg settings are documented here:
[http://us.download.nvidia.com/XFree86/Linux-x86/310.44/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/310.44/README/xconfigoptions.html)


When this is all working you will be advised to make a copy because, unfortunately there is a further trap:

**xorg.conf vanishes**
There is some process running which renames /etc/X11/xorg.conf to xorg.conf.<date> so making it inaccessible.  I suspect that software updates can trigger this.  
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546)
   
You can frustrate this undesirable behaviour by making the file immutable.
```
sudo chattr +i xorg.conf

```Check it with
```
sudo lsattr –l xorg.conf

```(look for i in the string on the left).
   
If you wish to remove immutability then
```
sudo chattr -i xorg.conf

```Both chattr and lsattr need root privileges (eg sudo in Ubuntu).

**Frontend running with 100% CPU.**

Contribute to this debate here:
[http://ubuntuforums.org/showthread.php?t=2251955](http://ubuntuforums.org/showthread.php?t=2251955)


**Backend consumes 100% cpu**
[https://forum.mythtv.org/viewtopic.php?f=2&t=815](https://forum.mythtv.org/viewtopic.php?f=2&t=815)

**DVD/Blu-ray issues**
a)  Cannot find DVD
Change setup> media settings> videos settings> player settings to your device eg /dev/cdrom

b) Cannot eject disk - 'no device to eject'.
Fixed by ```
sudo apt-get install udisks
```

c) for a more comprehensive article:     [http://ubuntuforums.org/showthread.php?t=2249102](http://ubuntuforums.org/showthread.php?t=2249102)

**Appendix 1.  Eliminate overscan with your TV.**
Many modern TV sets will require a ‘full screen’ or 'games' option to eliminate overscan.  This is how to do it on some sets:

JVC LT22C540        HDMI > Menu > Picture > Aspect Ratio > Full
Samsung  UE32F5500.    Source > HDMI > Tools > Picture Size > Screen fit

If your TV is not in this list, please add it!

**Acknowledgements**
Thanks to all the contributors to the forums who have provided the answers and to Lester Burnham for constructive comment on this text.

Happy viewing!
Phil Brady

---

