---
title: "Dual monitor: Ubuntu 11.04 does not detect second monitor"
date: 2013-03-12
forum: Multimedia Software
---

### Post by pakasmamu on 2013-03-12
Hi there, I have two identical monitors that I would like to connect to my computer running Ubuntu 11.04 and operate in "dual monitor" mode. Each monitor has 1 DVI, 1 HDMI and 1 VGA port. The desktop has 1 VGA and 2 DisplayPort (DP). My main problem is as follows: regardless of whether I connect the second monitor via VGA or DP, ubuntu does not detect it and the monitor always displays "no signal". Here is what I have tried so far:

[LIST=1]
[*]Connected both the monitors to the desktop via 2 DisplayPorts. Tried ***System -> Preferences -> Monitors***: It detects only one monitor and its named *Unknown*. Clicking on the button *Detect Monitors* does not change anything. 
[*]Tried to see if all the ports are listed. Output of ***xrandr -q*** (monitors connected to desktop via DP), only *default* is listed*.*
[I]xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080       0.0* 
   1280x1024       0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0
[/I] 
[*]I thought the DP to VGA cables and/or the monitors may not be working properly. But that's not the case. I tried connecting every pair of (monitor, cable) to the desktop and it works fine. Problem is that when I connect both the monitors, the second one is not detected, regardless of the port used. 
[/LIST]
 _System Information_

[LIST=1]
[*]OS: Ubuntu 11.04
***uname -r***
*2.6.38-16-generic*

***lsb_release -a***
[I]No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty[/I] 
[*]Output of ***lspci | grep -i VGA***
*00:02.0 VGA compatible controller: Intel Corporation Device 0162 (rev 09)* 
[*]Output of ***lsmod | grep -i video***
*video                  19623  0* 
[*]I have read posts about modifying xorg.conf and/or monitors.xml but I am wondering if there's a better way of doing this. I was not able to  locate xorg.conf @ /etc/X11/ (maybe its in a different location). I can  post ~/.config/monitors.xml if that might help. 
[/LIST]
 Please let me know if I should post additional information. Thanks a lot in advance!

---

