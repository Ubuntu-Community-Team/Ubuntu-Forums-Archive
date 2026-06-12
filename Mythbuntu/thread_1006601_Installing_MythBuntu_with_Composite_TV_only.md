---
title: "Installing MythBuntu with Composite TV only"
date: 2008-12-09
forum: Mythbuntu
---

### Post by scary_jeff on 2008-12-09
Hi Folks

I've spent a few hours trying to work out what I'm doing wrong, but I thought I would go back to a basic question: Should it be possible to install MythBuntu 8.10 from a CD, with only a composite-video TV connected through an nVidia 8500GT?

What is happening is that if I do not plug a monitor in, I can get to the boot disc menu (install mythbuntu, check RAM, etc), using the TV. Something goes wrong after choosing to install, and I end up at a command prompt. startx complains of no monitor, so I tried editing the xorg.conf file to specify some parameters of the TV, with no luck [though I may well have specified the wrong parameters].
If I repeat the process with a monitor plugged in, the TV never displays anything (not even any BIOS messages).

Sorry if this is covered in a guide somewhere, I did do a few forum searches and had a good trawl with google. I'm happy to post any logs, but I don't know how to transfer them from the machine in question without a GUI.

Cheers

---

### Post by SiHa on 2008-12-09
The best thing (and what I did to install to a machine that would only have s-vid connected) is to install with a monitor connected.
Then install nvidia-settings```
sudo apt-get install nvidia-settings
```

That will install an icon in the admin menus, you can run from here or from the command line. If you run from the command line, run it as 'sudo' otherwise it won't have the permissions to write to your xorg.conf

Once you've got nvidia-settings up, it should give you the option to enable the TV-out (it will probably auto-detect it). You should then be able to set it to TV-only.

As I said this is pretty much the way I did it a few months back with a new install of 8.04.1. I've heard that 8.10 makes less use of xorg.conf, so this may not work.

There's also a package called 'envy'. I've never tried it myself, but many people swear by it for getting the best out of their nVidia kit.

---

### Post by scary_jeff on 2008-12-09
OK, thanks for such a fast response!

The reason I was trying to install with TV-only is that I had already installed using a monitor, and was unable to get anything to come out of the TV output using the nvidia settings manager, or using various guides on setting up tv-out in ubuntu. I thought maybe if I installed with TV only, it might all just work. The nvidia settings found the TV and allowed me to select the resolution, but nothing would be displayed on the TV.

This is still good information, because now I won't spend hours trying to get it to install TV-only :). I have not tried the envy tool you mentioned, so I'll give that a go tomorrow and come back with the results.

Cheers

---

### Post by scary_jeff on 2008-12-10
OK, I didn't use envy in the end, because all it seems to do is install the driver for you. I have installed Mythbuntu now, and the nvidia driver seems to be working correctly (it lets me set resolutions, which it remembers after reboot). I have activated the TV (which the driver detects), and I am confident that the system thinks it is sending something to it.
The resolution on the TV is lower than on the monitor; if I move the mouse to the right from the bottom right of the monitor, then move it left again, the pointer appears back on the monitor at the point where the bottom of the TV should be. Similarly, I can move the mouse a few inches to the right of the monitor, and then have to move it back the same distance to the left to get the pointer back on the monitor.
I know it looks like the TV out on my graphics card simply doesn't work, but I know it does, because I can at least *start* the install process on the TV if no monitor is connected.

Any thoughts or ideas are most welcome!

[edit] I tried booting the machine with only the TV plugged in; it showed the Mythbuntu loading progress bar, but the TV lost signal just after the bar got to 100% [/edit]

---

### Post by wizgnome on 2008-12-11
I recently did a similar installation from the MythBuntu 8.10 live CD (Nvidia 7300 video card). During the initial install there was an option on the Video drivers setting to disable TV out - this is the default. When I changed it to enable TV out then I got no output on my TV display. Leaving the default setting of 'Disable TV out' and it worked fine. I also selected to install the Nvidia drivers.

If I boot with a monitor connected it will output to that, and if I disconnect the monitor it will output to 
the TV when I reboot.

---

