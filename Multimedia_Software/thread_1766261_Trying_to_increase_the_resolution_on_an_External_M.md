---
title: "Trying to increase the resolution on an External Monitor"
date: 2011-05-24
forum: Multimedia Software
---

### Post by Hansholz on 2011-05-24
I have seen many screen resolution problems & fixes here on the forum, but none quite the same as mine so I'm creating another thread in the hope of getting some help.

I have an EeePC 1005HA with Intel 945G chipset and graphics. I've got a 21" no-name touchscreen attached to the laptop with the intention of hiding the laptop away behind it and simply using the tactile widescreen with virtual keyboard (onboard). By the way, the Touch screen is working great OOTB in Ub 11.04, although will have to tweak some more to get multi-touch working.

On it's own the netbook runs 1024x600 (16:9) automatically. As soon as I plug in the larger monitor and mirror the images it auto-defaults both to 800x600 60hz and I have no options to select a higher res. I want to be able to run the large screen in something like 1024x600 or better, as long as its 16:9. At the moment everything is stretched out on the larger screen and on the netbook I have a 800x600 with black margins left & right.

Can't seem to work it out. The Monitor Config doesn't give me any higher options than 800x600 when mirrored. Below is the output of xrandr, if it's any help. Also my xorg.conf file is practically empty. Can anyone please help?

Output from xrandr
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0 +   65.0  
   800x600        60.3*    56.2  
   640x480        59.9  
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1
```

I don't know which of the LVDS and the VGA1 is the larger screen.

Here's the xorg.conf ... not sure if this is actually being used or if X is running?
```
# Minimal xorg.conf for the Nouveau driver
Section "Device"
	Identifier	"Default screen"
      	Driver		"nouveau"
EndSection
```

Thanks in advance

---

### Post by Grenage on 2011-05-24
That looks pretty standard, with VGA1 being your external VGA port, and LVDS1 being the computer screen.  xrandr also seems to be listing the correct resolutions for the displays.

Are you sure you have an Intel graphics card?  Your xorg.conf references the nouveau driver, which is the open nvidia driver.  If in doubt, post he output of:

```
lspci | grep VGA
```

If not in doubt, start by changing *nouveau* to *intel*.

---

### Post by Hansholz on 2011-05-24
Thanks for the fast response. I'm not sure if I have an intel graphics card. I looked up the hardware on the Eeepc 1005HA and read it had integrated intel chip and graphics, so assumed. I'm new to Ubuntu and couldn't find an equivalent of Device Manager (win) to check what I actually had.

I found this on the [EeePC from Wikipedia]("http://en.wikipedia.org/wiki/Asus_Eee_PC"):

> **Display**
The Eee PC 700 has a 800×480 pixels 7 inch (178 mm) display, measured diagonally. The screen does not cover the entire space within the lid; instead it is flanked on the sides by stereo speakers and, above, by the (optional) camera in the trim at the top. The Eee PC 900 and 901 come with a 1024x600 pixels 8.9-inch (226 mm) display, almost filling the lid.

The Eee PC 1000 comes with a 10-inch (254 mm) or 10.2-inch (259 mm) display with 1024 x 600 display.

With all models, an external display can be supported through a standard VGA connector. [COLOR="Red"]The manufacturer does not give any specifications on maximum resolution and display configuration (mirroring, extended desktop), but most models can handle an external display at native resolution of 1440 x 1050, and even 1600 x 900 although performance starts to slow down[/COLOR].

Models that ship with Xandros do not have access to the full capacity of the external VGA output by default, allowing only 'mirroring'. [COLOR="red"]Users must reconfigure their xorg.conf file, or install a more feature-rich OS such as Eeebuntu to allow the higher resolution output.[/COLOR]

I'll run that command tonight and let you know what comes out. Thanks!

---

### Post by Grenage on 2011-05-24
> **Hansholz said:**
> Thanks for the fast response. I'm not sure if I have an intel graphics card. I looked up the hardware on the Eeepc 1005HA and read it had integrated intel chip and graphics, so assumed. I'm new to Ubuntu and couldn't find an equivalent of Device Manager (win) to check what I actually had.

I'll run this tonight and let you know what comes out. Thanks!

Great, please do that; once we know what you have, we can build on it.

---

### Post by Hansholz on 2011-05-24
Output of lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
```

