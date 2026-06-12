---
title: "Two video cards, external switch"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by lagartoflojo on 2006-08-11
Hello,
·  I have an Alienware Area 51m - m5500 laptop with an integrated Intel video card and also a separate Nvidia Geforce 6600 Go. On the outside of the laptop there is a switch that says "EXT. VGA" and it is for choosing whether I want to use the Intel card or the Nvidia card. The switch must be moved to the chosen position before booting the computer, and it won't have any effects if it is switched while the computer is turned on.
·  The Geforce uses up a lot more battery than the integrated card, so in the occasions when the computer is not plugged in I want to use the latter. My X server, though, is configured to use the nvidia card and it works great when the EXT. VGA switch is ON. When I boot up while having the EXT. VGA switch in OFF, I receive an error saying that my X server is configured incorrectly. Obviously I do not want to reconfigure my xorg.conf manually everytime I choose to use one video card or the other, so I want that to be handled automatically somehow.
·  Does anyone know how I would go about doing this?

Thanks in advance
 - Lagarto Flojo

---

### Post by tseliot on 2006-08-11
If you don't care about using 3D acceleration you can try in this way:
sudo nano -w /etc/X11/xorg.conf

Get to the Section Device

Put a "#" before the BUSID

and set the driver to "vesa"

So that it looks similar to this (look at the part in red):

```
Section "Device"
    Identifier     "Device[0]"
[COLOR="Red"]    Driver		"vesa"
    #BusID		"PCI:1:0:0"[/COLOR]
EndSection
```

CTRL+X to exit (save the file).

In this way you won't need to reconfigure your xorg.conf every time you swap the cards but you'll make the worst of both your cards

---

### Post by lagartoflojo on 2006-08-11
Thanks for the reply, but that's not really the solution I was
hoping for. But maybe you can help me with an idea that I have.
I ran the lspci command both with EXT VGA in the ON and in the 
OFF positions. The output differs by one line:
```
**EXT. VGA ON:** 0000:03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
**EXT. VGA OFF:** 0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

```
So I was thinking I could have 2 different xorg.conf files, one 

xorg.nvidia.conf and the other xorg.intel.conf. Now, when I boot 
the computer and before starting X, a script could be ran 
automatically that will check the lspci command, find either the 
intel or the nvidia card and then copy the respective conf file 
to xorg.conf.

Would that be plausible?
If so, what would that script be, and when/where would it be 
executed?

Thanks,
- Lagarto Flojo

---

### Post by christhemonkey on 2006-08-11
I made a little script like this once...

A slightly different purpose, but a similar script.
Mine was to choose wether or not to enable 3D acceleration or not based on what kernel i was running.

Will have a dig round and find it for you.

---

### Post by lagartoflojo on 2006-08-11
Thanks! I'd appreciate it!

- Lagarto Flojo

---

### Post by tseliot on 2006-08-11
> **christhemonkey said:**
> I made a little script like this once...

A slightly different purpose, but a similar script.
Mine was to choose wether or not to enable 3D acceleration or not based on what kernel i was running.

Will have a dig round and find it for you.

I would really like to have a look at it

---

