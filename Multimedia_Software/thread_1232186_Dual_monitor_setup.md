---
title: "Dual monitor setup"
date: 2009-08-05
forum: Multimedia Software
---

### Post by kpgalligan on 2009-08-05
I have a monitor attached to my laptop.  They're both the same resolution, so everything works pretty smoothly.  However, the monitor is on the left.  When I configure it that way, the menus and whatnot wind up on the monitor.  However, I use the laptop as the main editing screen.  Is there any way to get the menus and applications bar on the right screen?  I've used both the GUI settings panel and xrandr, and feel comfortable with a more complex command line option.  xorg.conf if absolutely required ;)

Maybe somehow set the x position of the VGA to be a negative?  I have a feeling if I just "try" that I'll be burning a couple hours trying to get my computer to work again.

I guess I'll just try it.

Thanks in advance,
-Kevin

---

### Post by kpgalligan on 2009-08-05
> **kpgalligan said:**
> I guess I'll just try it.

xrandr is smart.  It simply recalculated what the '-1650x0' would mean in real coords, and put the VGA screen back at 0, and the laptop to the right of it at 1650.

So, essentially the same as putting the VGA to the left of the laptop.

Any thoughts on the menu deal?

---

### Post by duanedesign on 2009-09-25
kpgalligan,
Have you made any progress on getting your right monitor to be your 'main' monitor? If so how?
Thanks


