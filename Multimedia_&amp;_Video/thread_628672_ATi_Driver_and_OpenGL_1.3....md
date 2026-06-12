---
title: "ATi Driver and OpenGL 1.3...?"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Mike_SMD on 2007-12-01
Hi everyone,
I just downloaded the game Glest which looks reasonably fun, however after install and when I tried to play I got this message;

----------

Exception: Your system supports OpenGL version "1.2 (2.0.6747 (8.40.4))"
Glest needs at least version 1.3 to work
You may solve this problem by installing your latest video card drivers

----------

So...
I've got an older Radeon graphics card (9500 pro), I want to give this a shot but I had such a drag-out-hassle of a time getting the darn thing to work with the Ubuntu drivers in the first place that I'm fairly nervous about trying to 'upgrade' anything without knowing whether or not it's going to be worth it at this point. Do the latest ATI proprietary drivers include this bump up to OpenGL 1.3...? If I risk screwing everything up and having my girlfriend scream at me for knocking down the computer YET AGAIN is there going to be any actual reward for my risk?

Is there any simpler way to just upgrade OpenGL instead? 

If anyone knows whether or not this will upgrade me to OpenGl 1.3 please say so. I just need to know that there is a definite purpose to the hassles I am undoubtedly going to unleash. Beyond playing a game, I mean... you know... beyond simply the game....

Thanks!

Mike_SMD

---

### Post by blueyelabs on 2008-01-04
well, unfortunately I have EXACTLY the same problem as you: installed glest, it says it doesn't work.. and that I need OpenGL 1.3... I have a Radeon X800SE which is a few years old, but still copes fine with games like Crysis on my windows partition.

---

### Post by perixx on 2008-01-04
Hy guys!

I think what you need is this:
> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1950 GT
[COLOR="Blue"]OpenGL version string: 2.1.7170 Release[/COLOR]

Open a terminal and type 'fglrxinfo' to verify your OpenGL version and 'dpkg -l xorg-driver-fglrx' to see your ATI-driver's version (latest one is 8.443.1-1).
More info with: 'dpkg -s xorg-driver-fglrx'

Either you get and use 'Envy' to update your driver (didn't work for me) or you look here for manual installation:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

But from my latest experiences, I recommend trying to just remove the old drivers with
```
sudo dpkg -r xorg-driver-fglrx
``` or
```
sudo apt-get remove xorg-driver-fglrx
``` then
download and running the ATI-installer! See also my post and/or find other solutions for you: [http://ubuntuforums.org/showpost.php?p=4061365&postcount=273]("http://ubuntuforums.org/showpost.php?p=4061365&postcount=273")

Get the latest drivers here:
[http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")
before running it with ```
./ati-driver-installer-8.443.1-x86.x86_64.run
``` 
it's maybe a good ideo to check the driver's System Requirements and install missing dependencies (if any) - check them in Synaptic (but don't care for XFree...XYZ - it should be covered by Xorg):
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html")
[COLOR="Blue"]**Added:**[/COLOR]
Commonly used packages for compiling:
> build-essential
libstdc5++
libstdc6++
linux-headers-generic
module-assistant
dh-make
autotools (automake, autoconfig, autogen...)
fakeroot
debhelper
debconf Also, usually you need as well the '-dev' versions from packages for comiling (from source). 
**Note:** I can't tell if those above really are needed for ATI's driver-installer - they were already on my system - but they won't do any harm and I'd feel saver with them on board (if I hadn't have them already :)) when compiling. If I were you, I'd check at least for 1), 2), 4) and 5).

**The reason** I'm giving this advice: it worked totally painless for me, pretty much the opposite from any other method. I cannot guarantee though, that it will also for you...

**[COLOR="DarkOrange"]EDIT:[/COLOR]** If the drivers won't work (especially direct rendering/OpenGL), it may be necessary to do one or several of the following steps:
> a) sudo aticonfig --initial --input=/etc/X11/xorg.conf
b) sudo dpkg-reconfigure -phigh xserver-xorg
c) reboot system Where I'd try the last step first and the 2nd one could cause trouble with keyboard- and language settings, forcing you to re-set them in the desktop manager. Also please make a backup of your xorg.conf file first!!

perixx

---

### Post by blueyelabs on 2008-01-05
Thank you very much. I shall try this and get back to you. I'm glad it was painless for you though, because I must have reinstalled at least 10 times on account of xserver screw ups. I don't want to have to do so again.

---

### Post by blueyelabs on 2008-01-05
Well I used Envy to install the driver, and it worked evidently, but glest still says that my opengl version is too low:

```

gideon@dell8400:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GT
OpenGL version string: 2.1.7170 Release

```

```

gideon@dell8400:~$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 8.443.1-1      Video driver for the ATI graphics accelerato

```

What Glest says is:
```

gideon@dell8400:~$ glest
Exception: Your system supports OpenGL version "1.2 (2.1 Mesa 7.0.1)"
Glest needs at least version 1.3 to work
You may solve this problem by installing your latest video card drivers

```

I don't really know what to do from here.

---

### Post by perixx on 2008-01-05
@blueyelabs,

I'm having trouble with the new driver in the manner I cannot run 'freedroidRPG' anymore. It worked with the old driver version (8.34.sth.) which is provided by the official repos...
Could you play Glest with the old drivers? If so, I'd consider downgrading to an older version - perhaps ATI 'forgot' to implement OpenGL 1.2/1.3 into this driver, or they've crapped things again. 

perixx

---

### Post by perixx on 2008-01-07
hi again!

as I learned of today (installed a Nvidia card on the same system alternatively), the output of 'fglrxinfo' might not be very helpful while trying to get the actually supported OpenGL standard, it might be just showing some ATI-internal version number ... 

I used 'glxinfo' instead and that showed me the actual OpenGL versoin installed along with the latest Nvidia driver: 1.4. Also, there seems to have to be distinguished between OpenGL 'server' and 'client' versions....

perhaps you have a look at it...

perixx

---

