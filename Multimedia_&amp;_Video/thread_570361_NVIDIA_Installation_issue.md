---
title: "NVIDIA Installation issue"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by sjmiller85 on 2007-10-08
Well, I have searched far and through the forums, trying to see if anyone has come up with a legitimate solution to my problem, and have found none, so I apologize if I overlooked the obvious by asking for support in this.

First off, just for clarification, here are some numbers:

GFX card: NVIDIA Quadro FX 1400
OS: Ubuntu 6.10

Alright, got that out of the way, so now on to the messy stuff.  I am extremely new to Linux in general, but managed to get through most of my NVIDIA installation, until the end, when it displays the error
```
Warning: NVIDIA-Installer was forced to guess the x library path '/USR/LIB' and X Module path '/USR/LIB/XORG/Modules'; These paths were not queryable from the system.  If X fails to find the NVIDIA X Driver Module, please install the 'pkg-config' utility and the X.Org SDK/Development package for your distribution and re-install the driver
```
Sure enough, the installation will finish no problem, and the X server will fire right back up.  Now if I ever had to reboot, well then I get the error stating that the X server can't boot up, and I need to configure it so that it will.  I am forced to stay in text mode for the time being, unless I want to re-install my NVIDIA driver again while in text mode, and then it will fire back up when I type in the gdm start command, but only after I re-install my gfx card drivers.

I know that this problem has been encountered by many others, but I could not find a working solution to it, has anyone had any more luck than I with this issue?  Thank you for all your support!!!

---

### Post by RomeReactor on 2007-10-08
Hi. Have you tried getting the drivers for the Quadro card through the repositories (Synaptic, Apt-Get or Aptitude)? If not, to install the driver from the command line:
```
sudo apt-get install nvidia-glx-new
```
and
```
sudo nvidia-glx-config enable
```

---

### Post by sjmiller85 on 2007-10-08
No I haven't, but when I did, I typed:

```
sudo apt-get install nvidia-glx-new
```

the return is:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-new

```

any ideas?

---

### Post by RomeReactor on 2007-10-08
> **sjmiller85 said:**
> No I haven't, but when I did, I typed:

```
sudo apt-get install nvidia-glx-new
```

the return is:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-new

```

any ideas?

Sorry, it seems that package is not available for Edgy; try:
```
sudo apt-get install nvidia-glx
```

---

### Post by sjmiller85 on 2007-10-08
hmmmm...

Here is what I got:

```
scotty@scotty-laptop:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and:

```
scotty@scotty-laptop:~$ sudo nvidia-glx-config enable
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

Upon rebooting, I took a fine tooth comb over the X Server's status, when it asked me if I wanted to view it, and I did notice one thing that stood out.  It stated that the Nvidia's Kernel's version did not match the Nvidia driver version or something similar (I should have wrote it down, once again my memory fails me), and I was wondering if there was a way to configure it to match the correct ver. or a fix?

---

### Post by RomeReactor on 2007-10-08
I've seen that error when trying to install nvidia-glx after trying to install the .run driver from nvidia's site. Personally, I don't know how to fix that; sorry. Try doing a search for the error you get in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") section.

---

### Post by sjmiller85 on 2007-10-08
No worries bud, I appreciate your efforts.  I'll update this post if I find any fixes.  Thank you.

---

### Post by sjmiller85 on 2007-10-09
Here is what I have for somewhat of a solution:

Not exactly what I was going for, as I was hoping to find a fix for the specific problem for the feeling of self-accomplishment, but instead, I went with an alternative method of installing, which was using the Envy GUI.  I installed Envy, un-installed my drivers, installed them, reboot, and I received no error.  The only complaint I can give at this point is that every time I boot, it sticks me back at 1024x768 resolution.  Inconvenient? I guess.  Better than before?  Absolutely!  Anyone have any recommendations on how to go about fixing this problem?

---

### Post by RomeReactor on 2007-10-09
Glad you made it work!

For a possible fix to the resolution problem, try running nvidia-settings with administrator privileges:
```
gksudo nvidia-settings
```
choose your desired resolution, and see if it sticks between shutdowns/reboots.

---

### Post by sjmiller85 on 2007-10-09
worked like a charm, thank you!

---

