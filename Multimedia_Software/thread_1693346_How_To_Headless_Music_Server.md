---
title: "How To: Headless Music Server"
date: 2011-02-22
forum: Multimedia Software
---

### Post by maxim99 on 2011-02-22
I had an old laptop sitting around collecting dust so I wanted to do something with it. This beauty is a 500Mhz Celeron and will do just fine to play some music and be low power, and not take up a lot of space. In trying to set it up and ran into a few issues and wanted to record my efforts for others to maybe learn from.

Here's what I used:
Dell Inspiron 3800
Dynex PCMCIA 10/100 NIC
Ubuntu 10.10 Live

**1. Install Ubuntu**
I installed using the CD-ROM release and the CD-ROM drive in the laptop.

**2. Install various services, and applications**
I installed smbfs, openssh, and vncserver for needed services. I also installed a couple of applications, vbetool (turn off the screen), and guayadeque(to play the music).
```
sudo apt-get install cifs-utils tightvncserver vbetool guayadeque
```

**3. Setup pulseaudio to be a systemwide daemon.**
The most frustrating aspect of this setup was pulseaudio. I started with x11vnc, but found that the performance was sub-par which wasn't a surprise given the hardware. I then tried vncserver and found that after logging in there was no sound device detected. I later found this be due to the way that pulseaudio links up with X and since Xtightvncserver doesn't start a "real" X server, pulseaudio never hooks up to it. The solution was to start pulseaudio in system-wide mode so that it was always available and didn't require an real X instance.

I found this article which described setting pulseaudio up in such a fashion:
[http://www.ubuntugeek.com/how-to-setup-mpd-with-pulseaudio-independent-on-x.html](http://www.ubuntugeek.com/how-to-setup-mpd-with-pulseaudio-independent-on-x.html)

The users and groups appeared to be setup already, so I didn't have to perform those steps.

Edit /etc/default/pulseaudio
```
sudo nano /etc/default/pulseaudio
```
Find these and set them like below.
```
PULSEAUDIO_SYSTEM_START=1
DISALLOW_MODULE_LOADING=0
```
This will tell the pulseaudio server to start with the --system switch, as well as disallow arbitrary loading of modules by users which is a security measure.

Edit /etc/pulse/system.pa
```
sudo nano /etc/pulse/system.pa
```
Find these and set them like below.
```
.ifexists module-hal-detect.so
load-module module-hal-detect
```
to
> .ifexists module-**udev**-detect.so
load-module module-**udev**-detect
I don't know if changing system.pa is really needed but I did it anyway.

**4. Disable X Server from starting automatically**
An easy way I found to do this is to update the grub boot options to include "text"
Edit /etc/default/grub
```
sudo nano /etc/default/grub
```
Modify the parameter to what is below.
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
Update grub **Important! Don't miss this step!**
```
sudo update-grub
```

**5. Set a vncserver password.**
Ensure that you're the user that the vncserver is going to run under (shouldn't be root). Set the vnc password which will get saved to a file in ~/.vnc/passwd
```
vncpasswd
```
Answer the questions when asked. Setting a "viewer" password is not needed.

**6. Setup vncserver, and turn off the monitor upon boot completion**
The easiest way I found was to modify the rc.local file which executes after the system is completely booted up.
```
sudo nano /etc/rc.local
```
Add the following lines with applicable changes *_before_* "exit 0"
*Note: "exit 0" tells the script to exit with an error level of 0, if you put the commands after exit 0 they will never be executed.*
```
su maxim -c "vncserver -geometry 1280x800"
vbetool dpms off
```
Change "maxim" to the user vncpasswd was run under, and change the geometry to the desired resolution.

**7. Reboot**
Reboot and cross your fingers. Hopefully grub isn't messed up.

You can reboot prior to the last step to make sure that everything is working in between, but shouldn't be needed. At this point you should be able to log in to it through VNC at port :1.

OpenSSH was installed in the beginning because I was working with the machine remotely and it was just easier to work out all the problems.

**Notes**
I found while restarting the pulseaudio service that every other time the service was started, no device would be found in the vncserver. I think this is a bug and will eventually be worked out. If you experience this behavior, be sure to "stop" and then "start" the pulseaudio service instead of "restart" the service. I found it to work every other time the service was started.
```
sudo /etc/init.d/pulseaudio stop;sudo /etc/init.d/pulseaudio start
```

---

