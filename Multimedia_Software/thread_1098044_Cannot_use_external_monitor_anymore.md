---
title: "Cannot use external monitor anymore"
date: 2009-03-16
forum: Multimedia Software
---

### Post by ztrange on 2009-03-16
I used to connect my laptop to a TV. But now it doesn't work anymore. I haven't made any changes to my computer unless some update of the ones I get automatically.

Before, I plugged the TV to my computer, went to screen resolution and checked clone screen. Now, when I do the same, the TV just keeps with the "no signal" on screen and when I re open the screen resolution program, the clone screen checkbox is unckecked.

I tried booting my laptop with the TV plugged in and I seemed to work fine until I got to the login screen which displayed fine on both TV and laptop screen. But then, when I logged into gnome, The TV got the "no signal" again and I was unable to use it like an external monitor.

I also, tried something I saw somewhere, I plugged the TV while on session, opned a terminal and typed 

 sudo dpkg-reconfigure -phigh xserver-xorg

But it didn't seemed to work. Also went to terminal with Ctrl + Alt + F1 and then back to X with Alt + F7 but the TV stayed all the time with the "no signal".

Well, any help will be appreciated, my sister says that she would rather use windows than Ubuntu with these kind of issues. Her laptop with XP works fine with the TV.

---

### Post by ztrange on 2009-03-19
Come on, there's gotta be some expert in here...

Please!

---

### Post by linux_tech on 2009-03-19
If you type in terminal 
```
xrandr
```
Does the external monitor tv show up?

---

### Post by roblubbers on 2009-03-19
what type of videocard are you using and which drivers? The ones ubuntu provided?

---

### Post by ztrange on 2009-03-20
Ok, I had my computer powered on, and I plugged the tv into it. I went to screen resolution and checked the clone screen. My laptop screen went dark and back on with the resolution changed to 1024 (the one compatible with the tv) The TV just said "no signal". I went to a terminal and typed xrandr and just got the follwing: (Without change in the tv screen)

```
-----@-----:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA connected (normal left inverted right x axis y axis)
   1152x864       60.0  
   1280x768       59.9  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  

```

My laptop has an Intel 945 graphic chip, as listed by lspci:
L Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


The driver I'm using is the default Ubuntu one, never changed it but always wondered if my chip is working at its full potential.

---

### Post by ztrange on 2009-03-24
Hello... anyone??

---

### Post by kumar_physics on 2011-04-29
I have the same problem. I found an workaround, but not the solution. Just load the old kernel version from the boot menu. It worked for me and I am waiting for the bug fix.

---

