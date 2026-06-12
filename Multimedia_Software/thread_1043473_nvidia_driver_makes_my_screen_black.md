---
title: "nvidia driver makes my screen black"
date: 2009-01-18
forum: Multimedia Software
---

### Post by waynefwayne on 2009-01-18
To day is my second day with ubuntu every thing works
great until I install nvidia drivers then my screen goes 
black on reboot. I have reinstalled ubuntu three times 
to try each of the recommend versions and each time blackness.
Please help I was so gun ho for ubuntu that I deleted XP on install. I read that this was a problem wile doing google searches
but some how they are able to get the blackness to go away type some thing in and then there good.

---

### Post by Nov8tr on 2009-01-18
I have the same problem. Been 3 weeks trying to fix it.

---

### Post by Stieffers on 2009-01-18
Is the screen completely blank?  Are you recieving any on-screen text information?  Does it show the KDE/Gnome startup bar?  It may be that the configureation for your nVidia drivers is not correct, and as a result Xserver is unable to startup.

---

### Post by waynefwayne on 2009-01-18
there is a small line at the top runing left to right 4 pixels wide
I can see my mouse move in it. but does nothing

---

### Post by Stieffers on 2009-01-18
Try hitting **Ctrl+Alt+Backspace**.  This will terminate Xserver, if it is running.  Next hit **Ctrl+Alt+F1**.  This will bring up a terminal window where you can enter commands.  Here, you'll want to install nvidia-xconfig.  It may already be installed but just to make sure...

```
sudo apt-get install nvidia-xconfig
```

Next run it, using the **nvidia-xconfig** command in console.  Now try restarting KDE/Gnome.  Using the following command depending on what desktop you're running.

Gnome:
```
sudo /etc/init.d/gdm restart
```

KDE:
```
sudo /etc/init.d/kdm restart
```

If the desktop sucessfully starts, than congrats, problem solved.  However, if the screen flashes a few times and dumps you right back to the terminal, then the configuration file wasn't your problem.

Run the following command to check if Xserver outputs any errors or warnings.

```
sudo /etc/X11/X
```

If this runs sucessfully, you will now be presented with an "X" as your mouse icon, and a crosshatched gray background.  This means that Xserver is running fine.  Hit **Ctrl+Alt+Backspace** to get out of it.  At this point, the only advice I can give you is to download Envy, run it, and then uninstall your nVidia driver.

```
sudo apt-get install envyng-core
sudo envyng -t
```

---

### Post by waynefwayne on 2009-01-18
I am trying this now I reinstalled ubuntu again should
I do this before installing the drivers?

---

### Post by waynefwayne on 2009-01-18
how would i do this before installing the drivers?

---

### Post by solitaire on 2009-01-18
Do you still hear the start up sounds when the screen is blank?

if so their is a simple fix:

Install the Nvidia drivers as normal usingh EnvyNG or the Nvidia installer and reboot.
When the screen is blank change to tty1
and stop the GDM:
```

sudo /etc/init.d/gdm stop

```Then edit the "xorg.conf" file
```

sudo nano /etc/X11/xorg.conf

```Find the "devices" section and add in the following to the end
```

    Option       "UseDisplayDevice"    "DFP"
    Option       "AddARGBGLXVisuals"    "true"

```then start GDM again
```

sudo /etc/init.d/gdm start

```You should now see the Login screen.

For some reason the Nvidia drivers default to looking for the VGA output instead of the DFP screen. It's annoying and i hope their is a fix to the Nvidia drivers soon!

---

### Post by waynefwayne on 2009-01-18
what is tt1 also after pressing ctrl alt f1 my login name 
and password are not excepted. it lets me type in my name
but when typing my password the curser doesn't move

---

### Post by solitaire on 2009-01-18
> **waynefwayne said:**
> what is tt1 also after pressing ctrl alt f1 my login name 
and password are not excepted. it lets me type in my name
but when typing my password the curser doesn't move

Ctrl+alt+f1 is tty1 

Your username will show up when typed but passwords do not show when typed.
Just make sure you type your username and password in as normal.

---

### Post by waynefwayne on 2009-01-18
I did that I even reinstalled ubuntu and same problem

---

### Post by waynefwayne on 2009-01-18
I still get nothing

---

### Post by Stieffers on 2009-01-19
You should get the default Open-source nVidia drivers when reinstalling Ubuntu.

---

