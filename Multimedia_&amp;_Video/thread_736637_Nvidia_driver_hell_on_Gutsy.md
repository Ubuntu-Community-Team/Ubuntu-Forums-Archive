---
title: "Nvidia driver hell on Gutsy"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by mr_plow_au on 2008-03-26
Hi all,

I am a new Ubuntu user and am a little annoyed about how hard it has been to get a simple graphics driver to work!  The scenario is as follows:

I have done a complete, new install of Ubuntu 7.10 (Gutsy) on an old IBM NetVista work station.  It has AGP graphics and I am using an old Nvidia FX5200 card. My monitor is an LG L204WT (widescreen, native 1680x1050 resolution), connected via DVI.  I tried to install the nvidia-glx-new restricted driver, but everytime I'd restart X, it would ignore the xorg.conf and use the failsafe conf instead, resulting in a resolution of 800x600...not very useful.  I then tried to install the Nvidia drivers using Envy.  According to the envy website, it now supports 7.10 gutsy!  I installed it, then did an 'dpkg-reconfigure xserver-xorg' and restarted X, only to get a lovely flashing screen!  Multiple colours, random patterns!  Very pretty, but very useless!  The same goes when I tried to install the drivers from the Nvidia website manually.  The only way I can get the graphics to work at all is to use the 'nv' driver, which manages to get the monitor working at the right resolution, but can't do any 3D effects.  I am well and truly stumped!  Can anyone give me some idea as to what might be going wrong? Please pretty please! I have wasted far to much time on this already!  Don't make me go back to CentOS!

Thanks in advance, Mr Plow!

---

### Post by ElKeBusK on 2008-03-26
Just as a guideline, be sure you cleaned any nvidia driver you may have installed untill now. use apt-get -purge and/or Synaptic uninstall features.

Once you are sure there are no old drivers installed, and before try any "exotic" solution, do the obvious: install Nvidia drivers downloaded from Nvidia site, and let them configure your desktop; was what worked for me and I had to do nothing else.

Only if a fresh drivers install doesn't work is when you must search in the forum for a solution to your problem (sticky posts use to be the threads you should read).

Finally after any major system upgrade remember purge and reinstall your nvidia drivers and never forget make a backup of the system files like xorg.conf before the upgrade.

---

### Post by wolfen69 on 2008-03-26
did you try 
```
dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace

---

### Post by mr_plow_au on 2008-03-26
> **wolfen69 said:**
> did you try 
```
dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace

