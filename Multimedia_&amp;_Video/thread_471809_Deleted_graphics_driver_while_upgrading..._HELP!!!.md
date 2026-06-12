---
title: "Deleted graphics driver while upgrading... HELP!!!"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by 213374U on 2007-06-12
Okay, last night I was trying to upgrade from the standard installed version of Compiz to the new Compiz.git following the instructions on the compiz website. During one portion of the install you have to alter the graphics card driver information.... forgot that I'm using an ATI Radeon X1600 Pro :hammer: Anyway, finished the upgrade and it didn't work, of course, so I began to try and undo what I had done. Nothing was working so I figured I'd start with a fresh install of Feisty. I inserted my disc and tried to reboot and when I did, it booted up with errors and launched the X Server (Terminal only). Here are the errors it listed before launching the terminal:

```
Log File: "/var/log/Xorg.0.log", Time: Mon Jun 11 22:10:37
Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
Undefined Device "Generic Video Card" referenced by Screen "Default Screen"

(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
screens found

(WW) xf86C loseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86C loseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
```

Can someone please walk me through getting this thing back up and running (VERY STUPID STYLE PLEASE). Computer is down till then and the wife is gonna get pissed if she can't check her MySpace :p

---

### Post by osxdude on 2007-06-12
Use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Make sure you download the stable version.

(What's her myspace address? ;) )

---

### Post by 213374U on 2007-06-12
Okay, downloaded envy to a thumb drive.

Now, how do I go about accessing it in X Server and installing the .deb file?

Please make instructions as stupid as possible, pretend I'm a moron ;)

---

### Post by rockingmtranch on 2007-06-12
Did you try: sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by 213374U on 2007-06-13
haven't but I will

---

### Post by rockingmtranch on 2007-06-13
That should get your driver reinstalled then you can go from there for upgrades or whatever.

---

### Post by 213374U on 2007-06-13
Okay, tried the above. My card is not supported under the above command. I have an ATI Radeon X1600 Pro. Highest the pro series went in the list was like an X950. So that was shot down.

Can anyone walk me through mounting my thumb drive and installing Envy in X Server? I think it's going to be my best bet.... unless of course anyone has any better ideas.

---

### Post by dabl on 2007-06-13
If you can log in to your system in text mode, probably the best approach to getting it back together is (a) get a GUI, and then (b) use Envy to re-install the driver you need. So, here's how to do it:

```
sudo dpkg-reconfigure xserver-xorg
```

This will start the xserver configuration script.  On the first screen, answer "NO" to autodetect, then on the second screen choose "VESA" display.  From there on, you can accept the defaults, unless you are aware of a non-standard item on your hardware.  When you get to the "monitor" section, choose only one of the display resolutions that you can be comfortable with for a little while, like 1024 x 768, and then choose a refresh range that your monitor or LCD will run with, and finish the script.  When you finish, it will dump you back to the prompt.

Now you can enter ```
startx
``` and the xserver should come up with a tolerable GUI for you to continue with.

So, now you can go to "Places" and browse to your thumb drive, and copy that Envy download file over to your /home directory, to the "Desktop" or "Downloads" or wherever you put such things.  Then follow the instructions on the Envy web site to install it and run it, and it should take care of installing your ATI driver.

HTH :D

---

### Post by 213374U on 2007-06-13
Man, I hope this works. I'll update as soon as I can but thanks to everyone so far who has lent a helping hand. This is why Linux rox!!!

---

### Post by 213374U on 2007-06-13
Okay, tried the above and my guess is that I can't get the settings correct and the defaults aren't working.... And ATI on Ubuntu sucks. Anyway, I am able to get a GUI up and running but its so screwy looking I can't make anything out. 

Is there a way to do this strictly in terminal since that seems to be all that is going to work for me?

---

### Post by 213374U on 2007-06-13
okay, I got it to run in Failsafe GNOME and was able to install and run Envy. Only problem now, the screen (workspace) is larger than my monitor so that when I run Envy, I'm able to select "install ATI driver" but can't get to the execute button. 

How do I resize the workspace so that it fits inside my screen?

---

### Post by rockingmtranch on 2007-06-13
Dumb question maybe but have you tried apt-get update? And, Envy can be run from the prompt screen. I'm looking for those commands.....around here somewhere...dangit.....

---

### Post by 213374U on 2007-06-13
I got ENVY to work and was able to install the ATI Driver.... I feel like a moron <alt><ctrl>grab window . But for some reason this still isn't solving my problem. It's still choppy (can't make anything out on the monitor) unless I load GNOME Failsafe session.

---

### Post by rockingmtranch on 2007-06-13
I don't know. Those symptoms could very well be hardware related.

---

### Post by 213374U on 2007-06-13
Yeah, I can't figure out what the hell is going on. I just need to format and re-install. Trying to get the iso image for the alternate install cd for feisty burned so I can do a text install but for some reason, my desktop just won't boot into anything but recovery mode. From there I can run 

```
sudo dpkg-reconfigure xserver-xorg
```

set everything up and then open GNOME Failsafe. But even failsafe isn't running properly, workspace is larger than my monitor!!!

If anyone has any suggestions please throw em out there. I'm just toying with it right now till I can find something that works.

---

### Post by rockingmtranch on 2007-06-13
Can't hurt it now so try: sudo apt-get dist-upgrade -- fix-missing

---

### Post by 213374U on 2007-06-14
Thanks for all the help. I finally dumped and re-installed... back up and running.

---