### Post by christhemonkey on 2006-08-11
From this thread:
[http://ubuntuforums.org/showthread.php?t=153254](http://ubuntuforums.org/showthread.php?t=153254)

But i have upgraded since, so lost my script.
I think this is what i ended up with though:
```

#! /bin/sh
#
set -e
DESC="checkxserver"
NAME=xorgsetup
SCRIPTNAME=/etc/init.d/$NAME

if uname -r | grep -q 'multimedia';
then cp /etc/X11/xorg.conf.music /etc/X11/xorg.conf
echo ""Music editing i see..."
else cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
echo "Just using the computer"
fi

```

Saved in /etc/init.d and then ran:
```
sudo update-rc.d xorgsetup defaults 99 
```

Obviously i had two xorg.conf's, one for with 3D and one for without.

---

### Post by tseliot on 2006-08-11
> **christhemonkey said:**
> From this thread:
[http://ubuntuforums.org/showthread.php?t=153254](http://ubuntuforums.org/showthread.php?t=153254)

But i have upgraded since, so lost my script.
I think this is what i ended up with though:
```

#! /bin/sh
#
set -e
DESC="checkxserver"
NAME=xorgsetup
SCRIPTNAME=/etc/init.d/$NAME

if uname -r | grep -q 'multimedia'; then
then cp /etc/X11/xorg.conf.music /etc/X11/xorg.conf
echo ""Music editing i see..."
else cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
echo "Just using the computer"
fi

```

Saved in /etc/init.d and then ran:
```
sudo update-rc.d xorgsetup defaults 99 
```

Obviously i had two xorg.conf's, one for with 3D and one for without.

Nice :) 

There is a mistake here:

```
if uname -r | grep -q 'multimedia'**; then**
then cp /etc/X11/xorg.conf.music /etc/X11/xorg.conf
```

should be:
```
if uname -r | grep -q 'multimedia'
then cp /etc/X11/xorg.conf.music /etc/X11/xorg.conf
```

---

### Post by christhemonkey on 2006-08-11
Aah, my apologies.
As you can see in the other thread, i never posted the completed script and upgraded since then, so has been wiped off my hard drive.

But thanks for pointing that out!

---

### Post by tseliot on 2006-08-11
lagartoflojo

these are the instructions you should follow:

type:
```
sudo nano -w /etc/init.d/xorgsetup

```


then copy and paste this:

```
#! /bin/sh
#
set -e
DESC="checkxserver"
NAME=xorgsetup
SCRIPTNAME=/etc/init.d/$NAME

if lspci | grep 'nVidia'
then
    cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
    echo ""Nvidia card detected"
else
    cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
    echo "Intel card detected"
fi
```

then press CTRL+X to exit (save the file).

Make the file executable:
```
sudo chmod a+x /etc/init.d/xorgsetup
```

Then make 2 copies of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.intel
```

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
```


then:
```
sudo nano -w /etc/X11/xorg.conf.intel
```
and set the BUSID to "PCI:0:2:1" and the driver to "i810"

Save and exit


then:
```
sudo nano -w /etc/X11/xorg.conf.nvidia
```
and set the BUSID to "PCI:3:0:0" and the driver to "nvidia"

Save and exit


Then:
```
sudo update-rc.d xorgsetup defaults 99 
```

---

### Post by lagartoflojo on 2006-08-11
Thanks!! I was just coming on the forum to post a script I wrote that did exactly what you posted... It took me a bit, because it is the first bash script I write hehe. I'll post it anyways. What I definitely did not know are all those rc things. I will try your instructions right away. Thanks a lot, I knew it could be done!

**My script**
```
#!/bin/sh

lspcitext=$(lspci | grep -i nvidia)

#if this var is empty, then there is no nvidia card
if [ "$lspcitext" = "" ]
then
	isThereNvidia=false
else
	isThereNvidia=true
fi

if [ "$isThereNvidia" = "true" ]
then
	cp /etc/X11/xorg.nvidia.conf /etc/X11/xorg.conf
else
	cp /etc/X11/xorg.intel.conf /etc/X11/xorg.conf
fi
```

---

### Post by lagartoflojo on 2006-08-11
Okay, so there was only one little mistake and it was that the BusID must be set to "PCI:0:2:0" not the one you specified. That was easy enough.
A completely unrelated problem that I have faced now is that I can only get up to 1024x768 resolution on the intel card while ideally I'd like 1680x1050 like on the nvidia card.
Is this the pertinent xorg.conf section, and is it correct?

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Graphics"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by lagartoflojo on 2006-08-11
Well, it works in the right resolution now. I added "1680x1050" to a few more "Modes" lines in xorg.conf.intel and I installed 915resolution (though I did not even run it, so I guess changing the conf file did the trick). 
Thanks for everything, my system is working just the way I want it to!

-- Lagarto Flojo

---

