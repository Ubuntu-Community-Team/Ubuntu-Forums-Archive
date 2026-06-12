---
title: "Nvidia - HDMI output - please help!!"
date: 2008-07-13
forum: Multimedia Software
---

### Post by lover_of_sc on 2008-07-13
All,

Is it possible to get my HDMI output working in Ubuntu?

I have a HP Pavilion DV 9500 with a NGeForce 8600M GS graphics card.

I would really appreciate any help in this matter, maybe the Svideo out is the only option?

thanks.

---

### Post by xc3RnbFO8P on 2008-07-13
Did you install
**nvidia-settings** and
**nvtv** in Synaptic Package Manager

---

### Post by lover_of_sc on 2008-07-13
Oh wow, that works!!!!

Two minor problems though:

- The sound did not work though the HDMI cable - any ideas?
- Looks like there are some disturbances on the video quality when watching a movie, maybe some settings I need to change...

You are a star mate! :-D

---

### Post by xc3RnbFO8P on 2008-07-13
Not supported at the moment:
[http://www.nvnews.net/vbulletin/showthread.php?t=97993&highlight=hdmi+audio&page=3]("http://www.nvnews.net/vbulletin/showthread.php?t=97993&highlight=hdmi+audio&page=3")

> I sent this message to NVIDIA Customer Care at 11.4.2008:
I have Quadro FX 570 card on HP Compaq 8510w. I run linux/kubuntu 7.10. Everything works like charm, except I cannot pass audio through HDMI connection. Is this driver issue, or how should I solve this problem? I really need that audio, as I made final purchase decision based on HDMI connection on this laptop.

And got following reply next day:
Yes this is a driver issue. We recently implemented support for audio through HDMI and it is expected to ship in the release 177 driver when available. I suggest you periodically check our web site for driver updates to version 177.

---

### Post by lover_of_sc on 2008-07-13
Alright buddy, thank you. Lets hope that the new version will cure the problem. Thx.

---

### Post by Mushed on 2008-10-24
I installed ndtv and restarted and updated -- when i attempt to open the program nothing at all seems to happen - this also seems to happen wtih frostwrie (probably unrelated, i know).. Any advice?

-I'm running an HP DV900 with an Nivida Gforce Go 7600 trying to get the hdmi working. Also the driver is and Envy driver.

---

### Post by OpenMinded on 2011-06-06
try here:
[http://ubuntuforums.org/showthread.php?t=967023](http://ubuntuforums.org/showthread.php?t=967023)
and maybe here:
[http://wiki.linuxmce.org/index.php/Audio_over_HDMI](http://wiki.linuxmce.org/index.php/Audio_over_HDMI)

---

### Post by Xander {MP} on 2011-06-11
I have an nividia geForce 105M and I'm using the nvidia proprietary drivers, and I still and get hdmi out to a monitor to work. Any other suggestions?

Here is a terminal recording script I ran when messing with the nvidia-settings

username@terminal:~$ sudo nvidia-settings 

[sudo] password for blank: 



ERROR: Cannot open display <system name>.





ERROR: Unable to assign attribute CursorShadow specified on line 22 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowAlpha specified on line 23 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowRed specified on line 24 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowGreen specified on line 25 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowBlue specified on line 26 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowXOffset specified on line 27 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute CursorShadowYOffset specified on line 28 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute SyncToVBlank specified on line 29 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute LogAniso specified on line 30 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute FSAA specified on line 31 of configuration

       file '/home/username/.nvidia-settings-rc' (no Display connection).





ERROR: Unable to assign attribute TextureSharpen specified on line 32 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute AllowFlipping specified on line 33 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 35 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute OpenGLImageSettings specified on line 36 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 37 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute RedBrightness specified on line 38 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute GreenBrightness specified on line 39 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute BlueBrightness specified on line 40 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute RedContrast specified on line 41 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute GreenContrast specified on line 42 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute BlueContrast specified on line 43 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute RedGamma specified on line 44 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute GreenGamma specified on line 45 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute BlueGamma specified on line 46 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute DigitalVibrance specified on line 47 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute GPUScaling specified on line 48 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute OverscanCompensation specified on line 49 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute ColorSpace specified on line 50 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute ColorRange specified on line 51 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 52

       of configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute XVideoTextureContrast specified on line 53 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute XVideoTextureHue specified on line 54 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 55

       of configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).





ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line

       56 of configuration file '/home/username/.nvidia-settings-rc' (no

       Display connection).





ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 57 of

       configuration file '/home/username/.nvidia-settings-rc' (no Display

       connection).



username@terminal:~$ sudo nvidia-xconfig 



Using X configuration file: "/etc/X11/xorg.conf".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'

New X configuration file written to '/etc/X11/xorg.conf'


username@terminal:~$ sudo nvidia-xconfig [K[K[K[K[K[K[K[K[K-detector 

none



Script done on Sat 11 Jun 2011 01:38:53 AM PDT

---

