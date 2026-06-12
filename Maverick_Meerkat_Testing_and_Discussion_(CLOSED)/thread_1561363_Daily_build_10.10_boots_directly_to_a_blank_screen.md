---
title: "Daily build 10.10 boots directly to a blank screen"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by oneiota on 2010-08-26
The Maverick desktop AMD64 iso's I've tried so far (23rd and 25th August 2010) lead directly, without any GUI or interactive steps, to a nice purple splash screen with a moveable mouse pointer shown, and nothing else.

This is the case if I boot with CD or USB.

Since others have been able to install and test Maverick Meerkat, I'm assuming it must be something to do with my hardware:
    
    VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)

    ASUS P6T DELUXE V2: DDR3, 2-Way SLI & CrossFireX on Demand

Any idea where to start on this issue?  I've not experienced a problem like this with a previous release.

---

### Post by jppr on 2010-08-26
I think that Ubiquity is broken and new kernel don´t have come yet new debian-installer packages...

---

### Post by oneiota on 2010-08-26
Thanks for the reply.

If anyone can let me know how to test drive (or install) version 10.10, given the situation, that would be splendid.

---

### Post by VMC on 2010-08-26
> **oneiota said:**
> The Maverick desktop AMD64 iso's I've tried so far (23rd and 25th August 2010) lead directly, without any GUI or interactive steps, to a nice purple splash screen with a moveable mouse pointer shown, and nothing else.

This is the case if I boot with CD or USB.

Since others have been able to install and test Maverick Meerkat, I'm assuming it must be something to do with my hardware:
    
    VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)


Any idea where to start on this issue?  I've not experienced a problem like this with a previous release.

oneiota, I've been dealing with this issue for some time now. I have nVidia GeForce 6150 SE, and this is how I get Maverick installed:

Once you see that purple screen, type ```
Ctrl+Alt+t
``` , that will bring up a terminal. Then issue ```
sudo ubiquity
```. Ubiquity should now start and run to completion. It has for me anyhow. Another way is to push any-key when you see the "keyboard/human" figure at the bottom of the screen. Then push "Try Ubuntu..." Then start Ubiquity from the Install Ubuntu Icon from desktop. Either way has worked for me for several sessions now.

Also check you var logs and home dir video log to see the errors that nVidia has. It sees the available screens but can't use any of them for some reason. Oddly enough it does work from Try Ubuntu.

---

### Post by cariboo on 2010-08-26
Press Ctl-Alt-t to open a terminal, then at the prompt type:

```
sudo ubiquity
```

The above command will start the installer. The last time I tried it, grub didn't get installed, you you may have to install it manually.

---

### Post by VMC on 2010-08-26
One thing I noticed, is after starting ubiquity and going through the screens. If you see the Wireless dialog come up and you don't have wireless but lan/ethernet, then abort ubiquity and try starting ubiquity again.

 Usually after the second attempt it will recognize your internet and continue without errors, and you shouldn't see the Wireless dialog again.

---

### Post by Wobblybob on 2010-08-26
I've had this issue, when I get to the first purple screen with the 2 icon at the bottom I press F6 and the select language screeen pops up followed by the install menu.

---

### Post by oneiota on 2010-08-27
> **Wobblybob said:**
> I've had this issue, when I get to the first purple screen with the 2 icon at the bottom I press F6 and the select language screeen pops up followed by the install menu.


That works!  It seems if I hit any key at the point you mention, it brings up the language screen, followed by the install menu.  

Now I can test Maverick Meerkat - thank you!

---

### Post by jppr on 2010-08-27
Just did fresh todays live-cd installation [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
and everything goes wihtout problems :p I have amd64  and Nvidia card but system run nouveau-driver and that works fine too

---

### Post by tanari on 2010-08-29
I have just black screen :(. (tried alpha 3 and daily aug 29 live USB).

video: radeon 5750

---

### Post by jppr on 2010-08-29
Remove fglrx-package and boot system

---

### Post by tanari on 2010-08-29
thank you, now I can boot :), but no compiz and gnome shell :(

---

### Post by VMC on 2010-08-29
> **tanari said:**
> I have just black screen :(. (tried alpha 3 and daily aug 29 live USB).

video: radeon 5750

Have you tried adding this to the linux line:

```
radeon.modeset=0 xforcevesa
```

I played around with the modeset, using either "0" or a "1". Also I needed the xforcevesa to enable VT's.

---

### Post by tanari on 2010-08-29
> **VMC said:**
> Have you tried adding this to the linux line:

```
radeon.modeset=0 xforcevesa
```

I played around with the modeset, using either "0" or a "1". Also I needed the xforcevesa to enable VT's.

what is it? where I need to add this:confused:

---

### Post by VMC on 2010-08-29
> **tanari said:**
> what is it? where I need to add this:confused:

When you see the grub menu, go to your Meverick selection, push Tab, then arrow down to "linux" line. go to the end of that line , then add it there. Then Ctrl+x to boot. See if that works first.

---

