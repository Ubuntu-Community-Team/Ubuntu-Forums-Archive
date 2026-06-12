---
title: "HDMI Detects TV but TV still shows no signal"
date: 2010-12-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gregalynch on 2010-12-28
I just got a HP dm4 and I'm figuring out what works and what doesn't.

When I plug the HDMI into my TV and go to 'monitors' under system -> preferences, it can detect the TV and properly identifies it.  However, when I set the TV input to the HDMI in, it still says no signal.  The computer behaves like it is sending a signal to the TV (I can drag windows onto the other screen, etc, but at the end of the day no signal is being sent.

I'm running Natty, and I'm pretty sure the graphics card for this machine is IntelHD

[Oops, turned out I had a bad cable all along; HDMI works fine out of the box]

---

### Post by cariboo on 2010-12-28
Could you paste the output of:

```
lspci | grep VGA
```

in your next post.

I moved your thread from ABT to Natty testing & discussion.

---

### Post by gregalynch on 2010-12-28
greg@greg-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Thanks

---

### Post by terry_gardener on 2010-12-28
you might have set the screen res or refresh rate to high or to low for your TV to recognise. check the TV manual and set the output to a supported option.

---

### Post by gregalynch on 2010-12-29
I tried all the different aspect ratios the Monitors application (under system -> preferences) allowed, and none of them made a difference.  Its currently only allowing me one option for refresh rate - 60 Hz - so I couldn't adjust that.  

I tried finding what the minimum HDMI refresh rate was for the TV, but I couldn't find anything online or in the manual.  It seems that standard is 120Hz, but I don't know if that means that 60 won't work.  If so, is there a way to get 120Hz as an option?

Thanks

---

### Post by cariboo on 2010-12-29
I assume you've got an i3-5-7 series cpu with builtin gpu. Make sure you are using the i915 driver:

```
lsmod |grep i915
```

The output should look similar to this:

```
lsmod | grep i915
i915                  393661  4 
drm_kms_helper         40746  1 i915
drm                   182215  5 i915,drm_kms_helper
i2c_algo_bit           13150  1 i915
video                  18975  1 i915

```

You could also try creating an xorg.conf file, first go to a console: Ctrl-ALt-F1, and log in, then stop gdm:

```
sudo service gdm stop
```

Next at the prompt type:

```
Xorg -configure
```

this will create an xorg.conf file in your home directory called xorg.conf.new, if I remember correctly :), then copy the file to the /etc/X11 directory:

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

From what I found, the Intel devs are having a bit of a problem getting the driver to be reliable.

**Note:** The TV has to be connected when creating the xorg.conf file

---

### Post by gregalynch on 2010-12-30
i do have the i915 driver.  my output looked pretty much the same as what you posted

i have some questions, though, about the other commands you said for me to run. (pardon my ignorance, i'm still pretty much a beginner at higher-level computer stuff)

1. Is there a difference between 'console' and just typing code into the terminal?
2. Since gdm stop turns of the gui, how do I turn it back on after I've created and moved the xorg file?
3. If I plug in the monitor, do I also have to turn it on under system->preferences->monitors (I currently have it set to off) or does that matter?

Thanks

---

### Post by cariboo on 2010-12-30
> **gregalynch said:**
> i do have the i915 driver.  my output looked pretty much the same as what you posted

i have some questions, though, about the other commands you said for me to run. (pardon my ignorance, i'm still pretty much a beginner at higher-level computer stuff)

1. Is there a difference between 'console' and just typing code into the terminal?

there isn't much difference between a console and a terminal, it's just in this case you need to shut down X in order to create am xorg.conf file.

> 2. Since gdm stop turns of the gui, how do I turn it back on after I've created and moved the xorg file?

to restart gdm the command would be:

```
sudo service gdm start
```

rebooting will do the same thing

> 3. If I plug in the monitor, do I also have to turn it on under system->preferences->monitors (I currently have it set to off) or does that matter?

Thanks

If you are running in a console, qui tools are irrelevant Xorg -configure will detect all the monitors connected and turned on

---

### Post by gregalynch on 2011-01-15
I'm back home now (after a long Christmas break) so I finally got around to trying your fix.  After I typed the command Xorg -configure I get this error message:

Fatal server error:
Cannot move old log file "/var/log/Xorg.0.log" to /var/log/Xorg.0.log.old

I'm not sure what this means, so I didn't type in any of the further commands (I didn't want to screw anything up).

Do you know how to fix this?  Thanks

---

### Post by efflandt on 2011-01-15
cariboo907 may have forgotten an **sudo** in front of that command, because system things usually need to be done as root.

Also what happens if you boot with the with the HDTV or monitor already connected with that input selected, because usually with Intel or ATI BIOS defaults to the external display and X tries to pick a mirrored resolution that works for both.  Although, I have only done VGA with older Intel video laptop and I do not have any laptop with HDMI, so it would revert to mirroring 1024x768 on both displays.

> 3. If I plug in the monitor, do I also have to turn it on under  system->preferences->monitors (I currently have it set to off) or  does that matter?Doesn't it make sense that you would have to have it on for it to work?

If you plug in an external display after starting X, it would usually be recognized if you log out of X and back in.

---

### Post by gregalynch on 2011-01-17
Thanks, I'll try running the command as root.

I've have tried booting with the TV already connected (that's the only way I can get it to recognize it, anyway).  It does automatically set to mirror screens, but nevertheless there is no picture on the TV.

---

### Post by gregalynch on 2011-01-17
well, you were right that I needed to run the configure command as root; all the commands went through this time.

I assume that just creating the config file wasn't the fix (if it was, it didn't work), but just a step to help diagnose the problem.

Here's what the xorg.config file contains:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Does this tell you anything useful?  I don't really know what any of this should say.

Thanks

---

### Post by cariboo on 2011-01-17
I don't know if this will work for Intel graphics chipsets, but if you don't have a picture, go to Applications->Sound->Hardware and select Digital Stereo (HDMI) Output. Then if you need sound from the HDMI output open alsamixer and unmute S/SPDIF.

---

### Post by gregalynch on 2011-01-18
How do you unmute S/SPDIF?  The other devices listed in alsa have a volume setting listed in <>, but S/SPDIF doesn't and there doesn't seem to be any way to change the settings for it.

---

### Post by cariboo on 2011-01-18
As long as there is a 00 instead of MM it isn't muted, press m to unmute.

BTW the solution was in my notes, but I forgot to note why you need to set things that way, it is due to a bug with HDMI

---

### Post by gregalynch on 2011-01-18
thanks.  if that's the case then it isn't muted, but there's still no picture or sound through the TV

---

### Post by gregalynch on 2011-01-28
any other suggestions?

---

