---
title: "I can't Set My monitor over 640 x480 resolution"
date: 2008-11-30
forum: Multimedia Software
---

### Post by salem80 on 2008-11-30
hi every one 
I have LG FLATRON 775FT 17" CRT Monitor
And Nvidia Geforce 7600GS Graphic card 
this is the installed Driver (before i install it i was had no problem with res).

[IMG]http://xs233.xs.to/xs233/08480/harwaredriver692.jpg[/IMG]

and this is Max resolution i can get :confused:

[IMG]http://xs233.xs.to/xs233/08480/max_resolution781.jpg[/IMG]

I'm  use Ubuntu 8.04-  Hardy Heron
GNOME 2.22.3

---

### Post by brigadoon on 2008-11-30
The problem may be that the driver's display resolution does not match the resolution of the actual CRT display. This is a NVIDIA driver issue not a Ubuntu issue. I was able to correct the problem with my display by creating a custom EDID file used by the NVIDIA driver to communicate to the display. You can find the details of my fix at the following link...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Since you have a different NVIDIA driver and display you shall have to modify the instructions to fit your display resolution.

---

### Post by salem80 on 2008-11-30
> **brigadoon said:**
> The problem may be that the driver's display resolution does not match the resolution of the actual CRT display. This is a NVIDIA driver issue not a Ubuntu issue. I was able to correct the problem with my display by creating a custom EDID file used by the NVIDIA driver to communicate to the display. You can find the details of my fix at the following link...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Since you have a different NVIDIA driver and display you shall have to modify the instructions to fit your display resolution.
after i read 
> 4) After the reboot open the NVIDIA utility from System/Administration/NVIDIA X Server Settings. Go to the DFP-0 - (NVIDIA Default Flat Panel) tab and in the right side window select Aquire EDID. What happens here is the Flat Panel configuration gets exported in a binary format. This is where the hex editor comes in. 
You can load one through the Synaptic Package Manager. 
The problem is that the driver's display resolution does not match the resolution of the actual Flat Panel display. Thanks to orlo11 for the hint on fixing the display. The instructions are as follows...and i  download/Install Nvidia driver 173.14.12 from EnvyEng

[IMG]http://xs433.xs.to/xs433/08480/nvidia_driver798.jpg[/IMG]

But  i didn't  find this :-
>  Go to the DFP-0 - (NVIDIA Default Flat Panel) tab and in the right side window select Aquire EDID
how i export it  in a binary format .
to i can modify it  to fit your display resolution. their no Exploring Option on NV CP.

---

### Post by brigadoon on 2008-11-30
I have attached a screen shot of my display driver control. The appropriate tab is highlighted. The export EDID is on the lower right corner of the control window. If the option is available it should be under your CRT-0 - (CRT-0) tab. I am using a flat panel display (DFP-0). In my instructions where you see ***DFP*** replace it with ***CRT***.

---

### Post by salem80 on 2008-11-30
> **brigadoon said:**
> I have attached a screen shot of my display driver control. The appropriate tab is highlighted. The export EDID is on the lower right corner of the control window. If the option is available it should be under your CRT-0 - (CRT-0) tab. I am using a flat panel display (DFP-0). In my instructions where you see ***DFP*** replace it with ***CRT***.
I have see th CRT 0 but not all tab was Visible  (cos the 640*480 res)
so i didn't see Aquire EDID                       on anywhere on that window .
[LEFT]i read this thead (have same issue)
[/LEFT]
[http://ubuntuforums.org/showthread.php?t=996559](http://ubuntuforums.org/showthread.php?t=996559)
and i write this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after i restart  the res back to normal but the Nv driver not work well   (no visual effect )

[IMG]http://xs233.xs.to/xs233/08480/nvidia_controller293.jpg[/IMG]


and it's not enabled from H.D

[IMG]http://xs433.xs.to/xs433/08480/nvidia_hd_254.png[/IMG]

*sorry for my bad Eng*

---

### Post by brigadoon on 2008-11-30
Ouch! running the ***sudo dpkg-reconfigure -phigh xserver-xorg*** command is a very dangerous thing to do if you are not familiar with making edits to it. I would go back to your last xorg.conf file if you have it backed up. Some devices you have may not work since the xorg.conf file that gets loaded is very basic. That is why the NVIDIA driver did not load. If you re-install the NVIDIA driver again it may add in the missing lines needed by the NVIDIA driver.

In your last post I noticed that you had three displays listed under the GPU 0 tab.
      1) Thermal Monitor
      2) PowerMizer
      3) CRT-0 - (CRT-0)