### Post by SiHa on 2008-12-11
> **scary_jeff said:**
> 
The resolution on the TV is lower than on the monitor; if I move the mouse to the right from the bottom right of the monitor, then move it left again, the pointer appears back on the monitor at the point where the bottom of the TV should be. Similarly, I can move the mouse a few inches to the right of the monitor, and then have to move it back the same distance to the left to get the pointer back on the monitor.
 

That's just the overscan - all TV's scale the picture so that the edges are slightly off the viewable area of the screen. This essentially hides the ragged edges and other stuff that would otherwise be displayed. Using Nvidia-settings there should be an overscan slider which will let you adjust this in realtime to get the most picture on your screen. It's unlikely you'll be able to get the whole desktop to display, so you might want to use the screen setup wizard in the Utilities / Setup screens in MythTV. This will at least enable you to size the MythTV GUI and playback to the visible portion of the screen.
Beware, though that if you are running Mythbuntu with the standard xfce desktop (the black one), any resizing of the MythTV window will cause the toolbar / panel to sit on top of the window - this is a known bug, not sure it's been fixed yet. A workaround is to set the panel to 'Autohide' - works for me.

> [edit] I tried booting the machine with only the TV plugged in; it showed the Mythbuntu loading progress bar, but the TV lost signal just after the bar got to 100% [/edit] 

That's when your x-server start up. The card either can't detect the TV properly, or doesn't know what mode to use, so it will fall-back to the VGA-out. You probably need to try some of the xorg.conf options that force it to ignore these facts and just squirt the signal where you tell it.

The xorg logfile is a useful place to start, if there's a problem, it will tell you why it has defaulted to VGA.
```
cat /var/log/Xorg.0.log
```

Somthing like this in the device section of your xorg.conf (**/etc/X11/xorg.conf**) should help

```
Option          "TVOutFormat" "COMPONENT"  
Option          "TVStandard" "PAL-B" #or NTSC, PAL-G etc. whatever's correct for where you are
Option          "ConnectedMonitor" "TV" 
```

**Please Note**
Messing with your xorg.conf can render your system useless with no useable video output. Back it up first```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```If you find yourself without a useable display, reboot, and 'Press Esc for Menu' when prompted. At the GRUB menu, select the second (I think) option, and after a little while you should be presented with a menu, one of the options of which is to drop to a root prompt. When you get to the terminal prompt, simply restore the backup (no 'sudo' required - you are root)
```
cp /etc/X11/xorg.bak /etc/X11/xorg.conf
```
then ```
exit
```
to return to the menu, and select 'continue normal boot'. You should now be back where you were before the changes.

---

### Post by scary_jeff on 2008-12-14
> **SiHa said:**
> That's just the overscan - all TV's scale the picture so that the edges are slightly off the viewable area of the screen. This essentially hides the ragged edges and other stuff that would otherwise be displayed.

Hi, I didn't exactly give up yet. What I mean with the mouse pointer was that on the tft monitor [two screens connected], I could move the pointer way to the right, proving that there was some space there that X thought it could draw a mouse onto. Try the same thing on the left, and the mouse just stops at the edge of the screen. Either way, still no output on the TV.

When I say I didn't exactly give up, my plan all along was to use a VGA > SCART lead, which I made. I have had some luck with it, in that I can get my TV to display a vertical black bar with a single pixel vertical white line to the left of it, a flickering blue screen [as opposed to a static blue screen (blue means it didn't manage to lock to anything)], two flickering horizontal white lines, or a plain black screen [after the machine is booted it always goes to plain black screen if there were no errors in Xorg.0.log].

Given that my Xorg.0.log file seems to show it happily loading my mode (only warning is "(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0"), and the TV changes from the blue 'no signal' screen to totally black, does anyone have a thought on what my problem might be? I've checked and rechecked my cable. I'm taking it into work tomorrow to scope up the csync circuit and prove its working.

Cheers

---

### Post by scary_jeff on 2008-12-16
Well, this is sort of solved now.

I had thought that SCART pin 8, which selects 16:9 or 4:3 format for the incoming picture, wouldn't matter given that I can switch to the scart channel and change the picture format on the TV anyway. Turns out I was wrong. ~7.5V on pin 8 now, and it's working :D

Should I mark this as solved? I never solved the original problem, but I am happy in the end.

---

