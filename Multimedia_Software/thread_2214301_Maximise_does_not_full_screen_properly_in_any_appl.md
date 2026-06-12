---
title: "Maximise does not full screen properly in any application"
date: 2014-03-31
forum: Multimedia Software
---

### Post by uzk20707 on 2014-03-31
When maximising any application window (even via F11 full screen), the application does not take up the entire screenspace (as can be seen in the following screenshot):

[http://imageshack.com/a/img41/8596/yzvb.png](http://imageshack.com/a/img41/8596/yzvb.png)

Resizing is not a practical solution in terms of games (where distracting window borders can still be seen) and I'm wondering if there is some way to correct it so maximise/fullscreen takes up the full screen?

---

### Post by bapoumba on 2014-03-31
Do you mean the space between the FF windows and the panel ?
Please have a look at the margin tab in Prefs > Openbox Config Manager.

---

### Post by uzk20707 on 2014-03-31
> **bapoumba said:**
> Do you mean the space between the FF windows and the panel ?
Please have a look at the margin tab in Prefs > Openbox Config Manager.

Yeah, the gap at the bottom.

Margins are all 0. Curiously the background image of the login screen (but not the desktop screen) also has a tiled effect that has a line on the exact same point.

---

### Post by bapoumba on 2014-03-31
Hmm, I'm not much into video stuff. Please post your config, including video card and drivers you are using, so that others can help you. Thanks.

---

### Post by uzk20707 on 2014-03-31
> **bapoumba said:**
> Hmm, I'm not much into video stuff. Please post your config, including video card and drivers you are using, so that others can help you. Thanks.

How do I do that?

Here's what I mean about the background stuff doing it:
[http://imageshack.com/a/img834/2329/yhjw.png](http://imageshack.com/a/img834/2329/yhjw.png)

Surely that must be a bug?

---

### Post by bapoumba on 2014-03-31
> **uzk20707 said:**
> How do I do that?

Here's what I mean about the background stuff doing it:
[http://imageshack.com/a/img834/2329/yhjw.png](http://imageshack.com/a/img834/2329/yhjw.png)

Surely that must be a bug?

I do not know if it is a bug as the bottom of the wallpaper gets drawn below the area your maximized windows can open.

To get your video card info :
```
sudo lshw -class display
```

---

### Post by uzk20707 on 2014-03-31
> **bapoumba said:**
> 
To get your video card info :
```
sudo lshw -class display
```

Produces:

```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2400000-f24fffff


```

---

### Post by bapoumba on 2014-03-31
Thank. As I said, I'm not much into video and stuff. You have intel (same as here) I suppose you have no restricted drivers installed.
So I'm not sure where to point you at. One thing : in the Openbox Config Manager, do you have a reserved space for a dock ? It is the last item on the vertical left list.

---

### Post by uzk20707 on 2014-04-01
> **bapoumba said:**
> Thank. As I said, I'm not much into video and stuff. You have intel (same as here) I suppose you have no restricted drivers installed.
So I'm not sure where to point you at. One thing : in the Openbox Config Manager, do you have a reserved space for a dock ? It is the last item on the vertical left list.

Sorry for the delay. According to dockapps it's position is 'top-left'. There doesn't appear to be anyway to disable it. I don't have any dockapps.

---

### Post by vasa1 on 2014-04-01
> **uzk20707 said:**
> Sorry for the delay. According to dockapps it's position is 'top-left'. There doesn't appear to be anyway to disable it. I don't have any dockapps.
What do you have in the last tab (Advanced) of Panel Preferences (which you get after right-clicking on lxpanel and choosing Panel Settings)?
Under Properties, I have both items unticked.

---

### Post by bapoumba on 2014-04-01
> **vasa1 said:**
> What do you have in the last tab (Advanced) of Panel Preferences (which you get after right-clicking on lxpanel and choosing Panel Settings)?
Under Properties, I have both items unticked.
Both are ticked here.. No issue.

---

### Post by uzk20707 on 2014-04-01
> **vasa1 said:**
> What do you have in the last tab (Advanced) of Panel Preferences (which you get after right-clicking on lxpanel and choosing Panel Settings)?
Under Properties, I have both items unticked.

Despite parsing through the menu options, I cannot find 'lxpanel'.

---

### Post by uzk20707 on 2014-04-01
I apologise, I have found lxpanel and unticked the boxes:
[http://imageshack.com/a/img69/6977/gfwb.png](http://imageshack.com/a/img69/6977/gfwb.png)

However the results are the same.

---

### Post by bapoumba on 2014-04-01
> **uzk20707 said:**
> I apologise, I have found lxpanel and unticked the boxes:
[http://imageshack.com/a/img69/6977/gfwb.png](http://imageshack.com/a/img69/6977/gfwb.png)

However the results are the same.
Hmm, would you happen to have a second transparent panel above the bottom one ?
Edit : or have you connected a second screen with a different resolution at some point ? What is the output to **xrandr** ?

---

### Post by uzk20707 on 2014-04-01
> **bapoumba said:**
> Hmm, would you happen to have a second transparent panel above the bottom one ?
Edit : or have you connected a second screen with a different resolution at some point ? What is the output to **xrandr** ?

I have no transparent panels (this is a relatively fresh install).

I have a laptop (it's screen cannot be used) that uses an external screen as it's main screen.

Xrandr produces:
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by bapoumba on 2014-04-01
> **uzk20707 said:**
> I have no transparent panels (this is a relatively fresh install).

I have a laptop (it's screen cannot be used) that uses an external screen as it's main screen.

Xrandr produces: <snipped>
Could it be the bigger screen is using your laptop dead screen resolution or windows size or something ?
Edit : sorry, it's way past time to log off for me. Please have a look here : [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by uzk20707 on 2014-04-01
> **bapoumba said:**
> Could it be the bigger screen is using your laptop dead screen resolution or windows size or something ?
Edit : sorry, it's way past time to log off for me. Please have a look here : [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I did a rough comparison of the border differences, and apparently the windows maximise to a size of 1280x800, which is indeed the size of the defunct laptop screen. The actual screensize is 1280x1024

No need to apologise, you're helping me for free and your help is greatly appreciated. The fact the problem has been identified means that a solution will be much easier to develop. I'm guessing there must be an inconsistency somewhere in the software settings, because the background is sized correctly even if maximise isn't. In the meantime I'm going to see if I can use a resolution that both screens share.

---

### Post by bapoumba on 2014-04-02
I cannot test, maybe something along these lines : [http://forum.lxde.org/viewtopic.php?f=47&t=36489](http://forum.lxde.org/viewtopic.php?f=47&t=36489)

Edit : I know this is for trusty, may be an idea here : [http://ubuntuforums.org/showthread.php?t=2214380](http://ubuntuforums.org/showthread.php?t=2214380)
I may have missed it, which Ubuntu release are you running ? > Edit 2: 13.10, it is in one of your screenshots..

---

### Post by uzk20707 on 2014-04-04
> **bapoumba said:**
> I cannot test, maybe something along these lines : [http://forum.lxde.org/viewtopic.php?f=47&t=36489](http://forum.lxde.org/viewtopic.php?f=47&t=36489)

Edit : I know this is for trusty, may be an idea here : [http://ubuntuforums.org/showthread.php?t=2214380](http://ubuntuforums.org/showthread.php?t=2214380)
I may have missed it, which Ubuntu release are you running ? > Edit 2: 13.10, it is in one of your screenshots..

This has been extremely helpful (thank you very much for your help). Apparently the laptop screen is still on and isn't disabled when an external monitor is connected or when the lid is closed, disabling it with xrandr allows it to go fullscreen, but I recall a bug from my previous experience with xrandr when configuring resolution that xrandr doesn't tend to save it's settings.

Do you know the solution to that problem would be?

---

### Post by bapoumba on 2014-04-04
I'll look again tonight, last night I searched for the exact file to modify to make it permanent. But the file is different for different releases, especially after moving away from the ancien xorg.conf. I'll double check.

Edit : please have a look here : [https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)
The /etc/X11/xorg.conf.d/10-monitor.conf file is what I had in mind, provided the file location is correct.
[https://wiki.archlinux.org/index.php/Xorg#Monitor_settings](https://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

---

### Post by uzk20707 on 2014-04-04
> **bapoumba said:**
> I'll look again tonight, last night I searched for the exact file to modify to make it permanent. But the file is different for different releases, especially after moving away from the ancien xorg.conf. I'll double check.

Edit : please have a look here : [https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)
The /etc/X11/xorg.conf.d/10-monitor.conf file is what I had in mind, provided the file location is correct.
[https://wiki.archlinux.org/index.php/Xorg#Monitor_settings](https://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

Apparently the file directory is incorrect. In response to your earlier comment the system version is Lubuntu 13.10 Saucy Salamander (but I'm figuring you figured it out, so I'm just confirming).

---

### Post by bapoumba on 2014-04-04
> **uzk20707 said:**
> Apparently the file directory is incorrect. In response to your earlier comment the system version is Lubuntu 13.10 Saucy Salamander (but I'm figuring you figured it out, so I'm just confirming).
So if you do not have a  /etc/X11/xorg.conf.d/, please have a look at /usr/share/X11/xorg.conf.d/, this is where I have all the other config files :
```
ls /usr/share/X11/xorg.conf.d/
10-evdev.conf         11-evdev-trackpoint.conf  50-wacom.conf
10-quirks.conf        50-synaptics.conf         51-synaptics-quirks.conf
11-evdev-quirks.conf  50-vmmouse.conf
```

This is where you need to create the 10-monitor.conf file.

---

### Post by uzk20707 on 2014-04-05
> **bapoumba said:**
> So if you do not have a  /etc/X11/xorg.conf.d/, please have a look at /usr/share/X11/xorg.conf.d/, this is where I have all the other config files :
```
ls /usr/share/X11/xorg.conf.d/
10-evdev.conf         11-evdev-trackpoint.conf  50-wacom.conf
10-quirks.conf        50-synaptics.conf         51-synaptics-quirks.conf
11-evdev-quirks.conf  50-vmmouse.conf
```

This is where you need to create the 10-monitor.conf file.

I don't understand. What am I doing with the 10-monitor.conf file?

---

### Post by bapoumba on 2014-04-05
> **uzk20707 said:**
> I don't understand. What am I doing with the 10-monitor.conf file?

From the last link in my previous post, if you want to perm change the resolution, you need to create the file. There is an example in the Arch wiki link that you can use, provided you set it up according to you own bigger monitor:
```
Section "Monitor"
    Identifier             "Monitor0"
EndSection

Section "Device"
    Identifier             "Device0"
    Driver                 "vesa" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier             "Screen0"  #Collapse Monitor and Device section to Screen section
    Device                 "Device0"
    Monitor                "Monitor0"
    DefaultDepth           16 #Choose the depth (16||24)
    SubSection             "Display"
        Depth              16
        Modes              "1024x768_75.00" #Choose the resolution
    EndSubSection
EndSection
```
I was not certain where to create the file. If you do not have /etc/X11/xorg.conf.d/, have a look at /usr/share/X11/xorg.conf.d/ where I have the related stuff on 14.04.

---

### Post by uzk20707 on 2014-04-07
> **bapoumba said:**
> From the last link in my previous post, if you want to perm change the resolution, you need to create the file. There is an example in the Arch wiki link that you can use, provided you set it up according to you own bigger monitor:
```
Section "Monitor"
    Identifier             "Monitor0"
EndSection

Section "Device"
    Identifier             "Device0"
    Driver                 "vesa" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier             "Screen0"  #Collapse Monitor and Device section to Screen section
    Device                 "Device0"
    Monitor                "Monitor0"
    DefaultDepth           16 #Choose the depth (16||24)
    SubSection             "Display"
        Depth              16
        Modes              "1024x768_75.00" #Choose the resolution
    EndSubSection
EndSection
```
I was not certain where to create the file. If you do not have /etc/X11/xorg.conf.d/, have a look at /usr/share/X11/xorg.conf.d/ where I have the related stuff on 14.04.

Attempting to construct the file there results in:

> Error opening file '/usr/share/X11/xorg.conf.d/10-monitor.conf': Permission denied

---

### Post by bapoumba on 2014-04-07
When do you get the error? Creating the file or having it run when you boot up? (I suspect the first one).

---

### Post by uzk20707 on 2014-04-07
> **bapoumba said:**
> When do you get the error? Creating the file or having it run when you boot up? (I suspect the first one).

Creating the file.

---

### Post by bapoumba on 2014-04-08
OK, the file has to be created on the root filesystem where you need root privileges to write. You could do it opening leafpad as root, but I do not like it much that way. I'd prefer using nano which is a small command line editor. Open a terminal and run:

```
sudo nano /usr/share/X11/xorg.conf.d/10-monitor.conf
```
It will create the file. Include your settings. ctrl-o (letter o) to save, ctrl-x to exit nano. You may have to reboot, not sure a simple logout/log back in gets the conf files to be read again.

Please have a look at /usr/share/X11/xorg.conf.d/ and confirm you have other similar files in there. They may be different from mine, which are default and have not been modified, but they start with a rank number and end up with .conf

[http://linux.die.net/man/1/nano](http://linux.die.net/man/1/nano)

---

### Post by uzk20707 on 2014-04-09
Okay, I'm confused about how to gather the information required in order to fill in the file to save the settings. Also, I don't know how to configure it to automatically disable the laptop screen every time it starts up (suffers from the same problem). This is extremely complex.

---

### Post by bapoumba on 2014-04-10
I have moved your thread to Multimedia & Video. Hopefully someone will be able to guide you through. I'd need to do some testing because I'm not that at ease with video stuff, but I'm running out of free time. Quite sorry..

---