Hopefully this shines some light...I managed to edit the xorg.conf using:
```
sudo gedit /usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
```

Is the xorg.conf is in the right folder? I have seen many instances where people are editing it in /etc/x11/xorg.conf

Is this correct?

---

### Post by Grenage on 2011-05-25
That's just an example, and it explains why it has the wrong driver listed; you don't have an xorg.conf, which is common.  1024x600 isn't currently listed by xrandr as an available mode on VGA1, so let's start simple by making it available and trying it out:

```
xrandr --addmode VGA1 1024x600
xrandr --output VGA1 --mode 1024x600
```

How does that fare?

---

### Post by Hansholz on 2011-05-25
Thanks Gren. Once again, I'm caught at work until this evening. So can't try it out till very late tonight (11pm UK time). Will post the response in the early hours!

---

### Post by Grenage on 2011-05-25
Ok dokes, I'll check the thread when I get in, and before I hit the sack. :)

---

### Post by aeiah on 2011-05-25
as stated, by default the largest common resolution both screens share is 800x600.

if you're planning on hiding the laptop out of sight, why are you mirroring screens? just turn off your netbook screen and set your 21" to its native resolution.

ive scripted similar with xrandr so it changes to the external monitor if its plugged in. ill fish it out if you want?

---

### Post by Hansholz on 2011-05-25
> **aeiah said:**
> if you're planning on hiding the laptop out of sight, why are you mirroring screens? just turn off your netbook screen and set your 21" to its native resolution.

ive scripted similar with xrandr so it changes to the external monitor if its plugged in. ill fish it out if you want?

I was wondering how I could do that myself! Is switching off the screen the same as going into what I call "projector mode"...ie Pressing Fn+F8 a couple of times to scroll through Monitor, Monitor + Projector, Projector Only. 

I'm going to add those modes suggested by Grenage anyway, as I would like a few 16:9/16:10 options. Never the less, for the Fn+F8 method, this is how it works on Windows machines. I assume it's the same for Ubuntu. Would restarting cause this setting to default back to netbook screen?

I'd love to see the xrandr script you created. Thanks in advance for the help! There's more than one way to skin a cat, as we say!

---

### Post by Grenage on 2011-05-25
Indeed it's not at all a bad idea to turn off any screen you're not using, something such as:

```
xrandr  --output VGA1 --off
```

Would turn off that output.  I used to have two modes at my old residence; TV + monitor, and monitor only.

---

### Post by Hansholz on 2011-05-25
Thanks guys. This is all very useful. What about closing the netbook? At the moment this kills both screens...I want the 21" to carry on living :) when I shut the netbook. If the netbook's VGA output is off, will closing the lid still kill the 21"?

---

### Post by Grenage on 2011-05-25
> **Hansholz said:**
> Thanks guys. This is all very useful. What about closing the netbook? At the moment this kills both screens...I want the 21" to carry on living :) when I shut the netbook. If the netbook's VGA output is off, will closing the lid still kill the 21"?

I have no idea, but would imagine that's a power management setting.

---

### Post by aeiah on 2011-05-25
i thought my script checked to see if the screen was plugged in, but it doesnt. not that it matters - the command will fail silently if it isnt plugged in. the command in my script is:
```

xrandr --output VGA1 --mode 1024x768 --output LVDS1 --off
```

you'll want to change your --mode to your native resolution

you could put this in your startup and/or as a launcher button.

---

### Post by Hansholz on 2011-05-25
Great stuff. Thanks Aeiah!

I'll let you both know how I get on. [-o<

---

### Post by Hansholz on 2011-05-25
I'm over the moon! Both your solutions worked. I used Gren's tip to add my desired modes and Aieah's tip to set up a startup script running the following:
```
xrandr --output VGA1 --mode 1440x900 --output LVDS1 --off
```

This gives me 16:10 which is just big enough to allow big fingers to tap icons and check boxes etc on the touch screen.

The Power Mgt settings didn't fix the netbook lid closing problem. Closing the lid still makes it suspend and my only other options are hibernate, shutdown and blank screen. But this is a small problem as I have to keep the netbook open anyway to start it, as the button is under the lid.

**Thanks for your help!**

---

### Post by Grenage on 2011-05-26
Great news, glad to hear that you got it sorted.

---

