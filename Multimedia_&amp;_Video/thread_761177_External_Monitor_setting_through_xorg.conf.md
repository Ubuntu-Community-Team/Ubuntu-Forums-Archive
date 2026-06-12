---
title: "External Monitor setting through xorg.conf"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by kagashe on 2008-04-20
The LCD screen of my Laptop is broken and I use an external VGA monitor and using the Laptop as a Desktop.

Till Gutsy Gibbon there was no problem and the VGA monitor was automatically detected without any manual settings. I also use other distributions like Mandriva, Fedora, Puppy, DSL, Slax and no settings are required to be done in any of them.

Yesterday I downloaded PUD LXDE edition (which is based on Hardy Heron Beta) Live CD and tried it. Although the screen of Laptop is broken I could see on some patches of it that the distribution's blue desktop but the external monitor which was working showing the progress of booting (there is no splash image) becomes blank as the GDM starts. After pressing Ctrl alt F1 I could see the console with Ubuntu Live CD user.

First I tried by copying the xorg.conf file from Gutsy Gibbon install, it did not work. Then I noticed that the external monitor was configured through xrandr on Gutsy Gibbon. I tried xrandr --auto command on PUD Live CD console but it resulted into error (Can't open display).

After pressing Ctrl alt F1 on Gutsy Gibbon I tried xrandr -q on console. This also resulted into error "Can't open display". This means xrandr command does not work in console even on Gutsy Gibbon (HD install).

Please note that xrandr is working on Gutsy Gibbon Desktiop Terminal and the output is as follows:
> $ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right) 270mm x 200mm
   1280x768       60.0  
   1152x768       54.8  
   1024x768       60.0* 
   800x600        75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     60.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

I tried to do the above configuration in xorg.conf file of Gutsy Gibbon but could not succeed.

Please help me to write the above configuration in xorg.conf of Gutsy Gibbon. If it works on Gutsy Gibbon, I will copy it on PUD Live CD and see whether I can make the external monitor work there.

kagashe

---

### Post by colo on 2008-04-21
Try issung
```
DISPLAY=":0.0" xrandr --auto
```
on the text-mode VT; this should make xrandr control your primary X-Display and invoke its magic there correctly.

RANDR 1.2 (which enabled all the --auto- and modeswitching- and output-hotplugging-goodness is available since 7.10, I believe, and all distributions based on this or any later Ubuntu version.

---

### Post by kagashe on 2008-04-21
> **colo said:**
> Try issung
```
DISPLAY=":0.0" xrandr --auto
```
on the text-mode VT; this should make xrandr control your primary X-Display and invoke its magic there correctly.

RANDR 1.2 (which enabled all the --auto- and modeswitching- and output-hotplugging-goodness is available since 7.10, I believe, and all distributions based on this or any later Ubuntu version.I had tried "xrandr --auto" which gives error "Can't open display".
When I tried your command it gives error "Can't open display 0.0"

Please note that even on Gutsy install if you exit to console by pressing Ctrl Alt F1 and give any commands using "xrandr" it gives the same error "Can't open display".

xrandr works only when you open a terminal on the desktop.

kagashe

---

### Post by kagashe on 2008-05-10
The correct command is:
> xrandr -d :0 -q

I installed Ubuntu Hardy Heron and there was same problem. Finally, I could resolve it by writing xorg.conf file and using vesa driver. See my post [here]("http://ubuntuforums.org/showpost.php?p=4925380&postcount=891").

kagashe

---

### Post by RadenMu'az on 2008-06-28
I have a Compaq laptop that is 'misuse' as a desktop computer as the screen is damaged. Things are okay with Feisty. But on Hardy, the external monitor goes blank (no signal).

I tried to replace xorg server and ati driver on Xubuntu Hardy alternate installation but broke the system in the end.

So in Fedora LiveCD (have deleted Xubuntu iso because of running out of space),
I went to runlevel 3,
tried 'startx' on tty1,
ctrl-alt-F2 to swith tty2,
export DISPLAY=:0,
xrandr,

and got some output that says external monitor is connected, but hasn't set up the resolution. That's why it's blank.

When trying to change the resolution, cloning displays, etc,
I got this:
xrandr: configure crtc 1 failed.

how do I fix this?

I have no trouble whatsoever running TinyMe 2008. Maybe because it use vesa driver and xorg-server 1.3

---

### Post by kagashe on 2008-06-28
> **RadenMu'az said:**
> I have a Compaq laptop that is 'misuse' as a desktop computer as the screen is damaged. Things are okay with Feisty. But on Hardy, the external monitor goes blank (no signal).

I tried to replace xorg server and ati driver on Xubuntu Hardy alternate installation but broke the system in the end.

So in Fedora LiveCD (have deleted Xubuntu iso because of running out of space),
I went to runlevel 3,
tried 'startx' on tty1,
ctrl-alt-F2 to swith tty2,
export DISPLAY=:0,
xrandr,

and got some output that says external monitor is connected, but hasn't set up the resolution. That's why it's blank.

When trying to change the resolution, cloning displays, etc,
I got this:
xrandr: configure crtc 1 failed.

how do I fix this?

I have no trouble whatsoever running TinyMe 2008. Maybe because it use vesa driver and xorg-server 1.3If you would like to install Ubuntu or Xubuntu Hardy Heron proceed as follows:
1. Install Ubuntu/Xubuntu Hardy Heron.
2. When you boot you will get blank screen, press Ctrl Alt F1 and login to console and remove the ati driver with following command:
> sudo apt-get remove xserver-xorg-video-ati

Now reboot:
> sudo reboot
3. Ubuntu/Xubuntu Hardy will automagically use vesa driver in the absence of ati driver and you will not get blank screen.
4. You can continue to use vesa driver or download the following drivers from Debian Sid and install through dpkg:
xserver-xorg-video-ati_6.8.192-1_i386.deb
xserver-xorg-video-mach64_6.8.0-1_i386.deb
xserver-xorg-video-r128_6.8.0-1_i386
xserver-xorg-video-radeon_6.8.192-1_i386

Please note that the first driver (ati) has a dependency on others, so install them first and then ati.
5. Everything works fine with the above drivers, since the external monitor bug has been removed.

---

### Post by RadenMu'az on 2008-07-21
I've just uninstalled Xubuntu a month ago after reading your reply.
:( sheesh.

I'll find/download the iso tried it later
Thanks for that great idea

---

