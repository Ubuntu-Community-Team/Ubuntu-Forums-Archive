---
title: "[SOLVED] dual monitor issue"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Mafy on 2008-04-29
I have a Dell Inspiron 6400 with an ATI X1400 video card with 1280x800 resolution and a separate 22" Dell monitor with 1680x1050 resolution.
I have used the ATI driver not Mesa.

I tried tons of ways to make the two monitors to work as a big desktop but the resolution is not kept for the monitors (it becomes 1280x800 to 1680x800). Nu success so far!

After almost a week of struggle with some previous versions of ubuntu and kubuntu I just installed the latest release ubuntu 8.04 but the issue still persist.

Is there any solution for this? Is there anything new regarding this issue? If yes can you please post a tutorial or sticky thread with the solutions?

Thank you!
Mafy

---

### Post by DJYoshaBYD on 2008-04-29
make sure everything is updated, and use the actual ATI screen config for the settings, not ubuntu's stuff.. make sure you access it as sudo, and when you make the changes, it should have a choice to write the settings to xorg.conf... Thats how my nvidia works.. I never use ATI.. NVIDIA FOR LIFE, SON!!!

But yeah... try using the ati config utility, and make sure the settings get written to xorg.conf, and you should be good...

---

### Post by Mafy on 2008-04-29
I have tried that... Using ATI config screen does not help. And does not have an option that say anything about saving to xorg.conf.

My laptop was configured with ATI... I will not make the same mistake again: no more ATI.
Since ATI co. was incorporated by AMD co., the drivers were not successfully updated... and this is the main source of issues: drivers incompatibility (merely sure the drivers were not tested at all/enough on different linux distributions).

Thanks anyway! 
Stay away from ATI... it sucks!

---

### Post by DJYoshaBYD on 2008-04-29
> **Mafy said:**
> 
Stay away from ATI... it sucks!

NVIDIA FOR LIFE!!!!!!!:guitar::guitar::guitar::guitar:

---

### Post by Mafy on 2008-04-30
Any news from the admins?
This configuration issue persists from a long time and it should be marked with highest priority on bug fixes (how a major version could be released 8.xxx without to have those issues fixed?)... it is just about a decent usage of the operating system with two monitors.

I really like ubuntu's look and feel, stability, speed and functionalities provided but those can be used only with a single monitor!

Any plans for a fix for this bug?

