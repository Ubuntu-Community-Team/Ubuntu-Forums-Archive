---
title: "Installing open source Radeon driver"
date: 2011-09-22
forum: Multimedia Software
---

### Post by ChrisOfBristol on 2011-09-22
System/preferences/appearance doesn't show the appropriate tab to select desktop effects. 



I have a Radeon XPRESS 200 on-board graphics card (RS400/RS480 chip) in an Asus Pundit P1-PH1 running Ubuntu 11.04 it is using the Vesa driver.

"Ubuntu Natty Installation Guide" [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide) suggests that I need to install the open source driver as my card is excluded from support from the proprietary drive. It gives a page reference to "Updated Open Source Driver PPA's". However there is no sign of a Radeon driver (not RadeonHD which is deprecated) in that list!

"Ubuntu Documentation Radeon Driver" [https://help.ubuntu.com/community/RadeonDrive](https://help.ubuntu.com/community/RadeonDrive) 
says:
"Getting better 3D support
For r300-r500 (Radeon 9500 - X2300) cards, the r300g driver is a newer 3D driver based on Gallium3D. It will become the default 3D driver in Ubuntu Natty/11.04. To try this driver now, see the xorg-edgers.
"
However there is no sign of a Radeon driver (not RadeonHD which is deprecated) in that list!

If, as it states above, it is a default driver in Natty, perhaps I just need to enable it?

Perhaps the above site is incorrect though as this site: [http://www.x.org/archive/X11R6.8.2/doc/radeon.4.html](http://www.x.org/archive/X11R6.8.2/doc/radeon.4.html) does NOT have my card in its list of supported ones.

---

### Post by ChrisOfBristol on 2011-10-03
I'll look for the answer on a different thread.

---

### Post by pme 72 on 2011-10-05
The tab to change the Desktop Effects setting was removed from Appearance Preferences in 11.04.

I enabled my integrated Xpress 200 and opened a LiveCD of 11/04. It opens with Unity. 

Enter this code into a terminal and look at your output:
 
```
glxinfo | grep render
```

Mine shows:

direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on ATI RS480
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_light_max_exponent,

I changed nothing so the default for my RS480 is Gallium. 


```

lsmod | grep drm
```

returns:

ubuntu@ubuntu:~$ lsmod | grep drm
drm_kms_helper         40745  1 radeon
drm                   180037  5 radeon,ttm,drm_kms_helper

I am not sure why you are seeing Vesa as the driver.

That site you refer to at the end of your post does not list my integrated chip set either. It appears not to have been updated in quite awhile.

---

### Post by tgalati4 on 2011-10-06
It should work out of the box according to:

[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

---

### Post by ChrisOfBristol on 2011-10-06
pme72
> **pme 72 said:**
> The tab to change the Desktop Effects setting was removed from Appearance Preferences in 11.04.
...
Enter this code into a terminal and look at your output:
...
I am not sure why you are seeing Vesa as the driver.

I installed mesa-utils then tried the commands you suggested:

```
user@computer:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on ATI RS400
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_light_max_exponent, 
user@computer:~$ lsmod | grep drm
drm_kms_helper         40745  1 radeon
drm                   184164  4 radeon,ttm,drm_kms_helper
user@computer:~$ 
```

The results look to be the same as yours, so I am left with some questions.

1) Do the results suggest that my computer is set up properly to do the effects? 

2) I have discovered elsewhere that the tab in question no longer shows in 11.04 and it is necessary to use Compizconfig instead, so I have installed it. When I select Effects in CompixConfig nothing happens.

3) I used the script from here: [HTML]http://forlong.blogage.de/entries/pages/Compiz-Check[/HTML]
to show the driver in use, perhaps this is incorrect and Vesa is not the driver in use. Is there a better way to find out which driver is in use? (I know that the correct open source driver *should have been* installed by 11.04)

---

### Post by collisionystm on 2011-10-06
Just install the official Catalyst. I know your thread calls for OpenSource, but sometimes its not the best answer.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by pme 72 on 2011-10-06
Here is code to display card and driver. There are probably others too:

```
sudo lshw -c display
```

I see your chip set is shown as an ATI RS400. Perhaps that is significant. 

Here is another script to run, this to check if your system is able to run Unity. It may be more significant.

```
/usr/lib/nux/unity_support_test -p
```

I tried it on Lucid but got no output. I guess you need to be running 11.04 in order for it to output anything. 

I also looked here:

 [http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units)

To see what version of OpenGL the RS400 series uses and it is the same as the RS480 series. Scroll down the page to IGP (X200, X11xx). Your cards specs are quite similar to mine.

Furlong's blog brings back memories. I happened upon it when I was trying to get Compiz to run in Hardy Heron with my Xpress 200.

---

### Post by pme 72 on 2011-10-06
collisionystm, 

Yes, the official Catalyst is often the best choice and for the  newest cards sometimes the only choice but my understanding is that the chip set in question is no longer supported by the Catalyst driver.

---

### Post by ChrisOfBristol on 2011-10-07
> =pme 72;11317276]Here is code to display card and driver. There are probably others too:

I had to send the output to a file as otherwise it outputs all the lines over the top of each other making it illegible.
user@computer:~$ sudo lshw -c display > /home/user/Videos/monitor
results in:

  *-display
       description: VGA compatible controller
       product: RS400 [Radeon Xpress 200]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:17 memory:d8000000-dfffffff ioport:ee00(size=256) memory:fddf0000-fddfffff memory:fdd00000-fdd1ffff

> Here is another script to run, this to check if your system is able to run Unity. It may be more significant.
user@computer:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS400
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
user@computer:~$

I don't know whether this is alright, but it is referring to RS400  and saying 'yes'. 

1) Can I assume that this means that the correct driver is installed?
2) If so, what should I check now to find out why I still can't get 'Effects'?

---

### Post by collisionystm on 2011-10-07
> **pme 72 said:**
> collisionystm, 

Yes, the official Catalyst is often the best choice and for the  newest cards sometimes the only choice but my understanding is that the chip set in question is no longer supported by the Catalyst driver.

Well that just flat out sucks. Damn you AMD and your crappy ATI brand.

---

### Post by pme 72 on 2011-10-07
It looks to me like the proper driver is installed. You should be able to use Unity. What effects can you not enable?

---

### Post by ChrisOfBristol on 2011-10-11
> **pme 72 said:**
> It looks to me like the proper driver is installed. You should be able to use Unity. What effects can you not enable?
I don't want to use Unity, rather Classic with Effects. I have installed CompizConfig, but whatever settings I change, nothing happens - no Effects/Animations or Blur Windows and no Desktop/ Desktop cube or Desktop Wall.

---

### Post by pme 72 on 2011-10-13
Your installation boots into Unity by default? That should indicate that your graphics drivers are working. You are able to boot into the Classic mode? I have yet to try the Classic mode with my integrated card. Will give it a try and get back to you. Have to go to work.

---

### Post by pme 72 on 2011-10-13
I enabled my integrated Xpress 200 and booted into a LiveCD of 11.04. It boots into Unity for me which seems to work well. I logged out with Alt+Prnt Scrn+k and logged back in with ubuntu for the user name, changed the desktop to "Classic" and just pushed enter to fill the password screen. 

In the lower right hand corner the Workspace switcher was set to Columns 2, Rows 2. The cube needs at least a couple of Columns and only one Row so I set it to Columns 4 and Rows 1. Desktop Wall then worked with Alt+Ctrl+left or right arrows. 

I loaded Advanced Desktop Effects Settings (ccsm) from Software Center. Enabling the Cube required disabling Desktop Wall and Enabling OpenGL and Composte. I also enabled Wobbly Windows. Compiz crashed. I ran ```
compiz --replace
``` in a terminal and got just a colored screen so I logged out and back in again. The cube was enabled and I could rotate it with keyboard strokes Alt+Ctrl+ arrows left or right. 

Windows opened pinned to the upper panel with no visual menu bar. I went back into CCSM and enabled Move Windows which allowed me to grab a window anywhere by holding down the Alt key and the left mouse button. Windows still mostly opened with out a menu bar but I could use the lower panel to open or close them. Wobbly Windows worked.

I did not feel comfortable in that environment but the effects I tried did work with a little tweaking. I bought a dedicated card several years ago and have had good success with it. I can not explain why desktop effects do not work with your integrated card unless for some reason the installed version works differently from the LiveCD.

---

### Post by ChrisOfBristol on 2011-10-16
I installed 11.10 on Thursday and tried again following your instructions and it has worked at last! The wobbly windows etc are quite amusing.


> **pme 72 said:**
> booted into a LiveCD of 11.04.  I logged out with Alt+Prnt Scrn+k and logged back in 
This was useful I didn't know that it was possible...

> I loaded Advanced Desktop Effects Settings
Another useful tip. I didn't know you could install things when running a live CD!

> Compiz crashed.
Mine crashed several times!
> ```
compiz --replace
```
It only started to work when I did this first. Unfortunately I have to do this every time I switch the computer on.
 
> enabled Move Windows
I did this but it still happens to some windows.



Because of the two reasons above and because I can't edit the top and bottom panels any more (I've just discovered that this can be done with [ALT] right-click) I don't think I shall stick with it. It seems a bit underdeveloped, so like you I am not comfortable with it. Thanks for the help though - at least I have been able to make an informed decision about it now I have seen the effects.

---

### Post by pme 72 on 2011-10-16
Yes, the LiveCD is neat that way as long as you can avoid a reboot. Sorry to hear that Unity is not an option. This weekend I have been runing 11.10 from the LiveCD and so far no issues but I have only used the Unity interface. 

I think Lucid 10.4 will be supported through 13.04 if you want to give that a spin. It works well for me with a Radeon HD 4550. If it was not for the 4550 I would probably have given the integrated Xpress 200 a try and installed the xorg-edgers drivers from:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

From their site I see there is a lot of development going on with that PPA. There were 111 updates added last month. 

With the Xpress 200 in Lucid suspend did not work for me with the default driver and the game SuperTuxkart was not playable. Do not know if the xorg-edgers would solve those issues or not.

---

