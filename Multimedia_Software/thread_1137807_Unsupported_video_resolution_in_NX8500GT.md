---
title: "Unsupported video resolution in NX8500GT"
date: 2009-04-25
forum: Multimedia Software
---

### Post by jdash1 on 2009-04-25
specs
msi nx85000 td512E - graphics card
22" audiosonic lcd.
ubuntu 9.04 hardy



I can't install compiz and use my video card

everytime i go to system>admin>hardware then select the any of the 2 available restricted drivers (ver 180 and 173) and restart pc

i always see "unsupported" resolution of 720x400 in which i don't see anything at all in the monitor..

in which i always have to do recovery mode (xfix) to return to its normal resolution


**i'm not good in editing xorg.conf**

these are the only thing written in the file

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


**how can i use my NX8500 GT without going in the the unsupported mode when restarting the computer to install compiz..**

[COLOR="Magenta"]attached also is my xorg.conf info[/COLOR]

Pls assist.. although i'm still searching for answers.

thanks

---

### Post by loomsen on 2009-04-26
Choose drop to a shell to examine the problem or so. 

Then run 

```
aptitude search nvidia
```

To show whats available. And finally
```
sudo aptitude install nvidia-180-glx
```

When done, run 
```
sudo nvidia-xconfig
```

And just reboot...

---

### Post by jdash1 on 2009-04-26
let me try this..

ill let you know the result.

thanks

---

### Post by jdash1 on 2009-04-26
i already used

c   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-173-dev              - NVIDIA binary Xorg driver development file
c   nvidia-glx-180                  - NVIDIA binary Xorg driver      



3 of these but everytime i reboot the computer its still the same.. gives me "unsupported" resolution of 720x400 in which i don't see anything at all in the monitor.

i sense this has something to do with the monitor  but i canno't replace this.

any ideas ?


thanks

---

### Post by loomsen on 2009-04-26
sudo nvidia-xconfig

---

### Post by jdash1 on 2009-05-08
Sorry for the late reply.. i can only troubleshoot on this during my off,

here's the result..

HOPE SOMEONE can help me out. :)


> **loomsen said:**
> sudo nvidia-xconfig

jdash@jdash-desktop:~$ sudo nvidia-xconfig
[sudo] password for jdash: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'




reason i have that config is that i always use "xfix" to restore, everytime my computer gives me "unsupported" resolution of 720x400



HOPE someone is available to help me.

Thanks

---

### Post by xc3RnbFO8P on 2009-05-08
In Terminal:
> sudo gedit /etc/X11/xorg.conf 
and add these lines and reboot:

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

[B]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection[/B]

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by jdash1 on 2009-05-08
> **Ringi said:**
> In Terminal:

and add these lines and reboot:

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

[B]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection[/B]

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection


DOne doing it. 

after rebooting it. nothing happened ?  i was able to log-in fine


does this allows me to enable the my hardware driver without getting in to the unsupported resolution ?

Thanks

---

### Post by jdash1 on 2009-05-08
Sir, after doing the steps,

rebooting it and enabling the video card driver

still i get the unsupported video.

:(
thanks in advance

---

### Post by xc3RnbFO8P on 2009-05-08
Install Nvidia X server settings in Add/Remove 
In Terminal:
> sudo nvidia-settings
change the resolution  and save to xorg.conf (don't merge)
reboot

---

### Post by jdash1 on 2009-05-08
> **Ringi said:**
> Install Nvidia X server settings in Add/Remove 
In Terminal:

change the resolution  and save to xorg.conf (don't merge)
reboot

after opening the xserver settings. i dont see any option there to change the resolution?

what i did is, i checked the apperance and currently resolution of my computer is already in 1280x1024

***it comes back to 720x400 resolution every time i enable the video card.


Do you think is some sort of hardware issue my monitor is 22" audiosonic lcd.?


thanks

---

### Post by xc3RnbFO8P on 2009-05-08
do you have **nvidia 180  modaliases** installed

---

### Post by jdash1 on 2009-05-08
> **Ringi said:**
> do you have **nvidia 180  modaliases** installed

not installed,
in the update manager, nvidia version 180 and 173 are the option for me to install the driver card..but everytime i install them.. that's the time my computer crashes and return to 720x400 resolution...


thanks

---

### Post by xc3RnbFO8P on 2009-05-08
How did you install Jaunty, fresh or upgrade?

---

### Post by jdash1 on 2009-05-14
> **Ringi said:**
> How did you install Jaunty, fresh or upgrade?

fresh installed 

i'm thinking it could be the monitor that im using.


but anyway i like to try the "envy" thinggy ? I hope that would work

:)

---

### Post by jdash1 on 2009-05-21
up for assistance

thanks


help

---

### Post by xc3RnbFO8P on 2009-05-21
Install this:
> sudo apt-get install xresprobe
and show the output of:
> sudo ddcprobe

---

### Post by jdash1 on 2009-06-16
^ Sorry for the super late response, i was busy in work.

I appreciate the help.

To continue on....

after typing installing it and typing the last command i got these..


jdash@jdash-desktop:~$ sudo ddcprobe 
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: G86 Board - p403h21 Chip Rev
memory: 14336kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail
jdash@jdash-desktop:~$



Pls guide me here.

thanks

---

### Post by jdash1 on 2009-06-16
up for this..hopefully someone would see.


thanks

---

### Post by jdash1 on 2009-06-16
up again :(



THANKS

---

### Post by jdash1 on 2009-06-23
UP again hope someone would help.

---

### Post by jdash1 on 2009-08-12
UP for this...still having same issue..

been busy these days. :(

---

### Post by jdash1 on 2009-08-20
UP for this :(

---