Thanks!
:(

---

### Post by Mafy on 2008-05-02
I really need big desktop or at least dual monitors in clone mode.
Nothing works properly.

Any news on this?

---

### Post by rroberto on 2008-05-02
Try and install the latest drivers using Envy, it might work.

---

### Post by Mafy on 2008-05-02
I have tried that. 
:(

---

### Post by MatthewAPeters on 2008-05-02
Same or similar issue.

Using Nvidia GeForce 6600GT, dual panel monitors.

After upgrade to heron, resolution dropped and twinview failed - the screens just mirrored. 

Tried Envy, which worked in Gutsy.  That didn't work.  Tried nvidia-xconfig, that didn't work.  Saw a thread where someone used the second boot option in grub - there is a function at start up there for fixing xserver.  The results of that was to make one screen work at the correct resolution, but the second showed only garbage.  Any attempt to use Screens and Graphics made things worse again.  Reboot appears to mess things up again - so I am now banking on Linux's stability and hoping not to have to reboot any time soon.

This is very annoying.  There are bug tickets:

Nidia 6600GT Drivers, never getting the right resolutions, only when booting in safe mode. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/211387](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/211387)

nvidia 6600 not supported [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/219101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/219101)
 
nvidia broken with 2.6.24-16 [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220374](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220374)

If your xconfig.org is not taking effect, please look at and/or contribute to these tickets - I am concerned that they may not get proper attention unless they get heavy contribution.

UPDATE:
 Re: dual monitor issue
Cross post: [HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron]("http://ubuntuforums.org/showthread.php?t=780777")

Don't know if this will help folks with ATI cards. But I discovered that my Nvidia card was not new, and was not legacy, but was "new legacy" I pointed out that was an oxymoron, but what can you do? The first part of my how-to shows you what you might have to look for if your video card is "mature" but not a dinosaur.

Good Luck!

---

### Post by Teloid on 2008-05-02
Try to read this - [http://ubuntuforums.org/showthread.php?t=776886](http://ubuntuforums.org/showthread.php?t=776886) . I'm NVIDIA owner, but your problems wasn't made by ATI. You will not have problems with any onboard intel chipset, but if you wanna ATI or NVIDIA power read tutorials!
To add custom screen resolution you might run "gtf" utility, and place it output into /etc/X11/xorg.conf at "Monitor" section, then at section "Screen" add your modline name to "Modes" field.
Like that:
```

Section "Monitor"
    Identifier     "Generic Monitor"
    ModeLine       "1024x768_100.00" 113.3 1024 1096 1208 1392  768 769 772 814 -hsync +vsync
    Option         "DPMS"
EndSection

```
```

Section "Screen"
    Identifier     "Monitor"
    Device         "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1024x768_100.00"
    EndSubSection
EndSection

```

---

### Post by MatthewAPeters on 2008-05-03
updated my earlier post with cross-link to how-to.

---

### Post by peakshysteria on 2008-05-03
Getting Dual-head to work

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Also, are you sure you're running the right resolution from the beginning? Try to run sudo displayconfig-gtk from a terminal to set the right resolution.

---

### Post by Mafy on 2008-05-06
I give up!
And I hope that the new Fedora release (v.9) will not have such huge issues.

Good luck to you all!

[EDIT] Fedora has some bugs regarding this, too!

---

### Post by Mafy on 2008-06-16
Finally I have managed to make dual monitors to work.
Those are the needed steps to solve this:

1. *Install the latest Ubuntu distribution* (Ubuntu 8.04 LTS Desktop Edition)
2. *RESTART*
3. *Install all system updates* (**System->Administration->Update Manager:-->Check** button)
4. *RESTART*
5. *Install EnvyNG* (**System->Administration->Synaptic Package Manager:-->Search** button with "**envyng**" string and select the first two packages (with **Mark for installation**): **envyng-core** and **envyng-gtk** and then press **Apply** button)
6. *RESTART*
7. *Install the latest ATI drivers using EnvyNG* (**Applications->System Tools->EnvyNG:-->Main-->ATI-->check the Install the ATI driver (Automatic Hardware Detection)-->Apply** button)
8. *RESTART*
9. Start the terminal (** Applications->Accessories->Terminal**) and type the following commands:
[B]sudo aticonfig --initial
sudo aticonfig --initial=dual-head --screen-layout=right[/B]
CTRL+ALT+BACKSPACE
**sudo aticonfig --dtop=horizontal**
CTRL+ALT+BACKSPACE
// now the second display will have the resolution of the main (first from the left to right) monitor (1280x800) but I need another resolution for the second monitor (1680x1050)
**sudo aticonfig --mode2=1680x1050**
10. *RESTART*

---

### Post by peakshysteria on 2008-06-16
Nice. Thanks for sharing. I'll try that out soon. At least from point 7. Can I ask you if you had your pc connected to your tv at the same time as you installed the driver with EnvyNG? Or did you connect the tv after you installed the driver before you ran aticonfig in the terminal? And what about the catalyst control center. Have you managed to get it up and running?

I'm a bit reluctant to run EnvyNG since it haven't worked before. It always mess up my resolution making me sweat for hours to get it back again. Not sure why it doesn't work for my card (since the card is supported). Strange.

---

### Post by Mafy on 2008-06-16
I had all the time both monitors connected and turned on.

I did not tried this time the Catalyst Control Center because I had many failures with it. 
Previous times it usually messed the xorg.conf and I needed to revert to original xorg.conf to restore Ubuntu because it killed the X.

As for EnvyNG... it worked for me. But you could try to install the latest version from AMD/ATI site. I am afraid to try this :) because I had enough failures. 

Good luck!

---

### Post by ricardo072 on 2008-07-22
:confused:

I have a similar problem with NVIDIA... :(
[http://ubuntuforums.org/showthread.php?t=866608](http://ubuntuforums.org/showthread.php?t=866608)
Anybody can help me ?

Thanks.

---

### Post by DouchesWild on 2008-08-20
I'm definitely having the same problems as these people, and I've gone through 4 fresh installs, and tried 4 different methods, all of them ruining my install of Ubuntu in some new and artistic manner. This was the first thing I tried to do after installing Ubuntu and it has to be one of the most discouraging things I've ever come across. 

Does anyone else have a success story for dual monitors with different resolutions on an ATI card? If my monitors were the same resolution my life would have an extra day in it. The gimped version of the CCC is no help either, in Windows everything is peachy, but it seems they took away like 80% of it's functionality.

---

