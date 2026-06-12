---
title: "HDMI using 12.04 doesn't work at all"
date: 2012-06-01
forum: Multimedia Software
---

### Post by Yellowbelly on 2012-06-01
It seems like other people have success using hdmi but I have a laptop with an hdmi out port. Whenever I connect to a tv, there is no recognition of the display. Even when I open up settings and click detect displays, nothing happens. Any ideas?

---

### Post by Cheesemill on 2012-06-01
Try connecting the HDMI cable to the TV and turning the TV on **before** turning on the laptop. Does it make a difference?

---

### Post by sammiev on 2012-06-01
As Cheesemill said. I need to reboot my laptop after plugging my cable in to watch a movie. Most other items seem to work other wise. :)

---

### Post by Yellowbelly on 2012-06-01
The TV recognized that something was plugged in but it had no signal. Ubuntu didn't recognize it too, so the exact same thing happened. It works immediately and well under windows vista.

---

### Post by DMGrier on 2012-06-01
Back when I was using 10.04 for some reason it would not work on some TV's, I know on my current TV I have 3 HDMI ports and it does not work on HDMI 1 which next to the port says DVI which from what I read on google said that is usually the problem. So it will only work on HDMI 2 and 3.

---

### Post by cortman on 2012-06-01
What's the output of 

```
xrandr
```

It may just need to be configured, or you may need a different graphics driver.

---

### Post by Yellowbelly on 2012-06-01
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1024 x 600, maximum 1024 x 600
default connected 1024x600+0+0 0mm x 0mm
   1024x600       50.0* 
   800x600        51.0     52.0  
   720x400        53.0  
   680x384        54.0     55.0  
   640x480        56.0     57.0     58.0     59.0  
   640x400        60.0  
   640x350        61.0  
   576x432        62.0  
   512x384        63.0     64.0     65.0     66.0  
   416x312        67.0  
   400x300        68.0     69.0     70.0     71.0     72.0  
   360x200        73.0  
   320x240        74.0     75.0     76.0     77.0  
   320x200        78.0  
   320x175        79.0  

The laptop was not plugged into the tv when I ran this. I have no idea if that's relevant at all. For whatever matters, the laptop is an Asus n10ja2, you'll see the small screen size.

---

### Post by cortman on 2012-06-01
Looks like you may need to install the Nvidia drivers- your laptop has the GeForce 9300M card. [Here's]("http://askubuntu.com/questions/43895/how-do-i-install-the-nvidia-driver-for-a-geforce-9300m") a link on installing those drivers, and now that you know the model you should be able to google-fu your way through any difficulties (but always feel free to ask on the forums too). 
Good luck!

---

### Post by digimark on 2013-01-15
Hi All,

same issue here...

xrandr responds

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


it looks like the ;laptop cannot see a device attached.....any ideas...im a very noob at this so anythihng step by step would be useful.....BTW it works fone when connected via VGA....

Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


Please any ideas would be useful.

thanks

---

### Post by johneverard on 2013-08-27
I am having the same problem.  I am running Ubuntu 12.04 and trying to send video down an HDMI cable to my television (I use the HDMI2 port to prevent problems others have reported with HDMI1) but the television sees nothing.  I have an HP Pavilion dv6 laptop that has an ATI Mobility Radeon graphics card.  I have been through system tools - system settings - additional drivers and installed the ATI propietary driver from there, but still no result.  The problem occurs whether or not I plug the cable in before I switch on the computer.  

xrandr gives:

Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1368 x 768, maximum 1368 x 768
default connected 1368x768+0+0 0mm x 0mm
1366 x 768 0.0
1368 x 768 0.0*

Grateful for any advice!

---

### Post by jlh68 on 2013-08-27
It works with my Acer Aspire TimelineX just fine.  (I am using Ubuntu 12.04.2LTS).  I even found out how to get the sound to work thru the HDMI cable.  I do have to turn laptop and tv on in a certain order to get it to work.  I can't remember the order, but it doesn't take long to try it either way.

---

