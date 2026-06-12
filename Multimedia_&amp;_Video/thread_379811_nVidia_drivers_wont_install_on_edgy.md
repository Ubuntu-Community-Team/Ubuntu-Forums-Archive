---
title: "nVidia drivers wont install on edgy"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by BlackCow on 2007-03-08
I had this same problem on drapper, I upgraded to edgy and still no luck. I'm installing the nVida drivers using this tutorial:
[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers]("http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers")

I was able to disable the gdm Xserver but when I got to the installer it says something to the effect of, 
"Kernel not found, would you like to see if we can find it on an ftp for you"
I hit OK it says,
"We were unable to find it, would you like to rebuild (or recompile I can't remember)"
I hit OK it says,
"Unable to rebuild, installation unsuccessful"

So um, what the heck is that about? :confused:

---

### Post by catanzag on 2007-03-09
Do you really need latest release from nvidia site? Otherwise, you could follow [this]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy") guide or install the latest driver (not official) from [http://www.albertomilone.com/driver.html](http://www.albertomilone.com/driver.html)

regards

---

### Post by david_2001 on 2007-03-09
> **BlackCow said:**
> I had this same problem on drapper, I upgraded to edgy and still no luck. I'm installing the nVida drivers using this tutorial:
[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers]("http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers")

I was able to disable the gdm Xserver but when I got to the installer it says something to the effect of, 
"Kernel not found, would you like to see if we can find it on an ftp for you"
I hit OK it says,
"We were unable to find it, would you like to rebuild (or recompile I can't remember)"
I hit OK it says,
"Unable to rebuild, installation unsuccessful"

So um, what the heck is that about? :confused:
I just took a look at that tutorial.  The one vital step that I couldn't find was installation of the headers or full source for the running Linux kernel.  The nvidia installer will not be able to compile the nvidia kernel module if the kernel headers/source are missing and the result will be the error that you quote.

---

### Post by BlackCow on 2007-03-09
> **david_2001 said:**
> I just took a look at that tutorial.  The one vital step that I couldn't find was installation of the headers or full source for the running Linux kernel.  The nvidia installer will not be able to compile the nvidia kernel module if the kernel headers/source are missing and the result will be the error that you quote.

So um, how do I install the "headers" or "full source"? :confused:  A little explanation would be good to. Ive googled around and I haven't been able to find any tutorial that can help. Other people don't seem to be having my problem.

Edit: I tried using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") and now im getting the error, "Error: Dependency is not satisfiable: module-assistant"

Why does Linux hate me :-P

---

### Post by Funk Soul Brother on 2007-03-09
Cow dude,

I followed the instructions from Alberto Milne to install Envy. That went ok, but then in the applications menu, the nVidia application won't launch. Bummer.

So I had to go and edit the xorg.conf file. I bungled it so I had to use 'safe' mode to boot my machine as my xserver was cooked. Me and Vi battled it out for a bit. I managed to change the driver from 'nVidia' back to 'nv' and I also set the horiz and vertical refresh rates per the monitor specs (NEC LCD1765).

I restarted the machino and kerpow! I now had full resolution at 65Hz - but it is still not running off the nVidia driver.

I'm using an AGP GeForce 6200LE. Hope the above helps. Kindoff a Linux dummy, here.

---

### Post by BlackCow on 2007-03-10
Well I tried to install the headers and it looked like it worked. It took me like a million trys to stop gdm but I finally did. When I tryed to run the installer is still gave me **** about the kernel. Is this not a common problem? I feel like im the only one having this problem. Nothing is going right, I tried to set the resolution to a wide screen and even though its in the list it dosnt work right and so I was hoping the nVidia drivers would fix it. Ubuntu is making me want to drown puppys right now. :mad:

---

### Post by david_2001 on 2007-03-11
Writing a proper tutorial would mean producing a complete guide to X configuration, quite simply because an attempt to install a third-party graphics driver without first having a working setup using the drivers that come with X is going to end in tears.

The first question that you really need to ask yourself is why you want to install the nvidia driver from nvidia.com and not use the ready made packages from the Ubuntu repositories.  They may not be absolutely the latest version but they are more likely to work first time AND they will not need to be reinstalled by hand every time the kernel gets updated, unlike the driver from nvidia.com.  (Did you read any of the avalanche of messages about nvidia drivers not working the last time that the kernel package was updated?)

Anyway, going back to that [COLOR="SandyBrown"][howto]("http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers")[/COLOR], try the following modification to step 2 to get the correct kernel headers installed (note the deliberate use of backquotes around `uname -r`): 
```
 sudo apt-get install build-essential pkg-config xserver-xorg-dev linux-headers-`uname -r`
```
I would also recommend studying the [COLOR="SandyBrown"][README]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html")[/COLOR] that nvidia produces for its linux driver, especially the section "Editing the configuration file by hand".

---

### Post by tseliot on 2007-03-11
> **david_2001 said:**
> I just took a look at that tutorial.  The one vital step that I couldn't find was installation of the headers or full source for the running Linux kernel.  The nvidia installer will not be able to compile the nvidia kernel module if the kernel headers/source are missing and the result will be the error that you quote.

There is always this guide:
[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)

---

### Post by tseliot on 2007-03-11
> **BlackCow said:**
> So um, how do I install the "headers" or "full source"? :confused:  A little explanation would be good to. Ive googled around and I haven't been able to find any tutorial that can help. Other people don't seem to be having my problem.

Edit: I tried using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") and now im getting the error, "Error: Dependency is not satisfiable: module-assistant"

Why does Linux hate me :-P

Enable the Universe repository

---

### Post by tseliot on 2007-03-11
> **Funk Soul Brother said:**
> Cow dude,

I followed the instructions from Alberto Milne to install Envy. That went ok, but then in the applications menu, the nVidia application won't launch. Bummer.

So I had to go and edit the xorg.conf file. I bungled it so I had to use 'safe' mode to boot my machine as my xserver was cooked. Me and Vi battled it out for a bit. I managed to change the driver from 'nVidia' back to 'nv' and I also set the horiz and vertical refresh rates per the monitor specs (NEC LCD1765).

I restarted the machino and kerpow! I now had full resolution at 65Hz - but it is still not running off the nVidia driver.

I'm using an AGP GeForce 6200LE. Hope the above helps. Kindoff a Linux dummy, here.

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

