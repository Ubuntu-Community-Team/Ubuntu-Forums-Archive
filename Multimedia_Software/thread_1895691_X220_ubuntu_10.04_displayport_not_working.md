---
title: "X220 ubuntu 10.04 displayport not working"
date: 2011-12-15
forum: Multimedia Software
---

### Post by vivien_yan on 2011-12-15
I got a ThinkPad X220 + Ubuntu 10.04 64bit. Graphics card should be Intel 3000HD. Now, if I connect an external monitor using VGA, it is working. But when I tried to use an external monitor using the displayport, I can see the external monitor in system->preference->monitors but the external monitor only gives me a black screen. Can anyone tell me what I should do to get the external monitor working using display port? Thanks in advance!

---

### Post by 2F4U on 2011-12-15
Maybe this helps

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220")

---

### Post by vivien_yan on 2011-12-15
I already did what was said on that page. Not working......

> **2F4U said:**
> Maybe this helps

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220)

---

### Post by ShamoIdol on 2011-12-31
I own x220 and x200s. 
You have to setup everything using xrandr (man xrandr).

---

### Post by vivien_yan on 2012-01-09
Can you give me more details? I have xrandr and I typed in "xrandr" and got the following information

~$ xrandr
Screen 0: minimum 320 x 200, current 3286 x 1200, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected 1920x1200+1366+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)


But still, the monitor cannot get the signal and goes directly to the power saving mode.

> **ShamoIdol said:**
> I own x220 and x200s. 
You have to setup everything using xrandr (man xrandr).

---

### Post by vivien_yan on 2012-03-10
[SIZE=4]Reinstall the operating system to Ubuntu 11.10. The displayport works out of box. Problem solved but now have to work on the bluetooth headset.  [/SIZE]

---

