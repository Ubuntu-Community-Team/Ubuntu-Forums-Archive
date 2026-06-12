---
title: "Laptop Screen Not Working"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by Ryxxui on 2007-04-06
I just installed Ubuntu for the first time today, and after fighting for several hours just to get something to show anywhere (it was a difficult process), I finally got into Ubuntu to realize that Ubuntu decided (or maybe I decided and didn't notice) that my extra CRT monitor that I use as a second monitor was considered to be my main monitor, and that the screen on my laptop was not being seen at all.  After screwing around for a while and installing the latest NVidia drivers (I'm running a GeForce 6600) I got the second screen to work, but every time that I restart the X Server every one of my video options goes back to default.  So, I cannot set up my two screens as seperate X Windows, and every time I restart Ubuntu I need to reset the refresh rate of the CRT and re-enable and re-position the laptop screen. 
Does anyone have any suggestions for a) how to get the settings to stay and b) how to get the laptop screen to be the primary screen?
Thanks!!

---

### Post by reacocard on 2007-04-06
> **Ryxxui said:**
> I just installed Ubuntu for the first time today, and after fighting for several hours just to get something to show anywhere (it was a difficult process), I finally got into Ubuntu to realize that Ubuntu decided (or maybe I decided and didn't notice) that my extra CRT monitor that I use as a second monitor was considered to be my main monitor, and that the screen on my laptop was not being seen at all.  After screwing around for a while and installing the latest NVidia drivers (I'm running a GeForce 6600) I got the second screen to work, but every time that I restart the X Server every one of my video options goes back to default.  So, I cannot set up my two screens as seperate X Windows, and every time I restart Ubuntu I need to reset the refresh rate of the CRT and re-enable and re-position the laptop screen. 
Does anyone have any suggestions for a) how to get the settings to stay and b) how to get the laptop screen to be the primary screen?
Thanks!!

Disconnect the external monitor, then follow these steps. You may want to print out a copy, as you won't have a GUI during this.

Log out. Press CTRL+ALT+F1. Login at the prompt with your normal username and password. Enter these commands one at a time, entering your password when prompted:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start && exit
```

That should completely reconfigure your xserver with the defaults, and since the external monitor isn't plugged in, it'll use your laptop monitor as the primary.  After this, all you'll need to do is enable the external monitor, and there are a number of threads on that already, just use the search. You'll also probably have to reenable the NVidia drivers in xorg.conf.

---

