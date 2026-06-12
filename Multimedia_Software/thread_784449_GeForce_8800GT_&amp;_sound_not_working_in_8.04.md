---
title: "GeForce 8800GT &amp; sound not working in 8.04"
date: 2008-05-06
forum: Multimedia Software
---

### Post by phearsome on 2008-05-06
Hello.
I recently got a new computer, and installed Windows XP and Ubuntu 8.04 Hardy Heron. 
Well, everything works fine in Windows, but in Ubuntu neither my sound or my graphics card works.

I have tried using Envy for the graphics driver. It appears to install without any problems. 
However, it doesn't appear in Applications, and when I try to run it through the terminal it says:
```
 /usr/bin/envyng: line 11: cd: /usr/share/envy: No such file or directory
Traceback (most recent call last):
  File "/usr/share/envyng-gtk/envynggtk.py", line 736, in <module>
    os.chdir('/usr/share/envy')
OSError: [Errno 2] No such file or directory: '/usr/share/envy'

```

When I try to install the drivers manually, it says I need to shut down X. How do I do that?

My sound card is integrated on my motherboard, MSI P35 NEO-F.

My hardware setup is:
MSI P35 NEO-F
Intel Core 2 Duo E6750 2.66GHz 
GeForce 8800GT 512MB 
2GB DDR2 800MHz RAM.

Grateful for any help, thanks in advance. :)

EDIT: I got the sound working, but I'm only getting sound on my left speaker.

---

### Post by Frankels on 2008-05-06
What worked for me was to go to system>preferences>sound> and change things to alsa, i have hda intel(alsa mixer) in default mixer tracks. (thats just the sound part...hope it helps someone)

---

### Post by TUOggy on 2008-05-06
Try doing a manual install.
Download the newest NVIDIA driver from their website (I generally just save it to the Desktop).

Stop X: Press Control-Alt-F1

Login.

Run:

```

sudo /etc/init.d/gdm stop

```

Go to the desktop

```

cd Desktop

```

lets install the nvidia driver from here:

```

sudo sh NVIDIA-Linux-x86-###.##.##-pkg1.run

```

(If you don't know the full name of the linux driver file, then a simple "ls" will show that)

The installer should start, and walk you through the rest.

whenever you are done, just type "startx" and it should reload gnome.

Hope this helps.

---

### Post by Gamehunter on 2008-05-07
Same problem here. Looking for solutions too! Please let me know if you mange to find one. I shall do the same!



**Processor:** Intel Core 2 Duo E8400 3Ghz
**Motherboard:** Intel DP35DP Original Motherboard [No onboard VGA available]
**RAM: **2GB
**Graphics Card:** MSI nVIDIA GeFOrce 8800 GT 512MB PCI-Express
**Sound:** On Board (SigmaTel Codec)
**OS:** Ubuntu 8.04 Hardy Heron & Windows XP SP2
**Monitor:** CRT 17" Samsung

Issues: Graphics card is not recognized by Ubuntu. Enabling the nvidia "new" driver causes the screen to revert to 640x480.

Xorg.conf detects it as generic Nvidia graphics card.


"PCI device failed to allocate mem"----This message is seen if I edit Xorg.conf to correct screen resolution values.
This is also seen if I try to run the Ubuntu 7.10 Live CD, though it is not seen with Ubuntu 8.04 Live CD.

"sudo dpkg-reconfigure xserver-xorg" does not configure or detect card properly.
There are no options to set screen resolution and refresh rates or horizontal and vertical refresh frequencies of the monitor while running the above command in Hardy Heron.



Manually editing xorg.conf crashes X on restart with the message "PCI device failed to allocate mem". "No screens found"

Repairing Xorg.conf in the recovery console allows me to restart X but again it has the same low resolution of 640x480.

3D acceleration is not properly working.



I had no issues on a previous system: Pentium 4 1.7GHz, Intel 845G Motherboard with GeForce 5700 AGP card running Ubuntu 7.10.

It used to work magnificently. ****

---

### Post by phearsome on 2008-05-07
I got the graphics drivers working, a bit at least. Thanks alot!
Though the highest resolution I can get is 1024x768, and I would like to make my resolution 1280x1024. Is that a possibility?

There is still no sound on my right speaker. Works fine in windows, so it's not the speakers fault.

I bet I just changed some setting somewhere, that's how I am, changing settings by mistakes and whatnot. 

Thanks in advance! (again)

EDIT: Also, can I change the brightness by software? Such as with Rivatuner in Windows XP. My screen is a little dark.

---

### Post by pedro_orange on 2008-05-07
What driver do you use for the sound?

And what sound are we talking about? Are we talking about mp3s and such?
It may be possible you do not have the codecs that require you to play these files correctly.

I use the alsa-oss package as my sound driver.

Also; you may wish to do the following to download dvd codecs/mp3 codecs/ flash player etc..

```
sudo apt-get install ubuntu-restricted-extras
```

If you're only getting sound in one speaker:

You could try running:

```
alsamixer
```

And seeing if the volumes are turned up correctly :)
Other than that; I suggest checking your connections

---

### Post by phearsome on 2008-05-07
Holy ****, I am retarded.
I thought there were only the visible controls in alsamixer, and now I realized it scrolls. Well yeah, the sound is fixed. Thanks alot!

---

### Post by phearsome on 2008-05-08
Okay, now when I started up the computer again, the drivers are not working. I got some error messages about... something, when I started it up, some low graphics mode stuff. What?

---

