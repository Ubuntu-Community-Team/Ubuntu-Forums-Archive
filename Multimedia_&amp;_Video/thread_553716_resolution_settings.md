---
title: "resolution settings"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by preludefan on 2007-09-18
hi all,

ive just installed fiesty 7.04 and cant change my resolution any higher than 800x600 at 50hz- its horrible,the screen flickers like mad and hurts my eyes- is there some sotware i can install to upgrade the resolution- i have an nvidia gforce  5200 card- i have downloaded drivers but i cant open them due to some text problem- its driving me nuts!
any help would be great!

mike

---

### Post by Steve1961 on 2007-09-18
> **preludefan said:**
> hi all,

ive just installed fiesty 7.04 and cant change my resolution any higher than 800x600 at 50hz- its horrible,the screen flickers like mad and hurts my eyes- is there some sotware i can install to upgrade the resolution- i have an nvidia gforce  5200 card- i have downloaded drivers but i cant open them due to some text problem- its driving me nuts!
any help would be great!

mike

Open a terminal and type 

sudo apt-get install nvidia-glx

Then type:

sudo gedit /etc/X11/xorg.conf

Make sure that this section:

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"

show the "nvidia" driver and not just "nv"

and also make sure this section:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

contains the resolution you want.

Save and close and reboot.

---

### Post by preludefan on 2007-09-18
steve, i just followed your instructions,however nthing has changed- is it possibly something else?
it seems to be locked in 800x600 mode- any clues?

---

### Post by w4ett on 2007-09-18
Let us see your xorg.conf file...in the terminal type:

```
cat /etc/X11/xorg.conf
```

and paste the results of the command back here.

Regarding how to actually fix it, I'd start by reconfiguring your xorg.conf.....boot into recovery mode.  As follows are the down and dirty commands:

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

Then I would install the Nvidia drivers.  There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu (included in Feisty and above), System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by alienexplorers on 2007-09-19
Run the ENVY script as w4ett suggested.  Remember to first delete your old drivers before loading the new ones.

---