Did you look under all display devices for the Aquire EDID option? Look through all tabs in the NVIDIA X SERVER SETTINGS control program. The control program for your driver may have it in another location that is different than mine.

For my solution to be of assistance to you you need to be able to export an EDID file compatible with your driver.

---

### Post by salem80 on 2008-12-01
i have try this (from nV readme file)
exit ur x server 
```
sudo /etc/init.d/gdm stop
```install the driver (i was move an rename it to nvidia.run)i typed this
```
sudo /sh/home/salem/nvidia.run
```after it finsh and download copbtible kernen i start x server 
```
sudo /etc/init.d/gdm start 
```so i login then  restart my pc...
after that i checked  the H.D an Nv A.g.D was enabled 
But Nvidia X server Say :
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


[IMG]http://xs234.xs.to/xs234/08491/nvidi_x_server_err225.jpg[/IMG]




note every time i restart my pc  
 ubuntu message appear  to me say "" ubuntu is runing in low graphic mode
so i press continue and loging
and my Max res are 800 x 600  (and Visual effect won't be enabled :(

---

### Post by brigadoon on 2008-12-02
When you ran the ***sudo dpkg-reconfigure -phigh xserver-xorg*** command you removed your old xorg.conf file specifically configured to work with your computer and replaced it with a generic file. The generic file is most likely missing a string of text require by your NVIDIA display driver to run in GNOME. When installing the driver with the NVIDIA install utility a backup of your old xorg.conf file should be created. You should have several backups prior to running the command by now. I would revert to the xorg.conf file that you were using a few days ago that actually loaded the driver. Then see if one of the other display devices allows you to export an EDID file.

---

### Post by fermin on 2008-12-05
I had a similar problem recently with an Nvidia GeForce MX 4000 and a 15 inch Viewsonic monitor (fresh installed Ubuntu 8.10 Intrepid Ibex) and i solved it (after long and thorough study) solely by understanding how the xorg.conf file works (thanks to "man xorg.conf") and editing it with the aid of the nvidia-settings utility. What i did was open the nvidia-settings utility in super user mode with the comand:

```
sudo nvidia-settings
```in a terminal, enter password and the window should open in su mode. There in the X server settings section (the second from the top down on the left side) i adjusted my resolution to the highest available one (in my case 1024 x 768 for a 15" monitor) and let the frequency rate in Auto. Then i used the option to write the settings to the X configuration file (xorg.conf) and UNchecked the option to merge the files (since if the files were merged, doubled info would have been present for, say, the Nvidia card that i already had configured) and pushed apply or OK. Closed the nvidia-settings dialog and restart your session and that should fix the resolution problem. Nevertheless, that being solved i hit into another problem that was i had no transparencies in compiz although i did have 3D acceleration capability. To solve that i had to manually edit the xorg.conf file and add an option INSIDE the "Screen" section, that is

```
**Section "Screen"**
    Identifier    "Screen0"
    Monitor        "Monitor0"
    Device        "Device0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0" "1024x768 +0+0"   
    **Option    "AddARGBGLXVisuals"    "True"**
**EndSection**
```You must edit the file in super user mode either by terminal doing:

```
sudo nano /etc/X11/xorg.conf
```or by GUI with:

```
sudo gedit /etc/X11/xorg.conf
```I also recommend that you backup your xorg.conf file prior to doing this edit, wich you can do with:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xor&#609;.conf.backup
```

I hope that helps. ):P

---