EDIT: I came across this GUI for xrandr that looks promising.
[http://www2.bryceharrington.org:8080/drupal/display-config-1](http://www2.bryceharrington.org:8080/drupal/display-config-1)

---

### Post by bluelamp999 on 2009-09-25
You can drag the panel(s) from one monitor to the other...

Press ALT and just drag the panels across.

---

### Post by PeaSoup on 2009-10-08
I'm trying to figure out a similar problem.

The panel dragging tip is nice but doesn't totally solve the issue in my case (although initially I thought it did)

Firstly, the desktop icons (mounted drives etc.) continue to show up on the wrong monitor. If I try to drag&drop them onto the correct monitor, it won't let me - they move back to the first monitor. 

Secondly, windows only seem to expand properly on the one that Ubuntu treats as my primary monitor. If I move the panels to the one I actually want as my primary monitor, and open up a window on there and expand it, it doesn't go all the way to the edge of the screen on one side, and spills over to the other screen on the other side.
I'm not sure if this is to do with different screen resolutions or something, and I think it might stop happening if I could properly choose the primary monitor.

I'm dual booting with Vista, and I must admit the simple checkbox for 'make this my primary monitor' has its advantages :-)

---

### Post by PeaSoup on 2009-10-08
Truly bizarre. I opened up my display preferences and tried the button 'show displays in panel'. Then I got a little icon in the top right of my screen next to the shutdown button. Suddenly the monitors worked exactly as I wanted, screens expanding properly and I was able to drag my mounted volumes into the screen I want. 

Then I reboot, and I'm back to square one. The mounted volumes have migrated back to the wrong screen and i the windows don't expand properly.

Is this just a bug? I haven't done any editing of xorg.conf yet - nothing except plug the monitors in and fiddle with display preferences. Sometimes it works as I want, and sometimes not.

---

### Post by PeaSoup on 2009-10-08
Just an extra note on this as I've been playing around with it for a little while.

As i mentioned before, the Alt+ (panel dragging) provides a partial fix but doesn't seem to solve the underlying issue. But if I turn off one of my screens and turn it on again, and log out/log in when directed to do so, then after doing that I can move my panels, and move my icons without them getting dragged back onto the wrong screen. I can also expand windows in each screen successfully.

(I also get a message at some point saying 'monitor resolution settings has detected that virtual resolution must be set in your configuration file in order to apply your settings. Would you like screen resolution to set the virtual resolution for you? Recommended' - to which I click YES instead of NO)

This is not really satisfactory as it's a pain to switch on/off screens etc. and jiggle my icons every time I boot up. But perhaps based on the above someone can suggest a permanent solution.

---

### Post by PeaSoup on 2009-10-09
Ok after rebooting / fixing screen set up several times yesterday, the setup does seem to be surviving the reboots today... although I suspect it won't last forever.
The cause of these problems still a mystery - anybody got any clue?

---

### Post by Paul dH on 2009-11-06
I got this from a dutch forum and translated it to English:

First: Install the proprietary driver from Nvidia

Do a reboot to load the drivers

Execute the following commands in a terminal session
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
sudo nvidia-settings
```

Step 1: Creates a backup from the original xorg.conf
Step 2: Makes the xorg.conf readable for the Nvidia configuration tool
Step 3: Set the right settings in the configuration tool and save it to the xorg.conf file (/etc/X11/xorg.conf)

Reboot again to check whether everything works.

Link: [http://forum.ubuntu-nl.org/hardware-en-drivers/dual-screen-instellingen-niet-op-te-slaan-in-9-10/](http://forum.ubuntu-nl.org/hardware-en-drivers/dual-screen-instellingen-niet-op-te-slaan-in-9-10/)

Don't shoot me because my crappy English please, I'm also dutch :P

Credits gos to Tabasco

Good luck, Paul

---

### Post by xnoxpx on 2009-11-22
From a command line try this

First, to get a list of your outputs 
```
xrandr
```
> Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
**VGA1 disconnected** (normal left inverted right x axis y axis)
**LVDS1 connected ** 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   50.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
**DVI1 disconnected** (normal left inverted right x axis y axis)


I see that my external monitor is "VGA1"(its disconnected right now)
so I then type 
```
xrandr --output VGA1 --auto --primary --right-of LVDS1
```
--output [the physical display you want to work with]
--auto [enables it to its preferred mode (if connected) or disables it(if disconnected)]
--primary [sets the physical display as your main monitor(panels and primary focus)]
--right-of [ configures the physical display connected to VGA1 to be to the right of the physical display LVDS1]
    **--left of**, --above, --below, --same-as [are also valid options]

If --auto sets a resolution you don't like, you can use 
```
xrandr --mode 1024x768
```
instead of 1024x768 you can use what ever resolution you want.

so for me the full command would be 
```
xrandr --output VGA1 --mode 1024x768 --primary --right-of LVDS1 --output LVDS1 --auto
```

---

### Post by Sawer on 2009-11-23
How to I get the settings to save? I've tried to save the settings from the nvidia server settings GUI with no luck. Is there a way to do this from the cml? Also could you post your xorg.conf, to make sure I put things in the right place.
Thanks

---

### Post by Sawer on 2009-11-23
Fixed: Ended up coping the xorg.conf from the nvidia server settings and pasting it in my xorg conf.

---

### Post by srikesh on 2009-12-13
Hello all,

I am trying to get my dual-screen set up to work in Ubuntu 9.10.

I am working with:

a) Toshiba Satellite Laptop
b) HP 2035 External Monitor

I have partially succeeded in getting the dual-screen set-up to work to the point where I get maximum resolution on the external monitor (1600x1200) but the laptop display resolution is low (800x600).

In the 'Display Preferences' dialog box I have the option to increase the resolution of the laptop display to '1024x768' or '1280x800'. But when I try one of those two options, I get the following error message:

"Monitor Resolution Settings has detected that the virtual resolution must be set in your configuration file in order to apply your settings. Would you like Screen Resolution to set the virtual resolution for you? (Recommended)".

If I select the recommended option, I am not able to log back into the regular gnome interface and get an error. Looking around in the error message I realized that Ubuntu writes a new 'xorg.conf' file that only lists the external monitor with the maximum virtual resolution of 1600x1200. The only way for me to get back to the usual ubuntu desktop screen is to replace the new 'xorg.conf' file with the backed-up file.

Can someone please help me figure out what is going on. Why can I get 800x600 with out a problem but with anything higher, Ubuntu complaints about virtual resolution? I would like to have the maximum resolution in both the screens.

According to my 'lspci', my graphics card is VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Thanks.
Srikesh

---

### Post by xnoxpx on 2009-12-14
> **srikesh said:**
> Hello all,

I am trying to get my dual-screen set up to work in Ubuntu 9.10.

I am working with:

a) Toshiba Satellite Laptop
b) HP 2035 External Monitor

I have partially succeeded in getting the dual-screen set-up to work to the point where I get maximum resolution on the external monitor (1600x1200) but the laptop display resolution is low (800x600).

In the 'Display Preferences' dialog box I have the option to increase the resolution of the laptop display to '1024x768' or '1280x800'. But when I try one of those two options, I get the following error message:

"Monitor Resolution Settings has detected that the virtual resolution must be set in your configuration file in order to apply your settings. Would you like Screen Resolution to set the virtual resolution for you? (Recommended)".

If I select the recommended option, I am not able to log back into the regular gnome interface and get an error. Looking around in the error message I realized that Ubuntu writes a new 'xorg.conf' file that only lists the external monitor with the maximum virtual resolution of 1600x1200. The only way for me to get back to the usual ubuntu desktop screen is to replace the new 'xorg.conf' file with the backed-up file.

Can someone please help me figure out what is going on. Why can I get 800x600 with out a problem but with anything higher, Ubuntu complaints about virtual resolution? I would like to have the maximum resolution in both the screens.

According to my 'lspci', my graphics card is VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Thanks.
Srikesh


Look at my previous post, does it fix the problem, is it only for the current session?

---

### Post by srikesh on 2009-12-14
> **xnoxpx said:**
> Look at my previous post, does it fix the problem, is it only for the current session?

Here is what my xrandr has to say:

Screen 0: minimum 320 x 200, current 2000 x 1600, maximum 2048 x 2048
VGA1 connected 1200x1600+0+0 left (normal left inverted right x axis y axis) 408mm x 306mm
   1600x1200      60.0*+
   1280x1024      75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 800x600+1200+0 (normal left inverted right x axis y axis) 289mm x 21mm
   1280x800       60.1 +
   1024x768       60.0  
   800x600        60.3* 
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)

When I type in 'xrandr --output LVDS1 --mode 1280x800' I get the message 'xrandr: screen cannot be larger than 2048x2048 (desired size 2480x1600)'.  Is there a way to increase the maximum screen size to (1200+1280) 2480x2048?

To answer your question, xnoxpx, it is not just for the current session.

---

### Post by xnoxpx on 2009-12-16
> **srikesh said:**
> 

When I type in 'xrandr --output LVDS1 --mode 1280x800' I get the message 'xrandr: screen cannot be larger than 2048x2048 (desired size 2480x1600)'.  Is there a way to increase the maximum screen size to (1200+1280) 2480x2048?


PER [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

   xrandr: screen cannot be larger than 1600x1600 (desired size 2624x1200)

This can be fixed by editing xorg.conf and changing the virtual line (see example above) to something like:

   Virtual 2624 1200

Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048.** The virtual screen can be larger but DRI will be disabled. This may matter if you like games and compiz desktop effects, or if you want Google Earth to display in better than geological time.** Obviously the larger the virtual desktop, the more graphics memory is used. So for good performance with a shared graphics system such as Intel the Virtual should be no larger than necessary.

It is possible to set screen locations as --left-of, --right-of, --above and --below. Assuming displays sizes of 1024x768 and 1200x1600:

---

