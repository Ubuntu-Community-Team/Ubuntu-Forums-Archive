---
title: "Nvidia Driver issue with Riva TNT2"
date: 2008-07-01
forum: Multimedia Software
---

### Post by RViN on 2008-07-01
I'm using Ubuntu 8.04 with a clean install I tried updating the Graphics Drivers (the restricted Nvidia drivers) which Ubuntu prompted me to do when I first booted. Now I tried updating from System>administration>hardware drivers, and all that I will get once the install is done and the computer reboots is a black screen.

Then I tried searching all over the net and I came up upon this program called EnvyNG that was supposed to help me with this issue. Used it to install the drivers (first auto detect then second time I directed it to install driver version 71.86.04) and both times when I should be seeing the login window it showed me instead an empty screen that was alternating between black and grey.

My question is, is there a way to actually get these drivers working? Should I be installing a different version of the drivers? Is there something I'm missing?

The exact model of my graphics card is Creative Riva TNT2 Ultra

If people wonder why so many people prefer windows, this is the answer. Never had any problems installing drivers using windows :(

---

### Post by overdrank on 2008-07-01
> **RViN said:**
> I'm using Ubuntu 8.04 with a clean install I tried updating the Graphics Drivers (the restricted Nvidia drivers) which Ubuntu prompted me to do when I first booted. Now I tried updating from System>administration>hardware drivers, and all that I will get once the install is done and the computer reboots is a black screen.

Then I tried searching all over the net and I came up upon this program called EnvyNG that was supposed to help me with this issue. Used it to install the drivers (first auto detect then second time I directed it to install driver version 71.86.04) and both times when I should be seeing the login window it showed me instead an empty screen that was alternating between black and grey.

My question is, is there a way to actually get these drivers working? Should I be installing a different version of the drivers? Is there something I'm missing?

The exact model of my graphics card is Creative Riva TNT2 Ultra

If people wonder why so many people prefer windows, this is the answer. Never had any problems installing drivers using windows :(

Hi and welcome, Yes ubuntu is not for all but if you get the black screen again try and use the keys, alt, ctrl, F1 and this will bring you to the command prompt where you can login. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or you may try and reboot into recovery mode and use xfix to correct the GUI. That model of the graphic card should use the legacy drivers if I am not mistaken.

---

### Post by RViN on 2008-07-06
> **overdrank said:**
> Hi and welcome, Yes ubuntu is not for all but if you get the black screen again try and use the keys, alt, ctrl, F1 and this will bring you to the command prompt where you can login. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or you may try and reboot into recovery mode and use xfix to correct the GUI. That model of the graphic card should use the legacy drivers if I am not mistaken.

When you say reconfigure xorg do you mean to tell me reset the thing and change the drivers back to the generic 'nv' drivers to get the GUI working again? (which means that I'm back to where I started and theres no way to install these damn drivers) Or is there a chance that if I run that command the Nvidia drivers might work? Because when I had that black screen problem I just went into recovery mode and reset the xorg thing to just use the default drivers and I can get back into Ubuntu with the GUI intact now. So I know how to fix the screw up, but I don't know whats causing the screw up :(

And yes, the legacy drivers are what I've been trying to install.

And thanks for the reply :)

Love Ubuntu except for this one thing that screws up the experience for me.

---

### Post by overdrank on 2008-07-06
> **RViN said:**
> When you say reconfigure xorg do you mean to tell me reset the thing and change the drivers back to the generic 'nv' drivers to get the GUI working again? (which means that I'm back to where I started and theres no way to install these damn drivers) Or is there a chance that if I run that command the Nvidia drivers might work? Because when I had that black screen problem I just went into recovery mode and reset the xorg thing to just use the default drivers and I can get back into Ubuntu with the GUI intact now. So I know how to fix the screw up, but I don't know whats causing the screw up :(

And yes, the legacy drivers are what I've been trying to install.

And thanks for the reply :)

Love Ubuntu except for this one thing that screws up the experience for me.

Ok I guess I am confused as to what driver you are trying to install. I had that model card on a laptop with feisty and on it and the drivers were installed by default and the only issue was 3d support.

---

### Post by RViN on 2008-07-07
> **overdrank said:**
> Ok I guess I am confused as to what driver you are trying to install. I had that model card on a laptop with feisty and on it and the drivers were installed by default and the only issue was 3d support.

I'm trying to install the Nvidia drivers for it, which don't seem to work.

With the default open source drivers it works, but there is no 3D support.

---

### Post by cariboo on 2008-07-07
That is a fairly old video card, I don't think it has enough video ram to use the latest driver and all the whiz bang effects. I think you are going to stay with the nv driver for now. If you can wait for intrepid to be released there may be a few surprises as far as video drivers are concerned.

Jim

---

### Post by RViN on 2008-07-29
> **cariboo907 said:**
> **That is a fairly old video card, I don't think it has enough video ram to use the latest driver** and all the whiz bang effects. I think you are going to stay with the nv driver for now. If you can wait for intrepid to be released there may be a few surprises as far as video drivers are concerned.

Jim

Yeah I know, I have Ubuntu installed on my secondary PC, a pentium 3.

Anyway I know the new drivers won't work, which is why I've been trying to install the legacy (old) drivers. Still it doesn't want to work.

---

