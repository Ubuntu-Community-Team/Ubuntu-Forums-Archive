---
title: "External monitor resolution is not recognized"
date: 2012-02-06
forum: Multimedia Software
---

### Post by almikul on 2012-02-06
Good day fellow ubunters,

I have a problem with the graphics card not recognising the external monitor's information. The laptop is Dell E6220 and the graphics card is Intel HD 3000. The monitor is a typical Dell 22". When I go to System Settings -> Displays, it shows "Unknown" for the external monitor and only proposes generic resolutions (i.e., 1024x768, 800x600). 

The monitor is fine because a different laptop running Karmic 9.10 could perfectly recognise it. I know it is a problem with the hardware because even Windows 7 could not automatically set the right resolution, but at least it remembered the settings after I set it manually. For Ubuntu, now I use xrandr --newmode, --addmode and --output to set the correct resolution in .xprofile. Usually it works, but sometimes the monitor would not turn on (not sensing the input, I guess) or the desktop background would be messed up even though the positioning of the two displays looks fine in the settings. 

I would like to ask if it is possible to see whether the monitor is connected, and to see what information it shows to the laptop (if any), and depending on this, to assign the right mode. I know that using .xprofile is not ideal because it is executed very late in the login process. Is it possible to execute my custom script earlier before the system attempts to deal with the monitor itself? 

I apologise for being cumbersome and not very clear, but I hope you got the main idea of what I am trying to do. Your help will be very appreciated.

---

### Post by almikul on 2012-02-14
Bump. Any suggestions at all? :(

---

### Post by SorryGoFish on 2012-02-14
> **almikul said:**
> Bump. Any suggestions at all? :(

Problem sounds clear enough to me. Maybe try asking at askubuntu.com?

**Edit**
Some possibilities...
[http://askubuntu.com/questions/40219/monitor-preferences-monitor-unknown](http://askubuntu.com/questions/40219/monitor-preferences-monitor-unknown)
[http://askubuntu.com/questions/77405/monitor-shows-up-as-unknown-on-a-dell-d630](http://askubuntu.com/questions/77405/monitor-shows-up-as-unknown-on-a-dell-d630)
[http://askubuntu.com/questions/83681/intel-graphics-3000-hd-card-only-displays-at-1024x768-over-hdmi](http://askubuntu.com/questions/83681/intel-graphics-3000-hd-card-only-displays-at-1024x768-over-hdmi)

---

### Post by jpc2769 on 2012-09-27
I am having a similar problem. I am using a Lenovo Thinkpad x230t running Kubuntu 12.04 and trying to connect an old Samsung 23" LCD TV as a monitor using the VGA input. The manual for  for the Samsung says that it is capable of 1360x768, but when I hook it up to my laptop, the best resolution it will put out to the monitor is 1024x768, which chops off the side of my desktop.

Does anyone know how I can get Kubuntu to recognize that the monitor is capable of a higher resolution?

Jason

---

### Post by almikul on 2012-09-27
> **jpc2769 said:**
> The manual for  for the Samsung says that it is capable of 1360x768, but when I hook it up to my laptop, the best resolution it will put out to the monitor is 1024x768 ...

Does anyone know how I can get Kubuntu to recognize that the monitor is capable of a higher resolution?
Here is what you can try. From terminal, do this:
```
cvt 1360 768
```
You will get something like this:
```
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync 
```
Now, open .xprofile in your home directory (or create it if it does not exist), and add these lines:
```
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1360x768_60.00"
```

Of course, you have to replace VGA1 with whatever output you are using. To get the list of available outputs, do this:
```
xrandr -q
```

After you log out (or restart) and connect your TV, you can go to Settings -> Displays and set set the right resolution because it will have it in the list. It will still not recognise the TV resolution automatically, but it will have the correct resolution in the list (because you added it) and will hopefully remember to set it automatically 2nd time you connect this exact TV.

---

### Post by jpc2769 on 2012-09-27
> **almikul said:**
> Here is what you can try. From terminal, do this:
```
cvt 1360 768
```
You will get something like this:
```
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync 
```

I did that, and got the output you predicted.

> **almikul said:**
> Now, open .xprofile in your home directory (or create it if it does not exist), and add these lines:
```
xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1360x768_60.00"
```

Of course, you have to replace VGA1 with whatever output you are using. 

I did this part as well.

> **almikul said:**
> To get the list of available outputs, do this:
```
xrandr -q
```

After you log out (or restart) and connect your TV, you can go to Settings -> Displays and set set the right resolution because it will have it in the list. It will still not recognise the TV resolution automatically, but it will have the correct resolution in the list (because you added it) and will hopefully remember to set it automatically 2nd time you connect this exact TV.

I typed this after modifying the .xprofile, but the output still only showed 1024x768, and when I restarted the computer I still could not make the resolution better than 1024x768.

Jason

---

