---
title: "Lost 1280x1200 on nvidia"
date: 2010-09-08
forum: Multimedia Software
---

### Post by Innigo on 2010-09-08
Overnight, I seem to have lost the preferred native reolution of my monitor which is 1280x1200
I'm on Ubuntu 10.04 and Synaptic shows nvidia-current installed as well as nvidia-glx-185, 180, 173, 96 and some other stuff. I have partner repo enabled which is, I believe, where I got my Nvidia driver from.
output of:
$sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

output of:
$ xrandr
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1920 x 1200
default connected 1360x768+0+0 0mm x 0mm
   1024x768       50.0     63.0  
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  
   1360x768       63.0* 
   1920x1200      50.0

---

### Post by Innigo on 2010-09-09
$xrandr  -d default --mode 1920x1200
didn't work
Then I tried 
$sudo dpkg-reconfigure -phigh xserver-xorg
which didn't seem to work either but on rebooting...
Full native res. 1920x1200 is back again :-)

---

