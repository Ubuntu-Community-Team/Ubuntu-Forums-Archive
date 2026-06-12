---
title: "how to install+configure ATI Radeon HD 5450 ?"
date: 2011-01-05
forum: Multimedia Software
---

### Post by trekki on 2011-01-05
After installation of the new hardware i activated the ATI closed source driver. There is an issue with the screens
1st screen, via DVI: i cannot change to the native screen resolution
2nd screen, via VGA: the background of any window is not drawn. Means: i can see lots of parts of other windows after moveing or closeing them.

Therefore i was searching for an alternative and found the hint to uninstall the ATI driver and use the open source one. 

After uninstall and reboot (requested by a parallel system update), some boot messages i have no screen output anymore. Means: two black screens. These are going into sleep mode after a few seconds. How can i get a running system again? Optimal would be, that i have full support for both screens.
Same happens in failsave mode.

System environment:
Ubuntu 10.04
AMD Athlon 64 X2 3800+, 4G RAM, motherboard ALiveNF6G-DVI (internal graphic deactivated), ATI Radeon HD 5450

Any hints for me?

trekki

---

### Post by pme 72 on 2011-01-05
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

When I ran into issues with fglrx in previous releases I ran the "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" instructions from the above link. 

That always seemed to work for me to reinstall the Radeon driver. The only issue I ever had was using them with Hardy Heron 8.04. The removal of the proprietary driver worked but I was unsuccessful attempting to reinstall fglrx. In subsequent releases when I removed fglrx I did not attempt to reinstall it. I have subsequently run into instructions for reinstalling fglrx here in posts on the forum but have no experience with them. 

My tech level is just very basic though.

---

### Post by trekki on 2011-01-06
Actually the screens gets blank in the boot phase and the switches off (the monitors only, not the pc). How can i avoid this? Otherwise i have no chance to enter the commands given in your link.

---

### Post by pme 72 on 2011-01-06
What happens if you enable your internal graphics adapter?

---

### Post by tjones00 on 2011-01-06
To me it sounds like you left the xorg.conf file behind after uninstalling fglrx. 

Lets get you back to a desktop first.

When the screen goes blank and just sits there press Ctrl+Alt+f2.

This will switch to a different tty login go ahead and login.

1) shutdown x server

```
sudo service gdm stop
```2) make sure fglrx is gone

```
sudo find / -name fglr*
```If you see any module files at this point that's bad. I don't believe you stated how you installed the driver from the web or Ubuntu.

Follow the purge directions at the link pme 72 posted [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I perfer the 
**Problem:  Need to fully remove -fglrx and reinstall -ati from scratch**


method.

> sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati[FONT=monospace]
[/FONT]sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
If you follow it to that point you should be setup to use the open source driver again.

3) Now make sure the xorg.conf is gone.

```
sudo rm /etc/X11/xorg.conf
```4) Lastly make sure ati or radeon isn't blacklisted
```

sudo nano /etc/modprobe.d/blacklist.conf
```If you see radon or ati in this file remove/comment their entries save and close. If this file doesn't exist on your system(is blank) that's fine as well.

```
sudo reboot
```You should now be back to the open source driver and clear of any fglrx.

---

### Post by trekki on 2011-01-07
> **tjones00 said:**
> 
1) shutdown x server

```
sudo service gdm stop
```
Answer```
stop: Unknown instance:
```,
> **tjones00 said:**
> 2) make sure fglrx is gone

```
sudo find / -name fglr*
```If you see any module files at this point that's bad. I don't believe you stated how you installed the driver from the web or Ubuntu.

I found 16 file, my installation was via DVD some years/versions ago. Since then i have followed each update.

> **tjones00 said:**
> 
...
3) Now make sure the xorg.conf is gone.
4) Lastly make sure ati or radeon isn't blacklisted
...You should now be back to the open source driver and clear of any fglrx.
Done without any error messages. 
After reboot i had the possibilty to select the screen resolutions and positions. This have a strange result.
First there is an offset between the top of the mouse pointer and the focus. You can see this here
[IMG]http://i1045.photobucket.com/albums/b459/trekkiOSM/P1150758.jpg[/IMG]
I have marked the mouse and the focus. This makes the usage very problematic.

Also the desktop have strange elements
[IMG]http://i1045.photobucket.com/albums/b459/trekkiOSM/P1150759.jpg[/IMG]
- there is a bar over the whole bottom of the left screen
- the mouse movement to the right is blocked randomly at any of the red, upright lines
- the second screen shows nothing but is not powered down

It seems, that my config is on a good way to be working, but  still something is missing. Any idea?

I did not activate the internal adapter again because your description seems to give me more details.

---

### Post by TG12 on 2011-01-11
I posted a guide here which makes it nice and simple
[http://ubuntuforums.org/showthread.php?t=1664919](http://ubuntuforums.org/showthread.php?t=1664919)

---

