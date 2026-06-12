---
title: "Edgy and Nvidia driver problems"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by mageus on 2006-11-03
Fresh install, can't get Nvidia drivers to work.  Here's my system:

MB: Biostar TForce 6100 (NForce 6100 chipset)
  onboard video disabled
CPU: Athlon 64 3000
RAM: 1GB
Vid: eVGA GeForce 7600GT
everything stock.

Here's what I tried:
- all software updated with apt-get
I used the Ubuntu HowTo for Edgy-
- nvidia-glx installation via apt-get ('Method 1')
- nvidia x86_64 drivers from website (1.0-8776)
- used both nv and nvidia setting in xorg.conf
- tried dpkg-reconfigure
- used lspci to verify that the correct slot was being used
- checked that linux-generic, linux-headers, linux-restricted-modules, xserver-xorg packages installed

When I install the nvidia-glx package, when it loads the xserver it gives an error that it failed.  The log lists something like:
"No matching device section for instance (BusID PCI:3:0:0)
Fatal server error: no screens found"

When I install the 8776 drivers from the website, when it loads the xserver the monitor turns off.  I tried the resolution and refresh rate fix but it didn't work.

I've scoured the forums and tried the various ideas, but without help.

Any ideas and help would be appreciated.

I've attached the xorg.conf for the 8776 drivers for reference.

---

### Post by mageus on 2006-11-03
Sorry, posted wrong xorg.conf

---

### Post by mageus on 2006-11-03
Just noticed something:

- Copied my old xorg.conf (VESA).
- changed VESA to 'nvidia' in the display section
- started xserver - blank screen / monitor turns off

- changed 'nvidia' to 'nv' -> Works!

So, the xorg.conf that nvidia-config creates doesn't work, even when changing 'nvidia' to 'nv'.
But, the default xorg.conf does work when changing to 'nv'.

Is there a benefit to using the 'nvidia' driver vs 'nv'?  I assume the nv is an older, safer driver but without certain features.

---

### Post by tommcd on 2006-11-03
Do you get the nvidia splash screen on bootup? You should if the nvidia driver is working. What is the output of glxinfo? The beginning should look something like this if the nvidia driver is working:
note the direct rendering part:

tom@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

---

### Post by tseliot on 2006-11-03
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by mageus on 2006-11-03
tseliot, thanx a bunch.

I figured out the main problem.  I have 3 monitor outputs, MB (disabled) and 2 DVI ports on the 7600GT, one going to Dell 2005FPW DFP and one going (via VGA) to my plasma TV.
I disconnected the VGA cable to the plasma and everything (almost) works on the 2005FPW. (must have been displaying on the TV & I didn't notice)

One more problem - resolutions:

- It won't do 1650x1080
- 1280x800 is stretched to 4:3 to the monitor.  xserver is displaying 1280x800 pixels but the monitor is seeing a 1280x1024 hard resolution.  So, xserver is stretching the 1280x800 to 1280x1024 (dithered) and sending that to the monitor.

From the xorg.log file it's detected my monitor correctly and even detecting the proper res/sync data in the modepool, but later on saying 
"No valid modes for "1650x1080"; removing."  Don't know why it's stretching the 1280x800.

I've broken up the log file into 3 segments, since the forum won't allow large uploads.

Much TIA.

---

### Post by mageus on 2006-11-03
My stupidity.

It's 1680x1050 (WSXGA), not 1650x1080.  Fixed xorg.conf and it works fine.  Thanx for all the help, everyone.

---

### Post by AlReece45 on 2006-11-03
My guess is that the nvidia driver does not support that graphics card yet. (It did that with my computer). I would personally recommend trying the beta drivers, they have been quite stable with me. But since turbo cache doesn't work, if you want that feature, the beta version might not be for you.

Like many others, I am pointing you to Step 2 of this [useful post]("http://www.ubuntuforums.org/showpost.php?p=1536245&postcount=1") if you want to install the beta drivers.

---

### Post by mageus on 2006-11-04
AlReece45, please see my above post.  Everything's working fine now.  Will test out the dual-head setup later.

Of course, I went and screwed up Gnome by trying to install XGL/Compiz.  Need to clean up that mess . . .

---

