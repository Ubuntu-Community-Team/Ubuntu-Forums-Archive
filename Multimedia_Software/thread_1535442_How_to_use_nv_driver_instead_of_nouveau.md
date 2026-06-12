---
title: "How to use nv driver instead of nouveau"
date: 2010-07-20
forum: Multimedia Software
---

### Post by applescotty on 2010-07-20
I'm trying to switch to use the nv driver for my video card instead of the nouveau drivers (see bottom for why, if interested). I running Lucid Lynx, 10.04. I followed the instructions in post #5 of this thread to generate the xorg.conf file:
[http://ubuntuforums.org/showthread.php?t=1271960](http://ubuntuforums.org/showthread.php?t=1271960)

So, I've got the following in my xorg.conf file (placed in /etx/X11/):

```
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV34M [GeForce FX Go5200 32M/64M]"
	BusID       "PCI:1:0:0"
EndSection
```

After a restart, I run lshw, and see the following entry:
```
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200 32M/64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:10 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable)
```

This seems to indicate that it is still using the nouveau driver.

So, how can I get it to use the nv driver instead of the nouveau driver?

I'm wanting to try the nv driver because both the nouveau driver and the NVIDIA binaries cause some video issues (either not resuming properly from sleep, or slow screen updates). The previous owner of the laptop said he used Ubuntu without issues, but I believe it was a release older than Lucid Lynx, and so he was probably using the nv driver. Thus, my interest in trying it.

Thanks!
Scott

---

### Post by rollin on 2010-07-20
Hey and welcome to the forum! I had some issues with an older PC which would not even boot with the nouveau driver, I could only get it to run 9.10 which uses vesa, so I can't think of a solution to swap them in 10.04 for booting.That said...

If you're literally just wanting to swap the nouveau driver for an official nvidia one, here is what I used.
Get your card info using:

```
lspci -v | grep VGA
```Just go to [www.nvidia.com]("http://www.nvidia.com/").  Download the driver to your home directory or whatever. Go to tty 1,  and kill the x session, using the commands:

```
Ctrl+Alt+F1
sudo /etc/init.d/gdm stop 

```Now cd to the directory where you downloaded the file and the  command to install is:
```

sudo sh <name of NVIDIA driver> 
```Personally I had some hash sum mishmatches at this stage due to  the download in FF, so I ended up downloading it with wget and the  installation went smoothly. I rebooted after this and removed the  proprietory drivers and everything was good, proper resolution etc...

Part of the script that comes with the driver updates Xorg for you, so hopefully this will solve the problem!

---

### Post by applescotty on 2010-07-21
rollin,

Thanks for the welcome and for the info. Unfortunately, the Nvidia binaries seem to cause problems of their own for me (the display starts updating very slowly after about 10 or 15 minutes of running, or after resuming). So, moving to those won't help my issue.

Scott

---

### Post by wojox on 2010-07-21
A lot has changed since 10.04. Try this [ Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

---

### Post by applescotty on 2010-07-21
So are the NVIDIA binary drivers that I would get from NVIDIA's site different from the NVIDIA binary drivers that get installed when I go through the Hardware Drivers control panel?

---

### Post by rollin on 2010-07-21
Hey you're welcome for the info! 

QUOTE=applescotty;9617585]So are the NVIDIA binary drivers that I would  get from NVIDIA's site different from the NVIDIA binary drivers that  get installed when I go through the Hardware Drivers control  panel?[/QUOTE]

They seems to be as I tried that method and they didn't work for me, but the one on the website  did?! I wish you luck in finding a solution whatever you decide! The link from wojox looks good too.

---

### Post by applescotty on 2010-08-06
Well, I was able to disable the use of the nouveau driver by blacklisting it. However, that didn't solve my problem. However, I was eventually able to get my system to be happy by using the nVidia driver, and setting the Visual Effects to None. Maybe it's not as pretty, but it works. :)

Scott

---

