---
title: "How to get your GUI back. Open video drivers do the best job"
date: 2010-02-15
forum: Multimedia Software
---

### Post by gwm on 2010-02-15
Hi,
My Karmic Ubuntu kept hanging. I didn't know about Ctl-Alt-Prt Scrn-R, E, I, S, U, B (mnemonic = Reboot Even If System Utterly Broken) and so had to press the reset button several times a day. Eventually I traced it to the **Screensaver: AntSpotlight**. Also, I can't use any **visual effects**. Except at low resolution, anything other than a setting of **None** gives me a black screen.

Earlier releases of Ubuntu used to offer a proprietary driver for this card but not any more. I have an ATI Radeon 9200 Pro card. It turns out that the newer ATI Linux drivers do not support it as far as I can see. In fact when I tried them, all I could see was nothing, zero, a black screen of death.

It has taken me the best part of a day and all night to get my screen back. Thank you to whoever it was in one of the forum threads, that referred us to **Envy** (available in the repositories). I used **EnvyNG** to finally got rid of enough of the Catalyst driver and put back enough of the open driver for me to at least get my GUI back.

I then followed the advice in the Ubuntu documentation for removing all video drivers and reinstalling the open driver. This still only gave me an unknown monitor with a refresh rate of zero and a suboptimal screen resolution. The final trick was to go into **/etc/X11** and **rename all the xorg.conf** files that I could find - three of them - to zxorg.conf files.

After the reboot, the open driver recognized the monitor as a Dell 20" and gave me back all the screen resolutions. So now I have my screen back but still no visual effects and I'll have to somehow selectively remove whatever screen savers use those special effects, crashing the system.

---

### Post by Yellow Pasque on 2010-02-15
You should have desktop effects. Make sure you've followed all of the commands in this section: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

If you reboot and still can't get effects, post output of:
```
compiz --replace
```

---

### Post by gwm on 2010-02-17
Hi Temujin,
I have done that and captured the output from each command if that will help.
Here is the requested output
```

**Compiz --replace**
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

# after this command, the windows on the screen went blank, black.
# Except for the Terminal window which remained visible.
# At screen resolution 1152 x 864 screen came back, allowing all special effects.
# Only working possibility for full resolution (1600 x 1200) is **Visual Effects = None**
# I've tried to find xgl and glx 1.3 in Synaptic - not sure what to install.


```

---

