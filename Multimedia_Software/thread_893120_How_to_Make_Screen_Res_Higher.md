---
title: "How to Make Screen Res Higher?"
date: 2008-08-17
forum: Multimedia Software
---

### Post by gillilandboy on 2008-08-17
I just installed Ubuntu on my HP and I am trying to figure out how to make my screen res 1440x900. Right now it only lets me set it as 800x600. I am very new to Linux so please don't hate on me :)


Thanks.

---

### Post by tuxxy on 2008-08-17
Is that resolution what you would expect in windows? did you install the video drivers? 

whats your video card model?

---

### Post by nkri on 2008-08-17
First off, welcome to Ubuntu!

To change the resolution, open up a terminal (Applications>Accessories>Terminal) and type
```
gksu displayconfig-gtk
```

It will ask for your password.  Type this in and hit enter.

In the first screen that pops up, there is a box for resolution; click it and select 1440x900.

Click OK.  I believe at this point you need to either reboot the computer or restart X (Ctrl+Alt+Backspace).

Good luck!
-nkri

---

### Post by gillilandboy on 2008-08-17
In Windows I always had 1440x900. Like I said I am very new to Linux and I have no idea how to install the video drivers. I have an Nvidia GeForce 7100.

---

### Post by overdrank on 2008-08-17
Hi and welcome, moved :)

---

### Post by gillilandboy on 2008-08-18
I downloaded the driver from the NVIDIA site and I was reading on how to install it and it says "Type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install the driver". I am guessing type that in to terminal? When I typed it in to terminal it said that it could not open the file so I don't know what else to try. I would really like to thank everyone for their help the Linux people are very nice :D

---

### Post by overdrank on 2008-08-18
> **gillilandboy said:**
> I downloaded the driver from the NVIDIA site and I was reading on how to install it and it says "Type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install the driver". I am guessing type that in to terminal? When I typed it in to terminal it said that it could not open the file so I don't know what else to try. I would really like to thank everyone for their help the Linux people are very nice :D

Ok have you tried the drivers located under system, administration, hardware drivers? 
This should work then you can install the nvidia-settings via synaptic manager and use them to help with resolution. Use the command by the alt,F2 keys and enter ```
gksu nvidia-settings
```

---

### Post by nkri on 2008-08-18
Yes, you're right that you have to type it into the terminal, but first you have to change the working directory in the terminal.  To do this, type
```
cd *directory in which you put the driver*
```

So for example, if you want to use a file on the desktop, it would be
```
cd Desktop
```

Then you can run the sh command.

Good luck!
-nkri

---

### Post by overdrank on 2008-08-18
> **nkri said:**
> Yes, you're right that you have to type it into the terminal, but first you have to change the working directory in the terminal.  To do this, type
```
cd *directory in which you put the driver*
```

So for example, if you want to use a file on the desktop, it would be
```
cd Desktop
```

Then you can run the sh command.

Good luck!
-nkri

Also the op will have to stop x by using the ctrl, alt, F1 keys and then using this command
```
sudo /etc/init.d/gdm stop
```
and cd to the file location then run the command 
```
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
```

This is why I suggested the hardware drivers.

---

### Post by gillilandboy on 2008-08-18
overdrank I did what you said and everything was going ok and then it says "No precomiled kernel interface was found to match your kernal; would you like the installer to attemt to download a kernel interface for your kernel from the NVIDIA ftp site?" I said yes then it said "No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel" I clicked ok and then it said "ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package." Clicked ok again and it said "ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com" Clicked ok AGAIN and then it just took me back to the command line.

---

### Post by overdrank on 2008-08-18
> **gillilandboy said:**
> overdrank I did what you said and everything was going ok and then it says "No precomiled kernel interface was found to match your kernal; would you like the installer to attemt to download a kernel interface for your kernel from the NVIDIA ftp site?" I said yes then it said "No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel" I clicked ok and then it said "ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package." Clicked ok again and it said "ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com" Clicked ok AGAIN and then it just took me back to the command line.

Have you tried the hardware drivers located under system, administration?

---

### Post by gillilandboy on 2008-08-18
Did that and is now enabled and in use but it still won't let me change the size of my screen res.

---

### Post by overdrank on 2008-08-18
> **gillilandboy said:**
> Did that and is now enabled and in use but it still won't let me change the size of my screen res.

Ok and have you tried using the nvidia-settings mentioned previously?

---

