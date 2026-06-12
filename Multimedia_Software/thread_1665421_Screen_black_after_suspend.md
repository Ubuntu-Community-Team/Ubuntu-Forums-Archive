---
title: "Screen black after suspend"
date: 2011-01-12
forum: Multimedia Software
---

### Post by wiley692 on 2011-01-12
I am using a Gateway 700SE with a VX920 monitor.  After suspending the computer then waking it up, the screen stays black but it is awake and so is the computer. It works fine the rest of the time and used to not do this with an older version of Ubuntu (I don't remember which one). I don't know what kind of video card is in the computer nor how to find out without opening it up. Are there any relatively simple solutions for this problem? I really don't want to go back to Windows on this machine if I can help it.

---

### Post by tjones00 on 2011-01-12
It seems this is becoming a current issue when resuming from hibernation/sleep.

So some assumptions on my end here. 

1) Your using the opensource driver for whatever your video card is.

2) This driver was installed by default and therefore is making heavy use of kms. There is no xorg.conf on your system.

3) You have made any custom edits to the graphics settings.

It appears that some people are trying to correct this issue by turning the sleep option off on the computer.

A static xorg.conf and turning off kms might work as well.

When the computer is working as expected try the following.

Applications > Accessories > Terminal

```
sudo Xorg -configure
```

Then type the following.

```
gksudo gedit /etc/default/grub
```

Find the line "quiet splash" and replace with "nomodeset" then save the file.

```
sudo update-grub2
```

Then reboot. If this doesn't work to reverse the changes do the following.

Edit /etc/default/grub and put quiet splash back in then update-grub2 again. Remove the file xorg.conf from /etc/X11/xorg.conf.

---

### Post by wiley692 on 2011-01-12
That fixed the black screen after suspend but now my maximum resolution is way lower than it used to be. Everything on the screen is huge.

---

### Post by tjones00 on 2011-01-12
It's probably easiest to try a modeline.

undo the /etc/default/grub edit update-grub and then

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.temp
```

reboot

Once you have the resolution you want with kms enabled probe xrandr.

```
sudo xrandr -q > ~/xrankmsres.txt
```

Also make a copy of the Xorg.0.log from the current session.

```
sudo cp /var/log/Xorg.0.log ~/Xorgkmsres.log
```

Turn off kms (grub edit and update) again and move the xorg.conf back into position.

```
sudo mv /etc/X11/xorg.conf.temp /etc/X11/xorg.conf
```

reboot

Now you have two files in your /home/user/ directory xrankmsres.txt and Xorgkmsres.log these files show the resolutions that were possible with kms enabled. Technically you only required the xorg.log but doesn't hurt to compare it to the xrandr output as well.

You can use the information contained in both of those files to create whats called a modeline in the monitor section of your xorg.conf listing the desired resolutions.

Read this if you haven't setup a modeline before.

[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

eg.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        VendorName      "Sun"
        ModelName       "X7200A"
        Option          "DPMS"
        ModeLine        "1600x1200" 132.000 1600 1608 1672 1776 1200 1205 1215 1239 +hsync +vsync
EndSection
```

---

### Post by intelligence storm on 2011-12-31
Sorry, it seems too old (one year ago) -Ah ! happy new year everyone :D:popcorn:-
but the problem I can't solve with commands above:confused:
can you help me more please :(:(
in addition of suspending doesn't work but still in black mode ! the Hibernate do shutdown for the laptop !!

Note:my Graphical Card is integrated, laptop is MSI

---

