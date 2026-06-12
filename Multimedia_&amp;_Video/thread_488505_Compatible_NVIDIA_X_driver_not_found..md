---
title: "Compatible NVIDIA X driver not found."
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by Seine on 2007-06-30
Hello

I'm in Lynx and having a not so good time. I just typed a lot of information and lost it all because I dared to press left-arrow. Ah the joys of HTTP before Mosiac...

Currently I cannot get a GDM session at all. I am looking for some assistance to debug this.

Here are some things I have tried.

1: purge nvidia & restricted modules and reinstall (from a thread called "nvidia nightmare"). This had no effect.
2: recreate xorg.conf. this generated heaps of new errors, so I restored the nvidia version.
3: changed driver in xorg.conf to "nv" or even "vesa" (not sure what that is). No effect.

The errors in my xorg log are

1: Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
2: xf86OpenSerial: Cannot open device /dev/input/wacom (No such file or directory).
The latter appears three times. I assume it is innocuous.

Please, any help will be appreciated!

Thanks
Jem

---

### Post by Seine on 2007-06-30
I have since used Envy to install a driver. This was a marginal failure. I was able to get GDM to work, but everything renders extremely slow and there are plenty of artefacts on the screen, such as scrambled images and chunks of black rectangles left behind by the movement of windows. I have used Envy to remove the driver again and I'm back where I started, sort of. Can anyone help me to debug this? I really don't understand the architecture in the linux video world at all.

---

### Post by RomeReactor on 2007-06-30
Hi. This might be a silly question, but do you have Breyl or Compiz (System-->Preferences-->Desktop Effects) active while doing all of this? In any case, have you tried running **sudo dpkg-reconfigure -phigh xserver-xorg** from the command line? Also, are you sure your card is functioning properly (if you dual-boot, does it work correctly on windows?)

---

### Post by Seine on 2007-06-30
Hi, all good questions:

**Do you have Breyl or Compiz (System-->Preferences-->Desktop Effects) active while doing all of this?**
It is installed, but does not work and so my desktop mgr is set to Metacity.

** In any case, have you tried running sudo dpkg-reconfigure -phigh xserver-xorg from the command line?**
Yes, it made no difference. I even tried running it with a zero-byte xorg.conf in place but that was disasterous. Heaps of new errors resulted so I rolled-back

**Also, are you sure your card is functioning properly (if you dual-boot, does it work correctly on windows?)**
Card is OK. I am writing to you from the evil realm at this very moment

---

### Post by RomeReactor on 2007-06-30
Hmmm... what video card do you have? The problem could stem from using the wrong set of drivers (e.g., if you have a TNT Riva 64 and using nvidia-glx-new). Also, is [this]("http://ubuntuforums.org/showthread.php?t=375627") the "Nvidia Nightmare" thread you mentioned?

---

### Post by Seine on 2007-06-30
[This is the post I followed instructions of]("http://ubuntuforums.org/showpost.php?p=2897131&postcount=6"). 

My card is a GeForce GO 7400.

EDIT: It's build into my HP Pavillion dv5000 laptop, if that makes a difference.

Thanks
Jeremy

---

### Post by dfreer on 2007-06-30
hmmm I have this same card, on an hp dv6000t.
From a clean install, restricted driver manager always works for me to install the driver on 32-bit. also, ```
sudo apt-get install nvidia-glx-new
``` works, although you need to manually change the /etc/X11/xorg.conf driver from "nv" to "nvidia". You can try either of these methods, although the restricted drivers manager makes things a lot eaiser.
You may run into problems getting these methods to work now your machine is broken, however. I'll try to help as much as possible, since our machines are pretty similiar.

The instructions in that post you linked to are not needed in feisty. also, it is pretty much always better to use the provided .debs of the nvidia driver than to use the ones downloaded from nvidia's site.

EDIT: also, did you follow the first set of instructions, or the second (the second involved compiling the drivers)?

---

### Post by Seine on 2007-07-01
Given Rome's question about Beryl I thought I'd try removing that. I removed (and purged, because it feels good) Beryl and Emerald. Then I installed nvidia-glx-new and ran nvidia-xconfig. All is well again.

Now, do I dare trying to install Beryl again?

Thanks to all who helped.

---

### Post by dfreer on 2007-07-01
beryl works fine for me. you'll need to add a line to xorg.conf ```
Option "AddARGBGLXVisuals" "True"
```, or run the 
```
nvidia-xconfig --add-argb-glx-visuals 
```

---

### Post by Seine on 2007-07-02
I installed compiz fusion and it works flawlessly. It's better than compiz or beryl alone ever were ... at least for me. Everything is fine again (I'm just awaiting the next kernel or nvidia driver update. Then the fun will start again!)

---

### Post by RomeReactor on 2007-07-02
Glad to hear you got it working!
Myself, I just switch Desktop Effects on and off every couple of days, change between my custom clearlooks-based theme and pure Ubuntu, change between Firefox, Opera and Navigator every now and then also. Compiz and Beryl are nice (they *do* provide some added functionality), but sometimes I just want a very breezy system (no pun intended :D ).

---

