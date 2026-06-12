---
title: "Just upgraded, and no ATI video"
date: 2009-06-30
forum: Multimedia Software
---

### Post by sjv on 2009-06-30
I just upgraded to jaunty and have no video whatsoever, just a black screen. I have tried the steps outlined here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

as well as trying to install using envyng. When I did envyng the first time I restarted I sort of got a very distorted(block lines along the bottom third of the screen, and ubuntu logo in choppy negative color values and mirrored/ghosted 3-4 times). Nothing at all seems to get me video. 

The card is identified by linux as a Radeon X1300/X1550 Series. The Xorg log doesn't show any errors. Anyone have any idea where I should start?

---

### Post by linuxmagick on 2009-06-30
You said you upgraded.  I bet you were using the proprietary fglrx driver from AMD/ATI, right?  Unfortunately, AMD has recently retired many of its graphics cards and will no longer be providing driver updates like in the past.  

I just had the same problem with a mobility Radeon 9600 in my laptop.  The good news is that the open source drivers should work pretty well for you.  You'll need to remove any remnants of the proprietary driver and then install the open source driver.

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

---

### Post by sjv on 2009-06-30
Yeah, that's all of the stuff in the link I posted. I was using fglrx, but I still get nothing but a blank screen after doing that unfortunately.

---

### Post by linuxmagick on 2009-06-30
Sorry, I guess I missed the link in your first post.  We'll just chalk that one up to it being a long day.  If possible, it may help in identifying your issue if we can see a copy of your xorg.conf.

---

### Post by linuxmagick on 2009-06-30
Maybe also try:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

and then try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sjv on 2009-06-30
Doing that just gives me a super generic xorg.conf as attached. I have also attached the xorg log.

---

### Post by linuxmagick on 2009-06-30
Yeah, that's pretty much what my functioning xorg.conf looks like, so I doubt there's any problem there.  Didn't see anything obvious in the log either.  If I come across anything else to try, I'll let you know.  Hang in there.  Someone is bound to be able to point you in the right direction.

---

### Post by Melcar on 2009-06-30
Open up your xorg.conf and add the following line under the *Device* section:

```
Driver   "radeon"

```
Save the file and reboot.
Fglrx does not support your card anymore (9.3 was the last one, but that version doesn't work on Jaunty), so you have to move to the open source drivers.  The above change will load *radeon* which should provide 2D/3D acceleration for your card.

---

### Post by linuxmagick on 2009-06-30
I am anxious to see if this works for sjv.  If it does, then I'd have the question of why he would need that line and my 9600 works fine with the open source drivers with 3D support enabled and without that line in xorg.conf.  Unless it is somehow a difference in what is required for the two different model graphics cards.  

Oh well, either way I'm intrigued and can't wait to see what the result is.

---

### Post by sjv on 2009-06-30
Nope, no dice specifying the radeon driver. I attached the new Xorg log, but after doing a diff between the two, the only difference is that the first one did an autodetect and load of the radeon driver, and some various memory locations being different which you would expect.

Something else which may or may not be of interest, is that I can't switch to a terminal. Normally ctrl+alt+f1-6 will get a terminal as I'm sure you're aware, with f7 being the xorg display. I can drop to watching the loading details fly by instead of the loading splash, but where I believe it starts gdm, it takes me to the black screen. While at the black screen it will intermittently flicker to tty1 for a second or two, and then go back to the black screen.

---

### Post by sjv on 2009-07-01
I came across this this morning:

[http://jeffrasmussen.wordpress.com/2009/05/06/ubuntu-jaunty-jackalope-904-with-ati-x1300/](http://jeffrasmussen.wordpress.com/2009/05/06/ubuntu-jaunty-jackalope-904-with-ati-x1300/)

It got me the most progress so far. I specified the driver as radeonhd, which ubuntu didn't necessarily care for, but it did come up with a graphical display saying so, and then I was able to get in in a low resolution mode(1280x1024 I believe) mirrored on both of my displays. I tried fiddling with things from there, but couldn't get the resolution up, nor the display stretched across both monitors.

---

### Post by sjv on 2009-07-01
Building on the radeonhd thing, I googled around and through some forum posts, came across this: 

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

After compiling that driver I'm in business. Both monitors work as they're supposed to. The system is pretty slow though. I'm not sure if that's the redraw, or if it has to do with it being the first time the system has loaded up(trackerd which I killed, and other update stuff).  Hopefully the sluggishness will pass.

Thanks for the help.

---

