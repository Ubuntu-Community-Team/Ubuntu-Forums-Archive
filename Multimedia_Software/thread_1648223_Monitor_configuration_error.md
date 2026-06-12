---
title: "Monitor configuration error"
date: 2010-12-18
forum: Multimedia Software
---

### Post by electrojustin on 2010-12-18
Recently, my computer has been giving me a message on boot-up saying "Could not apply stored configuration for monitors. Xserver does not support size requested." When I login, the resolution is messed up and mirror screens is enabled. I tried to change this in Preferences->Monitors, but it gives me the error that I need to logout and login again. Doing as it asks only produces the same errors. Anyone know how to fix this?

My system:
Acer 23 in. monitor | Samsung 17 in. | ATI Radeon 1200 | 320 GB Western Digital Hardrive | Dynex 400 watt power supply | Gigabyte GA-MA785GPM motherboard | AMD Phenom X4 processor | 2, 2 GB Crucial DDR2 RAM modules

---

### Post by tjones00 on 2010-12-19
With a radeon 1200 I assume you're using the open source driver radeon or radeonhd correct?

Try disabling xrandr in your xorg.conf and disable plymouth. Back when I was messing with a 1250 and the radeonhd driver it cleared up some display issues I had. My errors were very similar to yours.

See post #4 in this thread although it's specific to the radeonhd driver it might help you sort out your troubles. [http://ubuntuforums.org/showthread.php?t=1538308](http://ubuntuforums.org/showthread.php?t=1538308)

---

### Post by electrojustin on 2010-12-19
After disabling xrandr, it seems I can change the resolution and refresh rate correctly, but dual screens does not work. I am not sure how to disable plymouth.

---

### Post by tjones00 on 2010-12-19
Ok I was mistaken. In order to get multiple screens working with the opensource driver we need to keep xrandr on.

The good news though is we now know your issue is with xrandr. As to your original error it's probably due to the virtual desktop being larger than what your card can support. The size of the virtual desktop(all screens combined) depends on the amount of graphics memory of your video card.

Enable xrandr again and in a terminal (while both monitors/screens are active with the messed up resolutions) type:

```
sudo xrandr -q
```This should display the active connections and possible resolutions for both your monitors.

A quick google produced the following link regarding your card's capacity. [https://groups.google.com/group/x1250/web/ati-radeon-x1250-specifications](https://groups.google.com/group/x1250/web/ati-radeon-x1250-specifications)

Stating "It supports a maximum resolution of 2048x1536" so you should try not to exceed this. Meaning 2 x 1024x768 screens or any combination (one larger one smaller) not exceeding that combined value for a virtual screen.

This might vary according to your card. So some experimentation is in order try to see what your max combined resolution is.


[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)  information about setting up xrandr in your xorg.conf.

The opensource drivers don't generate an xorg.conf by default anymore so to make one yourself open a terminal and type.

```
sudo X -configure
```This will create an xorg.conf at /etc/X11/xorg.conf that you can then edit yourself adding xrandr variables/options.

Hope that helped.

---

### Post by electrojustin on 2010-12-19
I tried typing in sudo X -configure, but got the following error: Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by tjones00 on 2010-12-20
Try shutting down the x server before running X -configure.

press ctrl+alt+f2 and log in

type 

```
sudo service gdm stop
```

then type 

```
sudo X -configure
```

finally type

```

sudo service gdm start 
```

to restart the x server

---

### Post by electrojustin on 2010-12-20
Adding the configuration file did not work. Also, while I got it to work with a lower resolution, I actually have a Radeon HD 4200, not a 1200 and would like everything to not appear huge on my second screen.

---

### Post by electrojustin on 2010-12-20
I tried uninstalling Xserver, then reinstalling it, but I was unable to reinstall it and was forced to reload ubuntu. Thanks for your help anyway!

---

### Post by tjones00 on 2010-12-20
Oh a radeon hd 4200 that's a different can of worms.

Remove that xorg.conf if you haven't already. sudo rm /etc/X11/xorg.conf

The radeon hd 4200 should still be supported by the ati proprietary drivers. I'd suggest using those.  System > Administration > Hardware Drivers.

As to specs on your card. [http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/ati-radeon-hd-4200/pages/ati-radeon-hd-4200-specificatications.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/ati-radeon-hd-4200/pages/ati-radeon-hd-4200-specificatications.aspx)


[LIST]
[*]Two integrated DVI display outputs         
[LIST]
[*]Primary supports 18-, 24-, and 30-bit  digital displays at all resolutions up to 1920x1200 (single-link DVI) or  2560x1600 (dual-link DVI)1
[*]Secondary supports 18-, 24-, and 30-bit digital displays at all resolutions up to 1920x1200 (single-link DVI only)1
[*]Each includes HDCP encoder with on-chip key storage for maximum resolution playback of protected content2
[/LIST]
[*]Two integrated DisplayPort™ outputs         
[LIST]
[*]Supports 24- and 30-bit displays at all resolutions up to 2560x16001
[*]1, 2, or 4 lanes per output, with data rate up to 2.7 Gbps per lane
[/LIST]
[*]Two integrated 400 MHz 30-bit RAMDACs         
[LIST]
[*]Each supports analog displays connected by VGA at all resolutions up to 2048x15361
[/LIST]
[/LIST]
Just remember the virtual desktop that determines the combined total resolution of any multiple display setup. I can't remember if xrandr is used/required with the ati proprietary drivers.

According to the tech specs on your card you should be able run 2 x 1920x1200 via the two DVI connections that is if your monitors can support 1920x1200.

---

