---
title: "No desktop effects"
date: 2009-03-03
forum: Multimedia Software
---

### Post by velozoom on 2009-03-03
I've searched and not found a solution....hoping someone here has a better clue than me.  

Just rebuilt my workstation by replacing the guts.  Running Ubuntu 8.1 64bit.  I'm using an Asus P5QL-EM mobo with dual integrated video outputs, one VGA and one DVI.  Using two 19" Dell monitors.  THe left is my primary, VGA input.  

I have two issues that I think are likely related, but I'm not sure.  

First, the left monitor (VGA) intermittently flashes off then on.  Usually in sequences of three repetitions.  

Second, I can not enable desktop effects or apply themes.  

I reconfigured X by using ```
$dpkg-reconfigure -phigh xserver-xorg
```

this didn't work.  I checked which chipset I had

Output of $lspci | grep VGA
```
 00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

Then I added the following repository- 
[http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu)

and downloaded the latest drivers.  This didn't work.  When I start compiz from the command line I get- 

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x960) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
 
```

I tried changing the Virtual option in xorg.conf to below 2048 and it did not work.  

Here is my current xorg.conf
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2560 960
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

```

More odd details-

I CAN enable and use desktop effects when I mirror the displays. 

If after mirroring displays and enabling desktop effects I then remove the mirroring, I get a normal primary screen on my left monitor and a "half" screen on my right.  The desktop only goes about 60% of the way across the second monitor.  Both monitors are detected in System > Preferences > Screen Resolution and both resolutions are set to the same thing.  

It seems there is an issue with Compiz and my screen resolution but I had compiz and desktop effects running with the previous mobo and these same monitors/resolutions before.  

Not a clue what else to try.  Any suggestions?

---