I tried this.  All this did was set eht driver to 'nv' in xorg.conf :(

---

### Post by mr_plow_au on 2008-03-26
> **ElKeBusK said:**
> Just as a guideline, be sure you cleaned any nvidia driver you may have installed untill now. use apt-get -purge and/or Synaptic uninstall features.

Once you are sure there are no old drivers installed, and before try any "exotic" solution, do the obvious: install Nvidia drivers downloaded from Nvidia site, and let them configure your desktop; was what worked for me and I had to do nothing else.

Only if a fresh drivers install doesn't work is when you must search in the forum for a solution to your problem (sticky posts use to be the threads you should read).

Finally after any major system upgrade remember purge and reinstall your nvidia drivers and never forget make a backup of the system files like xorg.conf before the upgrade.

This is exactly how I started out.  Unfortunately, it hasn't been that simple :(

---

### Post by sanddgroper on 2008-03-27
Hi
I have a FX5200 card and I use the Nvidia-glx driver.
I think the Nvidia-glx-new driver is not the right one for the
FX5200 card.

Cheers
Sandy

---

### Post by eye208 on 2008-03-27
> **mr_plow_au said:**
> I tried to install the nvidia-glx-new restricted driver, but everytime I'd restart X, it would ignore the xorg.conf and use the failsafe conf instead, resulting in a resolution of 800x600...not very useful.
Does that mean you didn't use Restricted Drivers Manager to install the driver?

---

### Post by mr_plow_au on 2008-03-27
> **sanddgroper said:**
> Hi
I have a FX5200 card and I use the Nvidia-glx driver.
I think the Nvidia-glx-new driver is not the right one for the
FX5200 card.

Cheers
Sandy

Yep, I've tried that too.  Again all I get is a lovely multi-coloured flashing screen.  Pretty, but very useless!

---

### Post by mr_plow_au on 2008-03-27
> **eye208 said:**
> Does that mean you didn't use Restricted Drivers Manager to install the driver?

I tried both the Restricted Drivers Manager and manually installing.  All to no avail :(

---

### Post by Tomatz on 2008-03-27
Maby try using envy to install the nvidia drivers it downloads them from nvidia.com.

*Use this at your own risk*

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just download, install envy and run it.

It will do the rest of the work for you

---

### Post by mr_plow_au on 2008-03-27
> **Tomatz said:**
> Maby try using envy to install the nvidia drivers it downloads them from nvidia.com.

*Use this at your own risk*

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just download, install envy and run it.

It will do the rest of the work for you

As I said in my original post, I tried that :(

---

### Post by ubuntu-freak on 2008-03-27
When I installed Gutsy this week, it kept reverting to "nv" after installing the drivers with the Restricted Drivers Manager. I just kept repeatimg it each time it reverted, then I went to System>Preferences>Appearance>Effects and tried to enable them. It then told me I had to install the proprietary driver first, so I did, and it stuck this time. I then executed the "dpkg-reconfigure -phigh xserver-xorg" command and selected the correct resolution.
 
I realise this is a bit random, but don't give up with the Restricted Drivers Manager, and try to enable effects so you receive that prompt.
 
Nathan

---

### Post by sanddgroper on 2008-03-27
Hi
As I say I have no problem with my FX5200.
Do you have onboard graphics and is it disabled.
Does Xorg recognise your graphics card or does it just say generic.
What resolution are you trying to run at maybe your
graphics card cant handle the resolution you are asking for.
What do you have in System->Preferences->Appearence->Visual Effects.
Try None if it is not selected.I had problems if I recall correctly with 7.10
trying to run Compriz.
Your graphics card is ok you have had it running 3D without problems
before?.
The first thing I do on a install is install the drivers from synaptic before
I do anything else.Dont use Envy dont use restricted drivers manager.
So the last thing I can suggest is to reinstall and try using synaptic to
install the nvidia-glx drivers first if you have not tried that.

HTH
Cheers
Sandy

---

### Post by Tomatz on 2008-03-28
Have you tried:


**sudo apt-get install nvidia-glx**

then

**sudo nvidia-glx-config enable**

Its basically the same as installing them through the restricted driver manager. 

If step 1 is already done skip to step 2.

:confused:

---

### Post by ElKeBusK on 2008-03-28
Again i must encourage you to be sure you are installing the right drivers for your graphics card. I suggest go to nvidia site and download the drivers for your card and use the installer instead of ubuntu drivers (probably you will need download the legacy ones since your card is quite old). In my case is what worked right away and I had no problems. In fact my problems came from other sources (read below).

If you are not sure which drivers are the ones you must download from nvidia site use the Restricted Drivers Manager, right after shut down the desktop and run in console nvidia-xconfig --no-compose. This will create a new xorg.conf for your drivers. 

Edit the new xorg.conf file to be sure is correct as soon as you've got installed the drivers ($ sudo nano /etc/X11/xorg.conf will do the work); if in Device section you've got as driver "nv" change it to "nvidia"

If happens that you can't make your drivers work, be sure is not another device which causes your problems. The xorg.conf contains info about keyboard, mouse and monitor (along other devices you might have and gnome need configure) and if any of them is wrongly configured you will end running gnome in failsafe mode which means /etc/X11/xorg.conf.failsafe script is loaded instead /etc/X11/xorg.conf. So it is possible your drivers are correctly installed and another device is causing the problem. I tell you this because recently I ran into such case with my keyboard which was wrongly configured and I kept logging in failsafe mode until I fixed the problem but took me a day figure out that was not my nvidia drivers the source of the problem.

---

### Post by Tomatz on 2008-03-28
[edit] 

wrong thread sorry

---

### Post by Tomatz on 2008-03-28
> **ElKeBusK said:**
> Again i must encourage you to be sure you are installing the right drivers for your graphics card. I suggest go to nvidia site and download the drivers for your card and use the installer instead of ubuntu drivers (probably you will need download the legacy ones since your card is quite old). In my case is what worked right away and I had no problems. In fact my problems came from other sources (read below).

If you are not sure which drivers are the ones you must download from nvidia site use the Restricted Drivers Manager, right after shut down the desktop and run in console nvidia-xconfig --no-compose. This will create a new xorg.conf for your drivers. 

Edit the new xorg.conf file to be sure is correct as soon as you've got installed the drivers ($ sudo nano /etc/X11/xorg.conf will do the work); if in Device section you've got as driver "nv" change it to "nvidia"

If happens that you can't make your drivers work, be sure is not another device which causes your problems. The xorg.conf contains info about keyboard, mouse and monitor (along other devices you might have and gnome need configure) and if any of them is wrongly configured you will end running gnome in failsafe mode which means /etc/X11/xorg.conf.failsafe script is loaded instead /etc/X11/xorg.conf. So it is possible your drivers are correctly installed and another device is causing the problem. I tell you this because recently I ran into such case with my keyboard which was wrongly configured and I kept logging in failsafe mode until I fixed the problem but took me a day figure out that was not my nvidia drivers the source of the problem.


Mer!

Envy does this for you. It also rewrites xorg.conf :)

It wouldn't hurt if you posted xorg.conf so we could have a look though.

---

