---
title: "Can't set up a wide screen resolution"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by pochu on 2006-11-01
Hello

I have a new laptop, an Acer aspire 1640Z, with an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller, and a wide-screen with 1280*800 px resolution (16:10). When I installed the final release of Edgy Eft, the installer configured the monitor to a 1024*768 px resolution. And if I go to System>Preferences>Screen Resolution, I only can choose 1024*768, 800*600 and 640*480 px.

The /etc/X11/xorg.conf seems to be fine, but I have this in /var/log/Xorg.0.log

```
(WW) I810(0): config file hsync range 30-75kHz not within DDC hsync ranges.
(WW) I810(0): config file vrefresh range 30-60Hz not within DDC vrefresh ranges.
(II) I810(0): Generic Monitor: Using hsync range of 30.00-75.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 30.00-60.00 Hz
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
```

As you can see, the driver I have is the i810.

Please help me to set up my screen. If you need some information (such as the complete /etc/X11/xorg.conf, /var/log/Xorg.0.log or any other info) let me know.

Thanks
Pochu

P.S.: I have write a feature in launchpad about the wide-screens resolution configuration, which should be detected automatically.
[https://features.launchpad.net/distros/ubuntu/+spec/wide-screen-resolution](https://features.launchpad.net/distros/ubuntu/+spec/wide-screen-resolution)

---

### Post by xp_newbie on 2006-11-01
Using "Start Menu", select System | Administration | Synaptic Package Manager
> Settings | Repositories [Add]
   > Community maintained (Universe) [Add]
   > Reload, download and Install the "915resolution" package.

Using "Start Menu", select Applications | Accessories | Terminal
and type:

 sudo 915resolution -l
 > Your laptop's 1200x800 @ 32 bit mode will show something like "5c".

Then edit 915resolution's config file:

  sudo gedit /etc/default/915resolution

 > Change MODE from "auto" to "5c" and fill XRESO=1280, YRESO=800.

Save the file, Ctrl+Alt+Backspace, X starts again - 1200x800 at its glory.

HTH,
Alex

---

### Post by DannyG on 2006-11-07
Excellent howto, worked a treat!

Thanks,

Daniel.

---

### Post by sudipta_cht on 2006-11-17
Ok... I was running into stretched screens with my Ubuntu 6.06 on the Dell 6400 inspiron laptop, and then I found nirvana by going to this link: [http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

I had figured that I had an ATI graphics accelerator card but did not know how to configure that on linux. After downloading the driver, I installed it and then ran 

aticonfig --initial

And then rebooted the machine because it looked like some kernel modules were played around with by that. And now things go like a breeze on my laptop. The TUX ROCKS!! :)

---

### Post by xDieStarDiex on 2007-03-08
Ok this worked...but when I restart my notebook it reverts to the old settings. CTRL+ALT+Backspace restores the new settings but it gets annoying having to do that after every restart.

Is there any fix to that?

Sorry me==noob.

---

### Post by wazesz on 2007-03-17
> **xp_newbie said:**
> Using "Start Menu", select System | Administration | 

 sudo 915resolution -l
 > Your laptop's 1200x800 @ 32 bit mode will show something like "5c".

HTH,
Alex

i get an error when i typed 915resolution -l

this is the error:

desktop:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 29a08086
Please report this problem to [email]stomljen@yahoo.com[/email]


do i have the problem with the driver? im using the i810 driver..my computer is the hp A1640N using the Graphic Media Accelerator(GMA) 3000 graphic..anyone help? thanx in advance.

---

### Post by xDieStarDiex on 2007-06-18
I'm still having the same problem I was having with it reverting to the old resolution after I reboot. When I restart X it seems to be ok. Any idea what the problem could be?

---

### Post by Gremlinzzz on 2007-06-18
gateway 1440x 900 res  wide 19; screen this worked for me 
sudo apt-get install xserver-xorg-video-intel
reboot the check your resolution

---

### Post by xDieStarDiex on 2007-06-21
> **Gremlinzzz said:**
> gateway 1440x 900 res  wide 19; screen this worked for me 
sudo apt-get install xserver-xorg-video-intel
reboot the check your resolution

Worked like a charm, thank you very much for your help.

---

