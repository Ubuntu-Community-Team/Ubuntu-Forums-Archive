---
title: "OK I broke it"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by xhero0 on 2007-09-09
OK I am running 7.04 gnome desktop. I HAD a ATI x550 pcie card, and I put in a nVidia 7600 pcie and now xserver blew up in my face.. I forgot about that when I installed the card...

Now the question:

Should I just try to reinstall on top of it? If so how?
Or
How do I get the nvidia driver in the system.

Other info:
I made a fat32 partition so I can get fins back and forth from windows to linux....

I am kinda a noob to linux....

Thanx ahead of time!

lates!

joe

---

### Post by Jimmy The Clown on 2007-09-09
You should be able to repair your system without too much trouble. First try this from a command line:

```
sudo dpkg-reconfigure xserver-xorg
```

That might be enough.
 Otherwise do this to manually set your video driver:

```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
sudo nano -w xorg.conf
```

This is making a copy of your current config as a back up and then opening it for editing in a text editor. Scroll down until you see a ' Section "Device" '. Under that will a line that says ' Driver "ati" ' or maybe some other driver. Change the driver to 'nv' this is the default open source Linux driver and should get you up and running for now. ctrl-o to save and ctrl-x to exit. Reboot.

Good luck!

-JTC

---

### Post by Straylit Me on 2007-09-09
Ooook. Your probably just going to need to tell xorg.conf to use the nvidia driver instead of the ati driver.

When you boot up and X Server fails you should get kicked back to terminal. Go on and login. Procede to run the following.

```
sudo nano /etc/X11/xorg.conf
```

Scroll down to "Section "Device" where it mentions your nvidia card. Change the driver to "nv".
Press CTRL+X, then Y, then Enter.

Procede to try: ```
startx
```

Hope this helps. Im not entirely sure if it will work due to im not sure if linux will automatically identify the new hardware without doing it manually which im not sure how to do from command line. If it identifies it automatically then changing the driver to "nv" will work. From there you can use Envy to install the "nvidia" driver. But lets get you fixed up first.

---

### Post by xhero0 on 2007-09-12
Thank both of you for your help!

I followed ya'll directions in addition I installed the latest nvidia driver... so far so god...

except my system is now booting slower in to linux.... I am gonna have to sit down and figure out why some day! :(

thanx again!

---

