---
title: "Setting screen resolution"
date: 2012-07-02
forum: Multimedia Software
---

### Post by rickm1945 on 2012-07-02
I have a HP Laptop and after installing Ubuntu 12.04 my screen resolution is 1224 x 768 (4:3). on Windows partition the resolution is 1366 x 768 32 Bit 60Hz. My question is how can I set my resolution to 1366 x 768 32 bit 60 Hz?

---

### Post by cwsnyder on 2012-07-02
Have you read the wiki at [https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/) ?

---

### Post by cortman on 2012-07-02
It should be as easy as going to System Settings>Displays and adjusting the resolution there.

---

### Post by rickm1945 on 2012-07-02
> **cortman said:**
> It should be as easy as going to System Settings>Displays and adjusting the resolution there.
I only have two settings for my resolution. 1224x768 and 800x600. I looked in the edit and changed it to 1366x768 at60Hz and and nothing happened.

This what xrandr returned- 
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by cortman on 2012-07-02
> **rickm1945 said:**
> I only have two settings for my resolution. 1224x768 and 800x600. I looked in the edit and changed it to 1366x768 at60Hz and and nothing happened.

This what xrandr returned- 
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$

Sounds like you may need a different graphics driver- please post output of these commands:

```

lspci | grep -i vga
lshw -C video
```

Thanks!

---

### Post by cwsnyder on 2012-07-02
My monitor EDID is not read properly, so its top resolution has never been set properly with plug-n-play.  I use the guide here: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) to set my resolution.

---

### Post by rickm1945 on 2012-07-03
> **cortman said:**
> Sounds like you may need a different graphics driver- please post output of these commands:

```

lspci | grep -i vga
lshw -C video
```Thanks!
```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo lspci | grep -i vga
[sudo] password for richard: 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4000(size=64)
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```

---

### Post by cortman on 2012-07-03
> **rickm1945 said:**
> ```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo lspci | grep -i vga
[sudo] password for richard: 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:4000(size=64)
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```

Try the link given by cwsnyder; if that fixes it, great, otherwise post back. It looks like your driver should be OK.

---

### Post by rickm1945 on 2012-07-04
> **cortman said:**
> Try the link given by cwsnyder; if that fixes it, great, otherwise post back. It looks like your driver should be OK.
I followed instructions on website and here is the total output.

```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr -- newmode 
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr --addmode VGA1 1368x768_60.00
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA1"
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr --output VGA1 --mode 1366x768_60.00
xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```

It seems to be saying that 1024x768 60.00 is the highest resolution I can use. On my Windoze partition resolution is 1366x768 60Hz. I don't understand what happened when I installed Ubuntu 12.04. I had to add "nomodeset" from the live CD to be able to boot so I could install and after thee install I had to edit "Boot Options" and use "nomodeset" permanently just to boot. I had LM13 Mate installed previously and I could only boot through recovery mode. Still having the same resolution problem.

---

### Post by cortman on 2012-07-04
Going by [this info]("http://askubuntu.com/questions/135209/how-do-i-get-1366x768-resolution-on-my-hp-pavilion-g6"), it looks like you might want to downgrade your kernel.

Go to [this site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/") and download the linux-headers and the linux-image appropriate to your architecture (32 or 64 bit), as well as the linux-headers-*all.deb. Then open a terminal and run

```
sudo dpkg -i ~/Downloads/*.deb
```

This of course assumes that you don't have any other .deb files in your ~/Downloads directory- make sure you don't first.
Reboot, and from the GRUB menu, choose the 3.0 kernel. Good luck!

---

### Post by rickm1945 on 2012-07-05
> **cortman said:**
> Going by [this info]("http://askubuntu.com/questions/135209/how-do-i-get-1366x768-resolution-on-my-hp-pavilion-g6"), it looks like you might want to downgrade your kernel.

Go to [this site]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/") and download the linux-headers and the linux-image appropriate to your architecture (32 or 64 bit), as well as the linux-headers-*all.deb. Then open a terminal and run

```
sudo dkpg -i ~/Downloads/*.deb
```This of course assumes that you don't have any other .deb files in your ~/Downloads directory- make sure you don't first.
Reboot, and from the GRUB menu, choose the 3.0 kernel. Good luck!
I downloaded the files and ran the command you gave, I copied and pasted it and this is the return.
```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo dkpg -i ~/Downloads/*.deb
[sudo] password for richard: 
sudo: dkpg: command not found
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```
I have the three .deb files in my downloads directory anxiously waiting to be installed, and hopefully make my laptop enjoyable to use. I do appreciate your help.

---

### Post by cortman on 2012-07-05
> **rickm1945 said:**
> I downloaded the files and ran the command you gave, I copied and pasted it and this is the return.
```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo dkpg -i ~/Downloads/*.deb
[sudo] password for richard: 
sudo: dkpg: command not found
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
```

```
I have the three .deb files in my downloads directory anxiously waiting to be installed, and hopefully make my laptop enjoyable to use. I do appreciate your help.

Ugh. I made a typo- it's **dpkg**, not **dkpg**. Think of it as "d-package". Sorry about that!

---

### Post by rickm1945 on 2012-07-05
> **cortman said:**
> Ugh. I made a typo- it's **dpkg**, not **dkpg**. Think of it as "d-package". Sorry about that!
I should have seen the dpkg. I installed the three packages and rebooted. There was a Linux older versions selection and I choose it and it booted into Ubuntu 12.04,then my wireless network would connect, and my resolution was the same.

---

### Post by cortman on 2012-07-05
> **rickm1945 said:**
> I should have seen the dpkg. I installed the three packages and rebooted. There was a Linux older versions selection and I choose it and it booted into Ubuntu 12.04,then my wireless network would connect, and my resolution was the same.

You say your wireless would or would not connect? Are you able to change the screen resolution from Displays? What is the output (while booted into the older version) of xrandr?

---

### Post by rickm1945 on 2012-07-05
> **cortman said:**
> You say your wireless would or would not connect? Are you able to change the screen resolution from Displays? What is the output (while booted into the older version) of xrandr?
Wireless would not connect. There was no listing for my wireless to connect to. I had a listing for VPN, but that isn't my network. My laptop is being used by someone else now will have it back in a couple of minutes. I will run xrandr then.

richard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$

---

### Post by rickm1945 on 2012-07-05
ichard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
This is the same output as I had before.

---

### Post by cortman on 2012-07-05
> **rickm1945 said:**
> ichard@richard-HP-Pavilion-g6-Notebook-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
This is the same output as I had before.

Try running an Ubuntu 11.10 live CD on it and see if that gives you the correct resolution.

---

### Post by rickm1945 on 2012-07-06
> **cortman said:**
> Try running an Ubuntu 11.10 live CD on it and see if that gives you the correct resolution.
I had the same results. I guess I'll just have to leave it the way it is. I'm able to hide the panel on the left and doing so made the screen resolution look much better. For some reason Ubuntu sees my Graphics card as only being able to produce low res. settings, also it doesn't recognize my monitor as being a laptop, it list it as unknown.

---

### Post by cortman on 2012-07-06
I have a feeling this is being caused by "nomodeset" in the boot parameters- you might try removing that.

---

### Post by rickm1945 on 2012-07-07
> **cortman said:**
> I have a feeling this is being caused by "nomodeset" in the boot parameters- you might try removing that.
I had to add "nomodeset" in order to get my laptop to boot in a normal boot. When I remove "nomodeset" I have to boot into recovery mode. So are you saying to remove "nomodeset" and boot into recovery then try these different solutions? I will do that if necessary. Although I have hide the left panel and the resolution isn't that bad, 1366x768 would be better I'm sure.

---

### Post by cortman on 2012-07-09
Hi, after doing a little more looking around, I came across [this]("https://answers.launchpad.net/ubuntu/+faq/1901"). Info on how to find vertrefresh and horizsync [here]("http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/").

---

### Post by rickm1945 on 2012-07-09
> **cortman said:**
> Hi, after doing a little more looking around, I came across [this]("https://answers.launchpad.net/ubuntu/+faq/1901"). Info on how to find vertrefresh and horizsync [here]("http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/").

```

```richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo X-config:1
sudo: X-config:1: command not found
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo X-configure:1
sudo: X-configure:1: command not found
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo X -configure :1

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
Current Operating System: Linux richard-HP-Pavilion-g6-Notebook-PC 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=0274cb0f-d70e-4c0c-94af-0ed1a6700ad8 ro quiet splash nomodeset vt.handoff=7
Build Date: 26 June 2012  06:59:23AM
xorg-server 2:1.11.4-0ubuntu10.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Jul  9 09:49:06 2012
List of video drivers:
    mach64
    siliconmotion
    ati
    qxl
    trident
    openchrome
    nouveau
    ztv
    cirrus
    radeon
    sis
    neomagic
    s3
    sisusb
    r128
    savage
    mga
    geode
    vmware
    tdfx
    intel
    fbdev
    vesa
(++) Using config file: "/home/richard/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ gksu gedit ```

```

I started the second part of the instructions and I had no values to enter for replacement.

---

### Post by cwsnyder on 2012-07-22
I noticed when you set your line ```
$ xrandr --newmode
``` you did not set the parameters for your new mode.  The correct line for that entry should have been ```
$ xrandr --newmode "1368x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
``` followed by the lines ```
$ xrandr --addmode default 1368x768_60.00
$ xrandr --output default --mode 1368x768_60.00
```If *default* doesn't work, look in your xorg log files and see if the display is listed as something like CRT-1, that is ```
[  1326.420] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[  1326.423] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[  1326.423] (--) NVIDIA(0): Memory: 1048576 kBytes
[  1326.423] (--) NVIDIA(0): VideoBIOS: 62.92.63.00.10
[  1326.423] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1326.423] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1326.428] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[  1326.428] (--) NVIDIA(0):     CRT-1
[  1326.428] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[  1326.453] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1326.453] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[  1326.453] (**) NVIDIA(0):     all display devices.)
[  1326.456] (II) NVIDIA(0): Assigned Display Device: CRT-1
[  1326.456] (WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
[  1326.457] (II) NVIDIA(0): Validated modes:
[  1326.457] (II) NVIDIA(0):     "1024x768"
[  1326.457] (II) NVIDIA(0):     "640x480"
[  1326.457] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[  1326.461] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[  1326.461] (WW) NVIDIA(0):     from CRT-1's EDID.
``` Copied from another thread with a similar problem.

---

### Post by rickm1945 on 2012-07-23
> **cwsnyder said:**
> I noticed when you set your line ```
$ xrandr --newmode
``` you did not set the parameters for your new mode.  The correct line for that entry should have been ```
$ xrandr --newmode "1368x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
``` followed by the lines ```
$ xrandr --addmode default 1368x768_60.00
$ xrandr --output default --mode 1368x768_60.00
```If *default* doesn't work, look in your xorg log files and see if the display is listed as something like CRT-1, that is ```
[  1326.420] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[  1326.423] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[  1326.423] (--) NVIDIA(0): Memory: 1048576 kBytes
[  1326.423] (--) NVIDIA(0): VideoBIOS: 62.92.63.00.10
[  1326.423] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  1326.423] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1326.428] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[  1326.428] (--) NVIDIA(0):     CRT-1
[  1326.428] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[  1326.453] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1326.453] (**) NVIDIA(0):     device CRT-1 (Using EDID frequencies has been enabled on
[  1326.453] (**) NVIDIA(0):     all display devices.)
[  1326.456] (II) NVIDIA(0): Assigned Display Device: CRT-1
[  1326.456] (WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
[  1326.457] (II) NVIDIA(0): Validated modes:
[  1326.457] (II) NVIDIA(0):     "1024x768"
[  1326.457] (II) NVIDIA(0):     "640x480"
[  1326.457] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[  1326.461] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute 
[  1326.461] (WW) NVIDIA(0):     from CRT-1's EDID.
``` Copied from another thread with a similar problem.

I had to install Ubuntu again. I got a Low res. error and couldn't boot.
Refer to this post: [http://ubuntuforums.org/showthread.php?t=2031483](http://ubuntuforums.org/showthread.php?t=2031483)
I also have the boot grub set to "nomodeset" so I could use my system. If I attempt to do these things to correct my problem do I need to remove "nomodeset"? Also what is the easiest way to edit grub? I use:
gksudo gedit /etc/default/grub 
 When using this I save the changes, close the window and it ask again to save, and I save in "recently used/Default. Is this the correct way?

---

### Post by bdika on 2012-08-05
I had the original poster's problem with Linux Mint 13 which I believe is based on Ubuntu 12.04.

I have a HP Pavilion g series laptop and could not set the resolution to 1368x768 no matter what I did. I did not have that option, once Linux Mint 13 was installed. I also had to use nomodeset after the distribution was installed to keep from getting a blank screen when trying to login.

I spent the better part of a day trying to solve this problem, without any luck. What puzzled me was that with the live cd I had the correct reolution of 1368x768 but after installing the distribution to the hard drive I was stuck with 1024x768 and could not change it no matter what I tried.

When installing the distribution for the last time, I chose "Log me in automatically" instead of "Ask my password each time I log in", and the installed distribution worked. I no longer needed to use nomodeset and my screen resolution was the correct 1368x768. I believe there is some X related parameter associated with the login screen that causes the screen resolution to be fixed at a lower than optimal level. That is the only explanation I can come up with.

No login screen, no nomodeset and proper screen resolution. This is what worked for me.

Hope this helps someone else.

Bill Dika

---

### Post by rickm1945 on 2012-08-16
> **bdika said:**
> I had the original poster's problem with Linux Mint 13 which I believe is based on Ubuntu 12.04.

I have a HP Pavilion g series laptop and could not set the resolution to 1368x768 no matter what I did. I did not have that option, once Linux Mint 13 was installed. I also had to use nomodeset after the distribution was installed to keep from getting a blank screen when trying to login.

I spent the better part of a day trying to solve this problem, without any luck. What puzzled me was that with the live cd I had the correct reolution of 1368x768 but after installing the distribution to the hard drive I was stuck with 1024x768 and could not change it no matter what I tried.

When installing the distribution for the last time, I chose "Log me in automatically" instead of "Ask my password each time I log in", and the installed distribution worked. I no longer needed to use nomodeset and my screen resolution was the correct 1368x768. I believe there is some X related parameter associated with the login screen that causes the screen resolution to be fixed at a lower than optimal level. That is the only explanation I can come up with.

No login screen, no nomodeset and proper screen resolution. This is what worked for me.

Hope this helps someone else.

Bill Dika

 I appreciate your input. I install Ubuntu again but no Oscar. Even on the live CD I had 1024 x 768. So I will just have to adjust. It is not really all that bad. Too bad computer Companies like HP can't give a decent Graphics card even in a less expensive laptop. I guess most people are in bed with MS. I personally just can't deal with the non secure Windoze OS anymore.  i do prefer Linux. I have no problems with my Dell Desktop.

---

### Post by BicyclerBoy on 2012-08-17
The OP has sandybridge graphics.
The graphics adapter was showing as unclaimed.

The "best" option could be use xorg-edgers ppa to update the kernel to 3.5 & get last intel/xorg drivers.

"best" option has some risk but as you have been completely reinstalling the OS anyway..

You need to remove "nomodeset" to use xorg-edgers ; the intel driver can not load with nomodeset.

---

### Post by rickm1945 on 2012-08-29
> **BicyclerBoy said:**
> The OP has sandybridge graphics.
The graphics adapter was showing as unclaimed.

The "best" option could be use xorg-edgers ppa to update the kernel to 3.5 & get last intel/xorg drivers.

"best" option has some risk but as you have been completely reinstalling the OS anyway..

You need to remove "nomodeset" to use xorg-edgers ; the intel driver can not load with nomodeset.

Hi BicyclerBoy How do I install the xorg-edgers ppa? Does the xorg-edgers install the new drivers upon installation?Also If I remove nomodeset I will have to boot into recovery and install in recovery mode, will this create any problems for the install, and will Ubuntu 12.10, to be released in October. 2012 have these driver included in the OS? Sorry for my ignorance but I'm rather new to Linux.

---

### Post by BicyclerBoy on 2012-08-29
Have a read of:
[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The xorg-edgers ppa has a readme of sorts..
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

To Refresh package lists:
After adding a "ppa" you have to reload (synaptic) **or** if terminal apt-get:
sudo apt-get update

If you want to be cautious/careful then use simulation:
apt-get -s upgrade
(check the simulation output)
Note: can't run apt-get if synaptic is running.

To Install updates:
In synaptic click mark all updates **or** in terminal:
sudo apt-get upgrade

The xorg-edgers ppa also updates the kernel to 3.5.0-12 or later.

It should not matter if you are in recovering mode or even in a text console login (no X server no GUI & using apt-get).

Eventually these packages will get into std ubuntu (possible bug-fixes etc).

---

### Post by rickm1945 on 2012-09-08
> **BicyclerBoy said:**
> Have a read of:
[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The xorg-edgers ppa has a readme of sorts..
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

To Refresh package lists:
After adding a "ppa" you have to reload (synaptic) **or** if terminal apt-get:
sudo apt-get update

If you want to be cautious/careful then use simulation:
apt-get -s upgrade
(check the simulation output)
Note: can't run apt-get if synaptic is running.

To Install updates:
In synaptic click mark all updates **or** in terminal:
sudo apt-get upgrade

The xorg-edgers ppa also updates the kernel to 3.5.0-12 or later.

It should not matter if you are in recovering mode or even in a text console login (no X server no GUI & using apt-get).

Eventually these packages will get into std ubuntu (possible bug-fixes etc).
I got everything installed but it didn't change my graphics problem, but I lost my wireless connection. I can not connect to the Internet with my laptop now. Is there a way to install the B43 driver for broadcom w/o Internet connection, or do I need to install Ubuntu again for the 9th time?

---

### Post by BicyclerBoy on 2012-09-08
Ouch that sucks..

The later kernels break the broadcomm wifi b43 driver.
You can boot with an older kernel image:
- reboot & tap/hold down shift key
- select previous kernel image

Then you can uninstall the 3.5 image or just make the 3.2 image the grub default.
The later kernel is required for the video driver.

My Fix for the b43 driver:
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*
(network connection required)
The fix to the broadcomm wifi driver code is a couple of lines:
Attached are my notes on it..

But how is the graphics ?
Can you post your /var/log/Xorg.0.log?
You did remove the nomodeset ?

---

### Post by rickm1945 on 2012-09-09
> **BicyclerBoy said:**
> Ouch that sucks..

The later kernels break the broadcomm wifi b43 driver.
You can boot with an older kernel image:
- reboot & tap/hold down shift key
- select previous kernel image

Then you can uninstall the 3.5 image or just make the 3.2 image the grub default.
The later kernel is required for the video driver.

Fix the b43 driver:
The fix to the broadcomm wifi is a couple of lines:
Attached are my notes on it..

But how is the graphics ?


Can you post your /var/log/Xorg.0.log?
You did remove the nomodeset ?
The graphics didn't change and I just installed Ubuntu 12.04 again. I an  expert on Installing Ubuntu now. This was the 9 or 10 time. This laptop  discharges the battery about 10 to 15% over night in its case. So maybe  this Laptop is the real issue. I've been in contact with HP. Maybe time  they honor my Warranty and send me a new Laptop. Thank you for your  help with this I really do appreciate the time and effort you put forth.

---

### Post by BicyclerBoy on 2012-09-09
Almost never need to resort to reinstalling..You just needed to reboot into grub & select kernel 3.2..

It could have been useful to determine if kernel 3.5 made your battery discharge better or worse.

---

### Post by rickm1945 on 2012-09-10
I got everything back to where it was before I did all the changes. Resolution is still the same but I can live with it.

---

### Post by rickm1945 on 2012-09-10
> **BicyclerBoy said:**
> Almost never need to resort to reinstalling..You just needed to reboot into grub & select kernel 3.2..

It could have been useful to determine if kernel 3.5 made your battery discharge better or worse.

I don't know the discharge I was referring to was when I have shutdown and turned off the laptop. It discharges while off and in the carrying case. Something in the Laptop is causing the discharge and I have to make sure it is fixed or replaced before the warranty runs out.

---

### Post by rickm1945 on 2012-09-13
> **BicyclerBoy said:**
> Ouch that sucks..

The later kernels break the broadcomm wifi b43 driver.
You can boot with an older kernel image:
- reboot & tap/hold down shift key
- select previous kernel image

Then you can uninstall the 3.5 image or just make the 3.2 image the grub default.
The later kernel is required for the video driver.

My Fix for the b43 driver:
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*
(network connection required)
The fix to the broadcomm wifi driver code is a couple of lines:
Attached are my notes on it..

But how is the graphics ?
Can you post your /var/log/Xorg.0.log?
You did remove the nomodeset ?

Sorry BicyclerBoy I didn't see where you ask me to post /var/log/xorg.0.log. Here is the entire log.
```
[    16.428] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    16.428] X Protocol Version 11, Revision 0
[    16.428] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    16.428] Current Operating System: Linux RichardM 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64
[    16.428] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-30-generic root=UUID=14c32610-87a3-4051-8bdf-ae00e4a902d9 ro quiet splash nomodeset vt.handoff=7
[    16.428] Build Date: 04 August 2012  01:51:23AM
[    16.428] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    16.428] Current version of pixman: 0.24.4
[    16.428]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.428] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.428] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 13 04:49:44 2012
[    16.442] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.442] (==) No Layout section.  Using the first Screen section.
[    16.442] (==) No screen section available. Using defaults.
[    16.442] (**) |-->Screen "Default Screen Section" (0)
[    16.442] (**) |   |-->Monitor "<default monitor>"
[    16.442] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.442] (==) Automatically adding devices
[    16.442] (==) Automatically enabling devices
[    16.443] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.443]     Entry deleted from font path.
[    16.443] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.443] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.443] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.443] (II) Loader magic: 0x7f374a915b00
[    16.443] (II) Module ABI versions:
[    16.443]     X.Org ANSI C Emulation: 0.4
[    16.443]     X.Org Video Driver: 11.0
[    16.443]     X.Org XInput driver : 16.0
[    16.443]     X.Org Server Extension : 6.0
[    16.443] (--) PCI:*(0:0:2:0) 8086:0106:103c:1695 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00004000/64
[    16.443] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.443] (II) LoadModule: "extmod"
[    16.453] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.453] (II) Module extmod: vendor="X.Org Foundation"
[    16.453]     compiled for 1.11.3, module version = 1.0.0
[    16.453]     Module class: X.Org Server Extension
[    16.453]     ABI class: X.Org Server Extension, version 6.0
[    16.453] (II) Loading extension MIT-SCREEN-SAVER
[    16.453] (II) Loading extension XFree86-VidModeExtension
[    16.453] (II) Loading extension XFree86-DGA
[    16.453] (II) Loading extension DPMS
[    16.453] (II) Loading extension XVideo
[    16.453] (II) Loading extension XVideo-MotionCompensation
[    16.453] (II) Loading extension X-Resource
[    16.453] (II) LoadModule: "dbe"
[    16.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.454] (II) Module dbe: vendor="X.Org Foundation"
[    16.454]     compiled for 1.11.3, module version = 1.0.0
[    16.454]     Module class: X.Org Server Extension
[    16.454]     ABI class: X.Org Server Extension, version 6.0
[    16.454] (II) Loading extension DOUBLE-BUFFER
[    16.454] (II) LoadModule: "glx"
[    16.454] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.454] (II) Module glx: vendor="X.Org Foundation"
[    16.454]     compiled for 1.11.3, module version = 1.0.0
[    16.454]     ABI class: X.Org Server Extension, version 6.0
[    16.454] (==) AIGLX enabled
[    16.454] (II) Loading extension GLX
[    16.454] (II) LoadModule: "record"
[    16.454] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.454] (II) Module record: vendor="X.Org Foundation"
[    16.454]     compiled for 1.11.3, module version = 1.13.0
[    16.454]     Module class: X.Org Server Extension
[    16.454]     ABI class: X.Org Server Extension, version 6.0
[    16.454] (II) Loading extension RECORD
[    16.454] (II) LoadModule: "dri"
[    16.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.454] (II) Module dri: vendor="X.Org Foundation"
[    16.454]     compiled for 1.11.3, module version = 1.0.0
[    16.454]     ABI class: X.Org Server Extension, version 6.0
[    16.454] (II) Loading extension XFree86-DRI
[    16.454] (II) LoadModule: "dri2"
[    16.455] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.455] (II) Module dri2: vendor="X.Org Foundation"
[    16.455]     compiled for 1.11.3, module version = 1.2.0
[    16.455]     ABI class: X.Org Server Extension, version 6.0
[    16.455] (II) Loading extension DRI2
[    16.455] (==) Matched intel as autoconfigured driver 0
[    16.455] (==) Matched vesa as autoconfigured driver 1
[    16.455] (==) Matched fbdev as autoconfigured driver 2
[    16.455] (==) Assigned the driver to the xf86ConfigLayout
[    16.455] (II) LoadModule: "intel"
[    16.455] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.455] (II) Module intel: vendor="X.Org Foundation"
[    16.455]     compiled for 1.11.3, module version = 2.17.0
[    16.455]     Module class: X.Org Video Driver
[    16.455]     ABI class: X.Org Video Driver, version 11.0
[    16.455] (II) LoadModule: "vesa"
[    16.455] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.455] (II) Module vesa: vendor="X.Org Foundation"
[    16.455]     compiled for 1.11.3, module version = 2.3.0
[    16.455]     Module class: X.Org Video Driver
[    16.455]     ABI class: X.Org Video Driver, version 11.0
[    16.455] (II) LoadModule: "fbdev"
[    16.456] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.456] (II) Module fbdev: vendor="X.Org Foundation"
[    16.456]     compiled for 1.11.3, module version = 0.4.2
[    16.456]     ABI class: X.Org Video Driver, version 11.0
[    16.456] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    16.456] (II) VESA: driver for VESA chipsets: vesa
[    16.456] (II) FBDEV: driver for framebuffer: fbdev
[    16.456] (++) using VT number 7

[    16.458] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.458] (WW) Falling back to old probe method for fbdev
[    16.458] (II) Loading sub module "fbdevhw"
[    16.458] (II) LoadModule: "fbdevhw"
[    16.458] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.458] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.458]     compiled for 1.11.3, module version = 0.0.2
[    16.458]     ABI class: X.Org Video Driver, version 11.0
[    16.458] (II) Loading sub module "vbe"
[    16.458] (II) LoadModule: "vbe"
[    16.458] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    16.458] (II) Module vbe: vendor="X.Org Foundation"
[    16.458]     compiled for 1.11.3, module version = 1.1.0
[    16.458]     ABI class: X.Org Video Driver, version 11.0
[    16.458] (II) Loading sub module "int10"
[    16.458] (II) LoadModule: "int10"
[    16.459] (II) Loading /usr/lib/xorg/modules/libint10.so
[    16.459] (II) Module int10: vendor="X.Org Foundation"
[    16.459]     compiled for 1.11.3, module version = 1.0.0
[    16.459]     ABI class: X.Org Video Driver, version 11.0
[    16.459] (II) VESA(0): initializing int10
[    16.459] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    16.459] (II) VESA(0): VESA BIOS detected
[    16.459] (II) VESA(0): VESA VBE Version 3.0
[    16.459] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[    16.459] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[    16.459] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    16.459] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    16.459] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[    16.459] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    16.465] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    16.465] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    16.465] (==) VESA(0): RGB weight 888
[    16.465] (==) VESA(0): Default visual is TrueColor
[    16.465] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.465] (II) Loading sub module "ddc"
[    16.465] (II) LoadModule: "ddc"
[    16.465] (II) Module "ddc" already built-in
[    16.466] (II) VESA(0): VESA VBE DDC supported
[    16.466] (II) VESA(0): VESA VBE DDC Level 2
[    16.466] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    16.478] (II) VESA(0): VESA VBE DDC read successfully
[    16.478] (II) VESA(0): Manufacturer: LGD  Model: 2f2  Serial#: 0
[    16.478] (II) VESA(0): Year: 2010  Week: 0
[    16.478] (II) VESA(0): EDID Version: 1.3
[    16.478] (II) VESA(0): Digital Display Input
[    16.478] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    16.478] (II) VESA(0): Gamma: 2.20
[    16.478] (II) VESA(0): No DPMS capabilities specified
[    16.478] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.478] (II) VESA(0): First detailed timing is preferred mode
[    16.478] (II) VESA(0): redX: 0.605 redY: 0.355   greenX: 0.329 greenY: 0.579
[    16.478] (II) VESA(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    16.478] (II) VESA(0): Manufacturer's mask: 0
[    16.478] (II) VESA(0): Supported detailed timing:
[    16.478] (II) VESA(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    16.478] (II) VESA(0): h_active: 1366  h_sync: 1402  h_sync_end 1442 h_blank_end 1480 h_border: 0
[    16.478] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 780 v_border: 0
[    16.478] (II) VESA(0):  LG Display
[    16.478] (II) VESA(0):  LP156WH4-TLC1
[    16.478] (II) VESA(0): EDID (in hex):
[    16.478] (II) VESA(0):     00ffffffffffff0030e4f20200000000
[    16.478] (II) VESA(0):     00140103802213780a05859b5b549426
[    16.478] (II) VESA(0):     0e505400000001010101010101010101
[    16.478] (II) VESA(0):     010101010101121b567250000c302428
[    16.478] (II) VESA(0):     350058c2100000190000000000000000
[    16.478] (II) VESA(0):     00000000000000000000000000fe004c
[    16.478] (II) VESA(0):     4720446973706c61790a2020000000fe
[    16.478] (II) VESA(0):     004c503135365748342d544c433100ff
[    16.478] (II) VESA(0): EDID vendor "LGD", prod id 754
[    16.478] (II) VESA(0): Printing DDC gathered Modelines:
[    16.478] (II) VESA(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    16.478] (II) VESA(0): Searching for matching VESA mode(s):
[    16.479] Mode: 160 (0x0)
[    16.479]     ModeAttributes: 0x0
[    16.479]     WinAAttributes: 0x0
[    16.479]     WinBAttributes: 0x0
[    16.479]     WinGranularity: 0
[    16.479]     WinSize: 0
[    16.479]     WinASegment: 0x0
[    16.479]     WinBSegment: 0x0
[    16.479]     WinFuncPtr: 0x0
[    16.479]     BytesPerScanline: 0
[    16.479]     XResolution: 0
[    16.479]     YResolution: 0
[    16.479]     XCharSize: 0
[    16.479]     YCharSize: 0
[    16.479]     NumberOfPlanes: 0
[    16.479]     BitsPerPixel: 0
[    16.479]     NumberOfBanks: 0
[    16.479]     MemoryModel: 0
[    16.479]     BankSize: 0
[    16.479]     NumberOfImages: 0
[    16.479]     RedMaskSize: 0
[    16.479]     RedFieldPosition: 0
[    16.479]     GreenMaskSize: 0
[    16.479]     GreenFieldPosition: 0
[    16.479]     BlueMaskSize: 0
[    16.479]     BlueFieldPosition: 0
[    16.479]     RsvdMaskSize: 0
[    16.479]     RsvdFieldPosition: 0
[    16.479]     DirectColorModeInfo: 0
[    16.479]     PhysBasePtr: 0x0
[    16.479]     LinBytesPerScanLine: 0
[    16.479]     BnkNumberOfImagePages: 0
[    16.479]     LinNumberOfImagePages: 0
[    16.479]     LinRedMaskSize: 0
[    16.479]     LinRedFieldPosition: 0
[    16.479]     LinGreenMaskSize: 0
[    16.479]     LinGreenFieldPosition: 0
[    16.479]     LinBlueMaskSize: 0
[    16.479]     LinBlueFieldPosition: 0
[    16.479]     LinRsvdMaskSize: 0
[    16.479]     LinRsvdFieldPosition: 0
[    16.479]     MaxPixelClock: 0
[    16.479] Mode: 161 (0x0)
[    16.479]     ModeAttributes: 0x0
[    16.479]     WinAAttributes: 0x0
[    16.479]     WinBAttributes: 0x0
[    16.479]     WinGranularity: 0
[    16.479]     WinSize: 0
[    16.479]     WinASegment: 0x0
[    16.479]     WinBSegment: 0x0
[    16.479]     WinFuncPtr: 0x0
[    16.479]     BytesPerScanline: 0
[    16.479]     XResolution: 0
[    16.479]     YResolution: 0
[    16.479]     XCharSize: 0
[    16.479]     YCharSize: 0
[    16.479]     NumberOfPlanes: 0
[    16.479]     BitsPerPixel: 0
[    16.479]     NumberOfBanks: 0
[    16.479]     MemoryModel: 0
[    16.479]     BankSize: 0
[    16.479]     NumberOfImages: 0
[    16.479]     RedMaskSize: 0
[    16.479]     RedFieldPosition: 0
[    16.479]     GreenMaskSize: 0
[    16.479]     GreenFieldPosition: 0
[    16.479]     BlueMaskSize: 0
[    16.479]     BlueFieldPosition: 0
[    16.479]     RsvdMaskSize: 0
[    16.479]     RsvdFieldPosition: 0
[    16.479]     DirectColorModeInfo: 0
[    16.479]     PhysBasePtr: 0x0
[    16.479]     LinBytesPerScanLine: 0
[    16.479]     BnkNumberOfImagePages: 0
[    16.479]     LinNumberOfImagePages: 0
[    16.479]     LinRedMaskSize: 0
[    16.479]     LinRedFieldPosition: 0
[    16.479]     LinGreenMaskSize: 0
[    16.479]     LinGreenFieldPosition: 0
[    16.479]     LinBlueMaskSize: 0
[    16.479]     LinBlueFieldPosition: 0
[    16.479]     LinRsvdMaskSize: 0
[    16.479]     LinRsvdFieldPosition: 0
[    16.479]     MaxPixelClock: 0
[    16.479] Mode: 162 (0x0)
[    16.479]     ModeAttributes: 0x0
[    16.479]     WinAAttributes: 0x0
[    16.479]     WinBAttributes: 0x0
[    16.479]     WinGranularity: 0
[    16.479]     WinSize: 0
[    16.479]     WinASegment: 0x0
[    16.479]     WinBSegment: 0x0
[    16.479]     WinFuncPtr: 0x0
[    16.479]     BytesPerScanline: 0
[    16.479]     XResolution: 0
[    16.479]     YResolution: 0
[    16.479]     XCharSize: 0
[    16.479]     YCharSize: 0
[    16.479]     NumberOfPlanes: 0
[    16.479]     BitsPerPixel: 0
[    16.479]     NumberOfBanks: 0
[    16.479]     MemoryModel: 0
[    16.479]     BankSize: 0
[    16.479]     NumberOfImages: 0
[    16.479]     RedMaskSize: 0
[    16.479]     RedFieldPosition: 0
[    16.479]     GreenMaskSize: 0
[    16.479]     GreenFieldPosition: 0
[    16.479]     BlueMaskSize: 0
[    16.479]     BlueFieldPosition: 0
[    16.479]     RsvdMaskSize: 0
[    16.479]     RsvdFieldPosition: 0
[    16.479]     DirectColorModeInfo: 0
[    16.479]     PhysBasePtr: 0x0
[    16.479]     LinBytesPerScanLine: 0
[    16.479]     BnkNumberOfImagePages: 0
[    16.479]     LinNumberOfImagePages: 0
[    16.479]     LinRedMaskSize: 0
[    16.479]     LinRedFieldPosition: 0
[    16.479]     LinGreenMaskSize: 0
[    16.479]     LinGreenFieldPosition: 0
[    16.479]     LinBlueMaskSize: 0
[    16.479]     LinBlueFieldPosition: 0
[    16.479]     LinRsvdMaskSize: 0
[    16.479]     LinRsvdFieldPosition: 0
[    16.479]     MaxPixelClock: 0
[    16.480] Mode: 163 (0x0)
[    16.480]     ModeAttributes: 0x0
[    16.480]     WinAAttributes: 0x0
[    16.480]     WinBAttributes: 0x0
[    16.480]     WinGranularity: 0
[    16.480]     WinSize: 0
[    16.480]     WinASegment: 0x0
[    16.480]     WinBSegment: 0x0
[    16.480]     WinFuncPtr: 0x0
[    16.480]     BytesPerScanline: 0
[    16.480]     XResolution: 0
[    16.480]     YResolution: 0
[    16.480]     XCharSize: 0
[    16.480]     YCharSize: 0
[    16.480]     NumberOfPlanes: 0
[    16.480]     BitsPerPixel: 0
[    16.480]     NumberOfBanks: 0
[    16.480]     MemoryModel: 0
[    16.480]     BankSize: 0
[    16.480]     NumberOfImages: 0
[    16.480]     RedMaskSize: 0
[    16.480]     RedFieldPosition: 0
[    16.480]     GreenMaskSize: 0
[    16.480]     GreenFieldPosition: 0
[    16.480]     BlueMaskSize: 0
[    16.480]     BlueFieldPosition: 0
[    16.480]     RsvdMaskSize: 0
[    16.480]     RsvdFieldPosition: 0
[    16.480]     DirectColorModeInfo: 0
[    16.480]     PhysBasePtr: 0x0
[    16.480]     LinBytesPerScanLine: 0
[    16.480]     BnkNumberOfImagePages: 0
[    16.480]     LinNumberOfImagePages: 0
[    16.480]     LinRedMaskSize: 0
[    16.480]     LinRedFieldPosition: 0
[    16.480]     LinGreenMaskSize: 0
[    16.480]     LinGreenFieldPosition: 0
[    16.480]     LinBlueMaskSize: 0
[    16.480]     LinBlueFieldPosition: 0
[    16.480]     LinRsvdMaskSize: 0
[    16.480]     LinRsvdFieldPosition: 0
[    16.480]     MaxPixelClock: 0
[    16.480] Mode: 164 (0x0)
[    16.480]     ModeAttributes: 0x0
[    16.480]     WinAAttributes: 0x0
[    16.480]     WinBAttributes: 0x0
[    16.480]     WinGranularity: 0
[    16.480]     WinSize: 0
[    16.480]     WinASegment: 0x0
[    16.480]     WinBSegment: 0x0
[    16.480]     WinFuncPtr: 0x0
[    16.480]     BytesPerScanline: 0
[    16.480]     XResolution: 0
[    16.480]     YResolution: 0
[    16.480]     XCharSize: 0
[    16.480]     YCharSize: 0
[    16.480]     NumberOfPlanes: 0
[    16.480]     BitsPerPixel: 0
[    16.480]     NumberOfBanks: 0
[    16.480]     MemoryModel: 0
[    16.480]     BankSize: 0
[    16.480]     NumberOfImages: 0
[    16.480]     RedMaskSize: 0
[    16.480]     RedFieldPosition: 0
[    16.480]     GreenMaskSize: 0
[    16.480]     GreenFieldPosition: 0
[    16.480]     BlueMaskSize: 0
[    16.480]     BlueFieldPosition: 0
[    16.480]     RsvdMaskSize: 0
[    16.480]     RsvdFieldPosition: 0
[    16.480]     DirectColorModeInfo: 0
[    16.480]     PhysBasePtr: 0x0
[    16.480]     LinBytesPerScanLine: 0
[    16.480]     BnkNumberOfImagePages: 0
[    16.480]     LinNumberOfImagePages: 0
[    16.480]     LinRedMaskSize: 0
[    16.480]     LinRedFieldPosition: 0
[    16.480]     LinGreenMaskSize: 0
[    16.480]     LinGreenFieldPosition: 0
[    16.480]     LinBlueMaskSize: 0
[    16.480]     LinBlueFieldPosition: 0
[    16.480]     LinRsvdMaskSize: 0
[    16.480]     LinRsvdFieldPosition: 0
[    16.480]     MaxPixelClock: 0
[    16.480] Mode: 165 (0x0)
[    16.480]     ModeAttributes: 0x0
[    16.480]     WinAAttributes: 0x0
[    16.480]     WinBAttributes: 0x0
[    16.480]     WinGranularity: 0
[    16.480]     WinSize: 0
[    16.480]     WinASegment: 0x0
[    16.480]     WinBSegment: 0x0
[    16.480]     WinFuncPtr: 0x0
[    16.480]     BytesPerScanline: 0
[    16.480]     XResolution: 0
[    16.480]     YResolution: 0
[    16.480]     XCharSize: 0
[    16.480]     YCharSize: 0
[    16.480]     NumberOfPlanes: 0
[    16.480]     BitsPerPixel: 0
[    16.480]     NumberOfBanks: 0
[    16.480]     MemoryModel: 0
[    16.480]     BankSize: 0
[    16.480]     NumberOfImages: 0
[    16.480]     RedMaskSize: 0
[    16.480]     RedFieldPosition: 0
[    16.480]     GreenMaskSize: 0
[    16.480]     GreenFieldPosition: 0
[    16.480]     BlueMaskSize: 0
[    16.480]     BlueFieldPosition: 0
[    16.480]     RsvdMaskSize: 0
[    16.480]     RsvdFieldPosition: 0
[    16.480]     DirectColorModeInfo: 0
[    16.480]     PhysBasePtr: 0x0
[    16.480]     LinBytesPerScanLine: 0
[    16.480]     BnkNumberOfImagePages: 0
[    16.480]     LinNumberOfImagePages: 0
[    16.480]     LinRedMaskSize: 0
[    16.480]     LinRedFieldPosition: 0
[    16.480]     LinGreenMaskSize: 0
[    16.480]     LinGreenFieldPosition: 0
[    16.480]     LinBlueMaskSize: 0
[    16.480]     LinBlueFieldPosition: 0
[    16.480]     LinRsvdMaskSize: 0
[    16.480]     LinRsvdFieldPosition: 0
[    16.480]     MaxPixelClock: 0
[    16.480] Mode: 166 (0x0)
[    16.480]     ModeAttributes: 0x0
[    16.480]     WinAAttributes: 0x0
[    16.480]     WinBAttributes: 0x0
[    16.480]     WinGranularity: 0
[    16.480]     WinSize: 0
[    16.480]     WinASegment: 0x0
[    16.480]     WinBSegment: 0x0
[    16.480]     WinFuncPtr: 0x0
[    16.480]     BytesPerScanline: 0
[    16.481]     XResolution: 0
[    16.481]     YResolution: 0
[    16.481]     XCharSize: 0
[    16.481]     YCharSize: 0
[    16.481]     NumberOfPlanes: 0
[    16.481]     BitsPerPixel: 0
[    16.481]     NumberOfBanks: 0
[    16.481]     MemoryModel: 0
[    16.481]     BankSize: 0
[    16.481]     NumberOfImages: 0
[    16.481]     RedMaskSize: 0
[    16.481]     RedFieldPosition: 0
[    16.481]     GreenMaskSize: 0
[    16.481]     GreenFieldPosition: 0
[    16.481]     BlueMaskSize: 0
[    16.481]     BlueFieldPosition: 0
[    16.481]     RsvdMaskSize: 0
[    16.481]     RsvdFieldPosition: 0
[    16.481]     DirectColorModeInfo: 0
[    16.481]     PhysBasePtr: 0x0
[    16.481]     LinBytesPerScanLine: 0
[    16.481]     BnkNumberOfImagePages: 0
[    16.481]     LinNumberOfImagePages: 0
[    16.481]     LinRedMaskSize: 0
[    16.481]     LinRedFieldPosition: 0
[    16.481]     LinGreenMaskSize: 0
[    16.481]     LinGreenFieldPosition: 0
[    16.481]     LinBlueMaskSize: 0
[    16.481]     LinBlueFieldPosition: 0
[    16.481]     LinRsvdMaskSize: 0
[    16.481]     LinRsvdFieldPosition: 0
[    16.481]     MaxPixelClock: 0
[    16.481] Mode: 167 (0x0)
[    16.481]     ModeAttributes: 0x0
[    16.481]     WinAAttributes: 0x0
[    16.481]     WinBAttributes: 0x0
[    16.481]     WinGranularity: 0
[    16.481]     WinSize: 0
[    16.481]     WinASegment: 0x0
[    16.481]     WinBSegment: 0x0
[    16.481]     WinFuncPtr: 0x0
[    16.481]     BytesPerScanline: 0
[    16.481]     XResolution: 0
[    16.481]     YResolution: 0
[    16.481]     XCharSize: 0
[    16.481]     YCharSize: 0
[    16.481]     NumberOfPlanes: 0
[    16.481]     BitsPerPixel: 0
[    16.481]     NumberOfBanks: 0
[    16.481]     MemoryModel: 0
[    16.481]     BankSize: 0
[    16.481]     NumberOfImages: 0
[    16.481]     RedMaskSize: 0
[    16.481]     RedFieldPosition: 0
[    16.481]     GreenMaskSize: 0
[    16.481]     GreenFieldPosition: 0
[    16.481]     BlueMaskSize: 0
[    16.481]     BlueFieldPosition: 0
[    16.481]     RsvdMaskSize: 0
[    16.481]     RsvdFieldPosition: 0
[    16.481]     DirectColorModeInfo: 0
[    16.481]     PhysBasePtr: 0x0
[    16.481]     LinBytesPerScanLine: 0
[    16.481]     BnkNumberOfImagePages: 0
[    16.481]     LinNumberOfImagePages: 0
[    16.481]     LinRedMaskSize: 0
[    16.481]     LinRedFieldPosition: 0
[    16.481]     LinGreenMaskSize: 0
[    16.481]     LinGreenFieldPosition: 0
[    16.481]     LinBlueMaskSize: 0
[    16.481]     LinBlueFieldPosition: 0
[    16.481]     LinRsvdMaskSize: 0
[    16.481]     LinRsvdFieldPosition: 0
[    16.481]     MaxPixelClock: 0
[    16.481] Mode: 168 (0x0)
[    16.481]     ModeAttributes: 0x0
[    16.481]     WinAAttributes: 0x0
[    16.481]     WinBAttributes: 0x0
[    16.481]     WinGranularity: 0
[    16.481]     WinSize: 0
[    16.481]     WinASegment: 0x0
[    16.481]     WinBSegment: 0x0
[    16.481]     WinFuncPtr: 0x0
[    16.481]     BytesPerScanline: 0
[    16.481]     XResolution: 0
[    16.481]     YResolution: 0
[    16.481]     XCharSize: 0
[    16.481]     YCharSize: 0
[    16.481]     NumberOfPlanes: 0
[    16.481]     BitsPerPixel: 0
[    16.481]     NumberOfBanks: 0
[    16.481]     MemoryModel: 0
[    16.481]     BankSize: 0
[    16.481]     NumberOfImages: 0
[    16.481]     RedMaskSize: 0
[    16.481]     RedFieldPosition: 0
[    16.481]     GreenMaskSize: 0
[    16.481]     GreenFieldPosition: 0
[    16.481]     BlueMaskSize: 0
[    16.481]     BlueFieldPosition: 0
[    16.481]     RsvdMaskSize: 0
[    16.481]     RsvdFieldPosition: 0
[    16.481]     DirectColorModeInfo: 0
[    16.481]     PhysBasePtr: 0x0
[    16.481]     LinBytesPerScanLine: 0
[    16.481]     BnkNumberOfImagePages: 0
[    16.481]     LinNumberOfImagePages: 0
[    16.481]     LinRedMaskSize: 0
[    16.481]     LinRedFieldPosition: 0
[    16.481]     LinGreenMaskSize: 0
[    16.481]     LinGreenFieldPosition: 0
[    16.481]     LinBlueMaskSize: 0
[    16.481]     LinBlueFieldPosition: 0
[    16.481]     LinRsvdMaskSize: 0
[    16.481]     LinRsvdFieldPosition: 0
[    16.481]     MaxPixelClock: 0
[    16.481] Mode: 169 (0x0)
[    16.481]     ModeAttributes: 0x0
[    16.481]     WinAAttributes: 0x0
[    16.481]     WinBAttributes: 0x0
[    16.481]     WinGranularity: 0
[    16.481]     WinSize: 0
[    16.481]     WinASegment: 0x0
[    16.481]     WinBSegment: 0x0
[    16.481]     WinFuncPtr: 0x0
[    16.481]     BytesPerScanline: 0
[    16.481]     XResolution: 0
[    16.481]     YResolution: 0
[    16.481]     XCharSize: 0
[    16.481]     YCharSize: 0
[    16.481]     NumberOfPlanes: 0
[    16.481]     BitsPerPixel: 0
[    16.481]     NumberOfBanks: 0
[    16.481]     MemoryModel: 0
[    16.481]     BankSize: 0
[    16.481]     NumberOfImages: 0
[    16.481]     RedMaskSize: 0
[    16.481]     RedFieldPosition: 0
[    16.481]     GreenMaskSize: 0
[    16.481]     GreenFieldPosition: 0
[    16.482]     BlueMaskSize: 0
[    16.482]     BlueFieldPosition: 0
[    16.482]     RsvdMaskSize: 0
[    16.482]     RsvdFieldPosition: 0
[    16.482]     DirectColorModeInfo: 0
[    16.482]     PhysBasePtr: 0x0
[    16.482]     LinBytesPerScanLine: 0
[    16.482]     BnkNumberOfImagePages: 0
[    16.482]     LinNumberOfImagePages: 0
[    16.482]     LinRedMaskSize: 0
[    16.482]     LinRedFieldPosition: 0
[    16.482]     LinGreenMaskSize: 0
[    16.482]     LinGreenFieldPosition: 0
[    16.482]     LinBlueMaskSize: 0
[    16.482]     LinBlueFieldPosition: 0
[    16.482]     LinRsvdMaskSize: 0
[    16.482]     LinRsvdFieldPosition: 0
[    16.482]     MaxPixelClock: 0
[    16.482] Mode: 16a (0x0)
[    16.482]     ModeAttributes: 0x0
[    16.482]     WinAAttributes: 0x0
[    16.482]     WinBAttributes: 0x0
[    16.482]     WinGranularity: 0
[    16.482]     WinSize: 0
[    16.482]     WinASegment: 0x0
[    16.482]     WinBSegment: 0x0
[    16.482]     WinFuncPtr: 0x0
[    16.482]     BytesPerScanline: 0
[    16.482]     XResolution: 0
[    16.482]     YResolution: 0
[    16.482]     XCharSize: 0
[    16.482]     YCharSize: 0
[    16.482]     NumberOfPlanes: 0
[    16.482]     BitsPerPixel: 0
[    16.482]     NumberOfBanks: 0
[    16.482]     MemoryModel: 0
[    16.482]     BankSize: 0
[    16.482]     NumberOfImages: 0
[    16.482]     RedMaskSize: 0
[    16.482]     RedFieldPosition: 0
[    16.482]     GreenMaskSize: 0
[    16.482]     GreenFieldPosition: 0
[    16.482]     BlueMaskSize: 0
[    16.482]     BlueFieldPosition: 0
[    16.482]     RsvdMaskSize: 0
[    16.482]     RsvdFieldPosition: 0
[    16.482]     DirectColorModeInfo: 0
[    16.482]     PhysBasePtr: 0x0
[    16.482]     LinBytesPerScanLine: 0
[    16.482]     BnkNumberOfImagePages: 0
[    16.482]     LinNumberOfImagePages: 0
[    16.482]     LinRedMaskSize: 0
[    16.482]     LinRedFieldPosition: 0
[    16.482]     LinGreenMaskSize: 0
[    16.482]     LinGreenFieldPosition: 0
[    16.482]     LinBlueMaskSize: 0
[    16.482]     LinBlueFieldPosition: 0
[    16.482]     LinRsvdMaskSize: 0
[    16.482]     LinRsvdFieldPosition: 0
[    16.482]     MaxPixelClock: 0
[    16.482] Mode: 16b (0x0)
[    16.482]     ModeAttributes: 0x0
[    16.482]     WinAAttributes: 0x0
[    16.482]     WinBAttributes: 0x0
[    16.482]     WinGranularity: 0
[    16.482]     WinSize: 0
[    16.482]     WinASegment: 0x0
[    16.482]     WinBSegment: 0x0
[    16.482]     WinFuncPtr: 0x0
[    16.482]     BytesPerScanline: 0
[    16.482]     XResolution: 0
[    16.482]     YResolution: 0
[    16.482]     XCharSize: 0
[    16.482]     YCharSize: 0
[    16.482]     NumberOfPlanes: 0
[    16.482]     BitsPerPixel: 0
[    16.482]     NumberOfBanks: 0
[    16.482]     MemoryModel: 0
[    16.482]     BankSize: 0
[    16.482]     NumberOfImages: 0
[    16.482]     RedMaskSize: 0
[    16.482]     RedFieldPosition: 0
[    16.482]     GreenMaskSize: 0
[    16.482]     GreenFieldPosition: 0
[    16.482]     BlueMaskSize: 0
[    16.482]     BlueFieldPosition: 0
[    16.482]     RsvdMaskSize: 0
[    16.482]     RsvdFieldPosition: 0
[    16.482]     DirectColorModeInfo: 0
[    16.482]     PhysBasePtr: 0x0
[    16.482]     LinBytesPerScanLine: 0
[    16.482]     BnkNumberOfImagePages: 0
[    16.482]     LinNumberOfImagePages: 0
[    16.482]     LinRedMaskSize: 0
[    16.482]     LinRedFieldPosition: 0
[    16.482]     LinGreenMaskSize: 0
[    16.482]     LinGreenFieldPosition: 0
[    16.482]     LinBlueMaskSize: 0
[    16.482]     LinBlueFieldPosition: 0
[    16.482]     LinRsvdMaskSize: 0
[    16.482]     LinRsvdFieldPosition: 0
[    16.482]     MaxPixelClock: 0
[    16.482] Mode: 16c (0x0)
[    16.482]     ModeAttributes: 0x0
[    16.482]     WinAAttributes: 0x0
[    16.482]     WinBAttributes: 0x0
[    16.482]     WinGranularity: 0
[    16.482]     WinSize: 0
[    16.482]     WinASegment: 0x0
[    16.482]     WinBSegment: 0x0
[    16.482]     WinFuncPtr: 0x0
[    16.482]     BytesPerScanline: 0
[    16.482]     XResolution: 0
[    16.482]     YResolution: 0
[    16.482]     XCharSize: 0
[    16.482]     YCharSize: 0
[    16.482]     NumberOfPlanes: 0
[    16.482]     BitsPerPixel: 0
[    16.482]     NumberOfBanks: 0
[    16.482]     MemoryModel: 0
[    16.482]     BankSize: 0
[    16.482]     NumberOfImages: 0
[    16.482]     RedMaskSize: 0
[    16.482]     RedFieldPosition: 0
[    16.482]     GreenMaskSize: 0
[    16.482]     GreenFieldPosition: 0
[    16.482]     BlueMaskSize: 0
[    16.482]     BlueFieldPosition: 0
[    16.482]     RsvdMaskSize: 0
[    16.482]     RsvdFieldPosition: 0
[    16.482]     DirectColorModeInfo: 0
[    16.482]     PhysBasePtr: 0x0
[    16.482]     LinBytesPerScanLine: 0
[    16.482]     BnkNumberOfImagePages: 0
[    16.482]     LinNumberOfImagePages: 0
[    16.482]     LinRedMaskSize: 0
[    16.482]     LinRedFieldPosition: 0
[    16.483]     LinGreenMaskSize: 0
[    16.483]     LinGreenFieldPosition: 0
[    16.483]     LinBlueMaskSize: 0
[    16.483]     LinBlueFieldPosition: 0
[    16.483]     LinRsvdMaskSize: 0
[    16.483]     LinRsvdFieldPosition: 0
[    16.483]     MaxPixelClock: 0
[    16.483] Mode: 16d (0x0)
[    16.483]     ModeAttributes: 0x0
[    16.483]     WinAAttributes: 0x0
[    16.483]     WinBAttributes: 0x0
[    16.483]     WinGranularity: 0
[    16.483]     WinSize: 0
[    16.483]     WinASegment: 0x0
[    16.483]     WinBSegment: 0x0
[    16.483]     WinFuncPtr: 0x0
[    16.483]     BytesPerScanline: 0
[    16.483]     XResolution: 0
[    16.483]     YResolution: 0
[    16.483]     XCharSize: 0
[    16.483]     YCharSize: 0
[    16.483]     NumberOfPlanes: 0
[    16.483]     BitsPerPixel: 0
[    16.483]     NumberOfBanks: 0
[    16.483]     MemoryModel: 0
[    16.483]     BankSize: 0
[    16.483]     NumberOfImages: 0
[    16.483]     RedMaskSize: 0
[    16.483]     RedFieldPosition: 0
[    16.483]     GreenMaskSize: 0
[    16.483]     GreenFieldPosition: 0
[    16.483]     BlueMaskSize: 0
[    16.483]     BlueFieldPosition: 0
[    16.483]     RsvdMaskSize: 0
[    16.483]     RsvdFieldPosition: 0
[    16.483]     DirectColorModeInfo: 0
[    16.483]     PhysBasePtr: 0x0
[    16.483]     LinBytesPerScanLine: 0
[    16.483]     BnkNumberOfImagePages: 0
[    16.483]     LinNumberOfImagePages: 0
[    16.483]     LinRedMaskSize: 0
[    16.483]     LinRedFieldPosition: 0
[    16.483]     LinGreenMaskSize: 0
[    16.483]     LinGreenFieldPosition: 0
[    16.483]     LinBlueMaskSize: 0
[    16.483]     LinBlueFieldPosition: 0
[    16.483]     LinRsvdMaskSize: 0
[    16.483]     LinRsvdFieldPosition: 0
[    16.483]     MaxPixelClock: 0
[    16.483] Mode: 16e (0x0)
[    16.483]     ModeAttributes: 0x0
[    16.483]     WinAAttributes: 0x0
[    16.483]     WinBAttributes: 0x0
[    16.483]     WinGranularity: 0
[    16.483]     WinSize: 0
[    16.483]     WinASegment: 0x0
[    16.483]     WinBSegment: 0x0
[    16.483]     WinFuncPtr: 0x0
[    16.483]     BytesPerScanline: 0
[    16.483]     XResolution: 0
[    16.483]     YResolution: 0
[    16.483]     XCharSize: 0
[    16.483]     YCharSize: 0
[    16.483]     NumberOfPlanes: 0
[    16.483]     BitsPerPixel: 0
[    16.483]     NumberOfBanks: 0
[    16.483]     MemoryModel: 0
[    16.483]     BankSize: 0
[    16.483]     NumberOfImages: 0
[    16.483]     RedMaskSize: 0
[    16.483]     RedFieldPosition: 0
[    16.483]     GreenMaskSize: 0
[    16.483]     GreenFieldPosition: 0
[    16.483]     BlueMaskSize: 0
[    16.483]     BlueFieldPosition: 0
[    16.483]     RsvdMaskSize: 0
[    16.483]     RsvdFieldPosition: 0
[    16.483]     DirectColorModeInfo: 0
[    16.483]     PhysBasePtr: 0x0
[    16.483]     LinBytesPerScanLine: 0
[    16.483]     BnkNumberOfImagePages: 0
[    16.483]     LinNumberOfImagePages: 0
[    16.483]     LinRedMaskSize: 0
[    16.483]     LinRedFieldPosition: 0
[    16.483]     LinGreenMaskSize: 0
[    16.483]     LinGreenFieldPosition: 0
[    16.483]     LinBlueMaskSize: 0
[    16.483]     LinBlueFieldPosition: 0
[    16.483]     LinRsvdMaskSize: 0
[    16.483]     LinRsvdFieldPosition: 0
[    16.483]     MaxPixelClock: 0
[    16.483] Mode: 16f (0x0)
[    16.483]     ModeAttributes: 0x0
[    16.483]     WinAAttributes: 0x0
[    16.483]     WinBAttributes: 0x0
[    16.483]     WinGranularity: 0
[    16.483]     WinSize: 0
[    16.483]     WinASegment: 0x0
[    16.483]     WinBSegment: 0x0
[    16.483]     WinFuncPtr: 0x0
[    16.483]     BytesPerScanline: 0
[    16.483]     XResolution: 0
[    16.483]     YResolution: 0
[    16.483]     XCharSize: 0
[    16.483]     YCharSize: 0
[    16.483]     NumberOfPlanes: 0
[    16.483]     BitsPerPixel: 0
[    16.483]     NumberOfBanks: 0
[    16.483]     MemoryModel: 0
[    16.483]     BankSize: 0
[    16.483]     NumberOfImages: 0
[    16.483]     RedMaskSize: 0
[    16.483]     RedFieldPosition: 0
[    16.483]     GreenMaskSize: 0
[    16.483]     GreenFieldPosition: 0
[    16.483]     BlueMaskSize: 0
[    16.483]     BlueFieldPosition: 0
[    16.483]     RsvdMaskSize: 0
[    16.483]     RsvdFieldPosition: 0
[    16.483]     DirectColorModeInfo: 0
[    16.483]     PhysBasePtr: 0x0
[    16.483]     LinBytesPerScanLine: 0
[    16.483]     BnkNumberOfImagePages: 0
[    16.483]     LinNumberOfImagePages: 0
[    16.483]     LinRedMaskSize: 0
[    16.483]     LinRedFieldPosition: 0
[    16.483]     LinGreenMaskSize: 0
[    16.483]     LinGreenFieldPosition: 0
[    16.483]     LinBlueMaskSize: 0
[    16.483]     LinBlueFieldPosition: 0
[    16.483]     LinRsvdMaskSize: 0
[    16.483]     LinRsvdFieldPosition: 0
[    16.483]     MaxPixelClock: 0
[    16.484] Mode: 170 (0x0)
[    16.484]     ModeAttributes: 0x0
[    16.484]     WinAAttributes: 0x0
[    16.484]     WinBAttributes: 0x0
[    16.484]     WinGranularity: 0
[    16.484]     WinSize: 0
[    16.484]     WinASegment: 0x0
[    16.484]     WinBSegment: 0x0
[    16.484]     WinFuncPtr: 0x0
[    16.484]     BytesPerScanline: 0
[    16.484]     XResolution: 0
[    16.484]     YResolution: 0
[    16.484]     XCharSize: 0
[    16.484]     YCharSize: 0
[    16.484]     NumberOfPlanes: 0
[    16.484]     BitsPerPixel: 0
[    16.484]     NumberOfBanks: 0
[    16.484]     MemoryModel: 0
[    16.484]     BankSize: 0
[    16.484]     NumberOfImages: 0
[    16.484]     RedMaskSize: 0
[    16.484]     RedFieldPosition: 0
[    16.484]     GreenMaskSize: 0
[    16.484]     GreenFieldPosition: 0
[    16.484]     BlueMaskSize: 0
[    16.484]     BlueFieldPosition: 0
[    16.484]     RsvdMaskSize: 0
[    16.484]     RsvdFieldPosition: 0
[    16.484]     DirectColorModeInfo: 0
[    16.484]     PhysBasePtr: 0x0
[    16.484]     LinBytesPerScanLine: 0
[    16.484]     BnkNumberOfImagePages: 0
[    16.484]     LinNumberOfImagePages: 0
[    16.484]     LinRedMaskSize: 0
[    16.484]     LinRedFieldPosition: 0
[    16.484]     LinGreenMaskSize: 0
[    16.484]     LinGreenFieldPosition: 0
[    16.484]     LinBlueMaskSize: 0
[    16.484]     LinBlueFieldPosition: 0
[    16.484]     LinRsvdMaskSize: 0
[    16.484]     LinRsvdFieldPosition: 0
[    16.484]     MaxPixelClock: 0
[    16.484] Mode: 171 (0x0)
[    16.484]     ModeAttributes: 0x0
[    16.484]     WinAAttributes: 0x0
[    16.484]     WinBAttributes: 0x0
[    16.484]     WinGranularity: 0
[    16.484]     WinSize: 0
[    16.484]     WinASegment: 0x0
[    16.484]     WinBSegment: 0x0
[    16.484]     WinFuncPtr: 0x0
[    16.484]     BytesPerScanline: 0
[    16.484]     XResolution: 0
[    16.484]     YResolution: 0
[    16.484]     XCharSize: 0
[    16.484]     YCharSize: 0
[    16.484]     NumberOfPlanes: 0
[    16.484]     BitsPerPixel: 0
[    16.484]     NumberOfBanks: 0
[    16.484]     MemoryModel: 0
[    16.484]     BankSize: 0
[    16.484]     NumberOfImages: 0
[    16.484]     RedMaskSize: 0
[    16.484]     RedFieldPosition: 0
[    16.484]     GreenMaskSize: 0
[    16.484]     GreenFieldPosition: 0
[    16.484]     BlueMaskSize: 0
[    16.484]     BlueFieldPosition: 0
[    16.484]     RsvdMaskSize: 0
[    16.484]     RsvdFieldPosition: 0
[    16.484]     DirectColorModeInfo: 0
[    16.484]     PhysBasePtr: 0x0
[    16.484]     LinBytesPerScanLine: 0
[    16.484]     BnkNumberOfImagePages: 0
[    16.484]     LinNumberOfImagePages: 0
[    16.484]     LinRedMaskSize: 0
[    16.484]     LinRedFieldPosition: 0
[    16.484]     LinGreenMaskSize: 0
[    16.484]     LinGreenFieldPosition: 0
[    16.484]     LinBlueMaskSize: 0
[    16.484]     LinBlueFieldPosition: 0
[    16.484]     LinRsvdMaskSize: 0
[    16.484]     LinRsvdFieldPosition: 0
[    16.484]     MaxPixelClock: 0
[    16.484] Mode: 13c (0x0)
[    16.484]     ModeAttributes: 0x0
[    16.484]     WinAAttributes: 0x0
[    16.484]     WinBAttributes: 0x0
[    16.484]     WinGranularity: 0
[    16.484]     WinSize: 0
[    16.484]     WinASegment: 0x0
[    16.484]     WinBSegment: 0x0
[    16.484]     WinFuncPtr: 0x0
[    16.484]     BytesPerScanline: 0
[    16.484]     XResolution: 0
[    16.484]     YResolution: 0
[    16.484]     XCharSize: 0
[    16.484]     YCharSize: 0
[    16.484]     NumberOfPlanes: 0
[    16.484]     BitsPerPixel: 0
[    16.484]     NumberOfBanks: 0
[    16.484]     MemoryModel: 0
[    16.484]     BankSize: 0
[    16.485]     NumberOfImages: 0
[    16.485]     RedMaskSize: 0
[    16.485]     RedFieldPosition: 0
[    16.485]     GreenMaskSize: 0
[    16.485]     GreenFieldPosition: 0
[    16.485]     BlueMaskSize: 0
[    16.485]     BlueFieldPosition: 0
[    16.485]     RsvdMaskSize: 0
[    16.485]     RsvdFieldPosition: 0
[    16.485]     DirectColorModeInfo: 0
[    16.485]     PhysBasePtr: 0x0
[    16.485]     LinBytesPerScanLine: 0
[    16.485]     BnkNumberOfImagePages: 0
[    16.485]     LinNumberOfImagePages: 0
[    16.485]     LinRedMaskSize: 0
[    16.485]     LinRedFieldPosition: 0
[    16.485]     LinGreenMaskSize: 0
[    16.485]     LinGreenFieldPosition: 0
[    16.485]     LinBlueMaskSize: 0
[    16.485]     LinBlueFieldPosition: 0
[    16.485]     LinRsvdMaskSize: 0
[    16.485]     LinRsvdFieldPosition: 0
[    16.485]     MaxPixelClock: 0
[    16.485] Mode: 14d (0x0)
[    16.485]     ModeAttributes: 0x0
[    16.485]     WinAAttributes: 0x0
[    16.485]     WinBAttributes: 0x0
[    16.485]     WinGranularity: 0
[    16.485]     WinSize: 0
[    16.485]     WinASegment: 0x0
[    16.485]     WinBSegment: 0x0
[    16.485]     WinFuncPtr: 0x0
[    16.485]     BytesPerScanline: 0
[    16.485]     XResolution: 0
[    16.485]     YResolution: 0
[    16.485]     XCharSize: 0
[    16.485]     YCharSize: 0
[    16.485]     NumberOfPlanes: 0
[    16.485]     BitsPerPixel: 0
[    16.485]     NumberOfBanks: 0
[    16.485]     MemoryModel: 0
[    16.485]     BankSize: 0
[    16.485]     NumberOfImages: 0
[    16.485]     RedMaskSize: 0
[    16.485]     RedFieldPosition: 0
[    16.485]     GreenMaskSize: 0
[    16.485]     GreenFieldPosition: 0
[    16.485]     BlueMaskSize: 0
[    16.485]     BlueFieldPosition: 0
[    16.485]     RsvdMaskSize: 0
[    16.485]     RsvdFieldPosition: 0
[    16.485]     DirectColorModeInfo: 0
[    16.485]     PhysBasePtr: 0x0
[    16.485]     LinBytesPerScanLine: 0
[    16.485]     BnkNumberOfImagePages: 0
[    16.485]     LinNumberOfImagePages: 0
[    16.485]     LinRedMaskSize: 0
[    16.485]     LinRedFieldPosition: 0
[    16.485]     LinGreenMaskSize: 0
[    16.485]     LinGreenFieldPosition: 0
[    16.485]     LinBlueMaskSize: 0
[    16.485]     LinBlueFieldPosition: 0
[    16.485]     LinRsvdMaskSize: 0
[    16.485]     LinRsvdFieldPosition: 0
[    16.485]     MaxPixelClock: 0
[    16.485] Mode: 15c (0x0)
[    16.485]     ModeAttributes: 0x0
[    16.485]     WinAAttributes: 0x0
[    16.485]     WinBAttributes: 0x0
[    16.485]     WinGranularity: 0
[    16.485]     WinSize: 0
[    16.485]     WinASegment: 0x0
[    16.485]     WinBSegment: 0x0
[    16.485]     WinFuncPtr: 0x0
[    16.485]     BytesPerScanline: 0
[    16.485]     XResolution: 0
[    16.485]     YResolution: 0
[    16.485]     XCharSize: 0
[    16.485]     YCharSize: 0
[    16.485]     NumberOfPlanes: 0
[    16.485]     BitsPerPixel: 0
[    16.485]     NumberOfBanks: 0
[    16.485]     MemoryModel: 0
[    16.485]     BankSize: 0
[    16.485]     NumberOfImages: 0
[    16.485]     RedMaskSize: 0
[    16.485]     RedFieldPosition: 0
[    16.485]     GreenMaskSize: 0
[    16.485]     GreenFieldPosition: 0
[    16.485]     BlueMaskSize: 0
[    16.485]     BlueFieldPosition: 0
[    16.485]     RsvdMaskSize: 0
[    16.485]     RsvdFieldPosition: 0
[    16.485]     DirectColorModeInfo: 0
[    16.485]     PhysBasePtr: 0x0
[    16.485]     LinBytesPerScanLine: 0
[    16.485]     BnkNumberOfImagePages: 0
[    16.485]     LinNumberOfImagePages: 0
[    16.485]     LinRedMaskSize: 0
[    16.485]     LinRedFieldPosition: 0
[    16.485]     LinGreenMaskSize: 0
[    16.485]     LinGreenFieldPosition: 0
[    16.485]     LinBlueMaskSize: 0
[    16.485]     LinBlueFieldPosition: 0
[    16.485]     LinRsvdMaskSize: 0
[    16.485]     LinRsvdFieldPosition: 0
[    16.485]     MaxPixelClock: 0
[    16.486] Mode: 13a (0x0)
[    16.486]     ModeAttributes: 0x0
[    16.486]     WinAAttributes: 0x0
[    16.486]     WinBAttributes: 0x0
[    16.486]     WinGranularity: 0
[    16.486]     WinSize: 0
[    16.486]     WinASegment: 0x0
[    16.486]     WinBSegment: 0x0
[    16.486]     WinFuncPtr: 0x0
[    16.486]     BytesPerScanline: 0
[    16.486]     XResolution: 0
[    16.486]     YResolution: 0
[    16.486]     XCharSize: 0
[    16.486]     YCharSize: 0
[    16.486]     NumberOfPlanes: 0
[    16.486]     BitsPerPixel: 0
[    16.486]     NumberOfBanks: 0
[    16.486]     MemoryModel: 0
[    16.486]     BankSize: 0
[    16.486]     NumberOfImages: 0
[    16.486]     RedMaskSize: 0
[    16.486]     RedFieldPosition: 0
[    16.486]     GreenMaskSize: 0
[    16.486]     GreenFieldPosition: 0
[    16.486]     BlueMaskSize: 0
[    16.486]     BlueFieldPosition: 0
[    16.486]     RsvdMaskSize: 0
[    16.486]     RsvdFieldPosition: 0
[    16.486]     DirectColorModeInfo: 0
[    16.486]     PhysBasePtr: 0x0
[    16.486]     LinBytesPerScanLine: 0
[    16.486]     BnkNumberOfImagePages: 0
[    16.486]     LinNumberOfImagePages: 0
[    16.486]     LinRedMaskSize: 0
[    16.486]     LinRedFieldPosition: 0
[    16.486]     LinGreenMaskSize: 0
[    16.486]     LinGreenFieldPosition: 0
[    16.486]     LinBlueMaskSize: 0
[    16.486]     LinBlueFieldPosition: 0
[    16.486]     LinRsvdMaskSize: 0
[    16.486]     LinRsvdFieldPosition: 0
[    16.486]     MaxPixelClock: 0
[    16.486] Mode: 14b (0x0)
[    16.486]     ModeAttributes: 0x0
[    16.486]     WinAAttributes: 0x0
[    16.486]     WinBAttributes: 0x0
[    16.486]     WinGranularity: 0
[    16.486]     WinSize: 0
[    16.486]     WinASegment: 0x0
[    16.486]     WinBSegment: 0x0
[    16.486]     WinFuncPtr: 0x0
[    16.486]     BytesPerScanline: 0
[    16.486]     XResolution: 0
[    16.486]     YResolution: 0
[    16.486]     XCharSize: 0
[    16.486]     YCharSize: 0
[    16.486]     NumberOfPlanes: 0
[    16.486]     BitsPerPixel: 0
[    16.486]     NumberOfBanks: 0
[    16.486]     MemoryModel: 0
[    16.486]     BankSize: 0
[    16.486]     NumberOfImages: 0
[    16.486]     RedMaskSize: 0
[    16.486]     RedFieldPosition: 0
[    16.486]     GreenMaskSize: 0
[    16.486]     GreenFieldPosition: 0
[    16.486]     BlueMaskSize: 0
[    16.486]     BlueFieldPosition: 0
[    16.486]     RsvdMaskSize: 0
[    16.486]     RsvdFieldPosition: 0
[    16.486]     DirectColorModeInfo: 0
[    16.486]     PhysBasePtr: 0x0
[    16.486]     LinBytesPerScanLine: 0
[    16.486]     BnkNumberOfImagePages: 0
[    16.486]     LinNumberOfImagePages: 0
[    16.486]     LinRedMaskSize: 0
[    16.486]     LinRedFieldPosition: 0
[    16.486]     LinGreenMaskSize: 0
[    16.486]     LinGreenFieldPosition: 0
[    16.486]     LinBlueMaskSize: 0
[    16.486]     LinBlueFieldPosition: 0
[    16.486]     LinRsvdMaskSize: 0
[    16.486]     LinRsvdFieldPosition: 0
[    16.486]     MaxPixelClock: 0
[    16.486] Mode: 15a (0x0)
[    16.486]     ModeAttributes: 0x0
[    16.486]     WinAAttributes: 0x0
[    16.486]     WinBAttributes: 0x0
[    16.486]     WinGranularity: 0
[    16.486]     WinSize: 0
[    16.486]     WinASegment: 0x0
[    16.486]     WinBSegment: 0x0
[    16.486]     WinFuncPtr: 0x0
[    16.486]     BytesPerScanline: 0
[    16.486]     XResolution: 0
[    16.486]     YResolution: 0
[    16.486]     XCharSize: 0
[    16.486]     YCharSize: 0
[    16.486]     NumberOfPlanes: 0
[    16.486]     BitsPerPixel: 0
[    16.486]     NumberOfBanks: 0
[    16.486]     MemoryModel: 0
[    16.486]     BankSize: 0
[    16.486]     NumberOfImages: 0
[    16.486]     RedMaskSize: 0
[    16.486]     RedFieldPosition: 0
[    16.486]     GreenMaskSize: 0
[    16.486]     GreenFieldPosition: 0
[    16.486]     BlueMaskSize: 0
[    16.486]     BlueFieldPosition: 0
[    16.486]     RsvdMaskSize: 0
[    16.486]     RsvdFieldPosition: 0
[    16.486]     DirectColorModeInfo: 0
[    16.486]     PhysBasePtr: 0x0
[    16.486]     LinBytesPerScanLine: 0
[    16.486]     BnkNumberOfImagePages: 0
[    16.486]     LinNumberOfImagePages: 0
[    16.487]     LinRedMaskSize: 0
[    16.487]     LinRedFieldPosition: 0
[    16.487]     LinGreenMaskSize: 0
[    16.487]     LinGreenFieldPosition: 0
[    16.487]     LinBlueMaskSize: 0
[    16.487]     LinBlueFieldPosition: 0
[    16.487]     LinRsvdMaskSize: 0
[    16.487]     LinRsvdFieldPosition: 0
[    16.487]     MaxPixelClock: 0
[    16.487] Mode: 107 (0x0)
[    16.487]     ModeAttributes: 0x0
[    16.487]     WinAAttributes: 0x0
[    16.487]     WinBAttributes: 0x0
[    16.487]     WinGranularity: 0
[    16.487]     WinSize: 0
[    16.487]     WinASegment: 0x0
[    16.487]     WinBSegment: 0x0
[    16.487]     WinFuncPtr: 0x0
[    16.487]     BytesPerScanline: 0
[    16.487]     XResolution: 0
[    16.487]     YResolution: 0
[    16.487]     XCharSize: 0
[    16.487]     YCharSize: 0
[    16.487]     NumberOfPlanes: 0
[    16.487]     BitsPerPixel: 0
[    16.487]     NumberOfBanks: 0
[    16.487]     MemoryModel: 0
[    16.487]     BankSize: 0
[    16.487]     NumberOfImages: 0
[    16.487]     RedMaskSize: 0
[    16.487]     RedFieldPosition: 0
[    16.487]     GreenMaskSize: 0
[    16.487]     GreenFieldPosition: 0
[    16.487]     BlueMaskSize: 0
[    16.487]     BlueFieldPosition: 0
[    16.487]     RsvdMaskSize: 0
[    16.487]     RsvdFieldPosition: 0
[    16.487]     DirectColorModeInfo: 0
[    16.487]     PhysBasePtr: 0x0
[    16.487]     LinBytesPerScanLine: 0
[    16.487]     BnkNumberOfImagePages: 0
[    16.487]     LinNumberOfImagePages: 0
[    16.487]     LinRedMaskSize: 0
[    16.487]     LinRedFieldPosition: 0
[    16.487]     LinGreenMaskSize: 0
[    16.487]     LinGreenFieldPosition: 0
[    16.487]     LinBlueMaskSize: 0
[    16.487]     LinBlueFieldPosition: 0
[    16.487]     LinRsvdMaskSize: 0
[    16.487]     LinRsvdFieldPosition: 0
[    16.487]     MaxPixelClock: 0
[    16.487] Mode: 11a (0x0)
[    16.487]     ModeAttributes: 0x0
[    16.487]     WinAAttributes: 0x0
[    16.487]     WinBAttributes: 0x0
[    16.487]     WinGranularity: 0
[    16.487]     WinSize: 0
[    16.487]     WinASegment: 0x0
[    16.487]     WinBSegment: 0x0
[    16.487]     WinFuncPtr: 0x0
[    16.487]     BytesPerScanline: 0
[    16.487]     XResolution: 0
[    16.487]     YResolution: 0
[    16.487]     XCharSize: 0
[    16.487]     YCharSize: 0
[    16.487]     NumberOfPlanes: 0
[    16.487]     BitsPerPixel: 0
[    16.487]     NumberOfBanks: 0
[    16.487]     MemoryModel: 0
[    16.487]     BankSize: 0
[    16.487]     NumberOfImages: 0
[    16.487]     RedMaskSize: 0
[    16.487]     RedFieldPosition: 0
[    16.487]     GreenMaskSize: 0
[    16.487]     GreenFieldPosition: 0
[    16.487]     BlueMaskSize: 0
[    16.487]     BlueFieldPosition: 0
[    16.487]     RsvdMaskSize: 0
[    16.487]     RsvdFieldPosition: 0
[    16.487]     DirectColorModeInfo: 0
[    16.487]     PhysBasePtr: 0x0
[    16.487]     LinBytesPerScanLine: 0
[    16.487]     BnkNumberOfImagePages: 0
[    16.487]     LinNumberOfImagePages: 0
[    16.487]     LinRedMaskSize: 0
[    16.487]     LinRedFieldPosition: 0
[    16.487]     LinGreenMaskSize: 0
[    16.487]     LinGreenFieldPosition: 0
[    16.487]     LinBlueMaskSize: 0
[    16.487]     LinBlueFieldPosition: 0
[    16.487]     LinRsvdMaskSize: 0
[    16.487]     LinRsvdFieldPosition: 0
[    16.487]     MaxPixelClock: 0
[    16.487] Mode: 11b (0x0)
[    16.487]     ModeAttributes: 0x0
[    16.487]     WinAAttributes: 0x0
[    16.487]     WinBAttributes: 0x0
[    16.487]     WinGranularity: 0
[    16.488]     WinSize: 0
[    16.488]     WinASegment: 0x0
[    16.488]     WinBSegment: 0x0
[    16.488]     WinFuncPtr: 0x0
[    16.488]     BytesPerScanline: 0
[    16.488]     XResolution: 0
[    16.488]     YResolution: 0
[    16.488]     XCharSize: 0
[    16.488]     YCharSize: 0
[    16.488]     NumberOfPlanes: 0
[    16.488]     BitsPerPixel: 0
[    16.488]     NumberOfBanks: 0
[    16.488]     MemoryModel: 0
[    16.488]     BankSize: 0
[    16.488]     NumberOfImages: 0
[    16.488]     RedMaskSize: 0
[    16.488]     RedFieldPosition: 0
[    16.488]     GreenMaskSize: 0
[    16.488]     GreenFieldPosition: 0
[    16.488]     BlueMaskSize: 0
[    16.488]     BlueFieldPosition: 0
[    16.488]     RsvdMaskSize: 0
[    16.488]     RsvdFieldPosition: 0
[    16.488]     DirectColorModeInfo: 0
[    16.488]     PhysBasePtr: 0x0
[    16.488]     LinBytesPerScanLine: 0
[    16.488]     BnkNumberOfImagePages: 0
[    16.488]     LinNumberOfImagePages: 0
[    16.488]     LinRedMaskSize: 0
[    16.488]     LinRedFieldPosition: 0
[    16.488]     LinGreenMaskSize: 0
[    16.488]     LinGreenFieldPosition: 0
[    16.488]     LinBlueMaskSize: 0
[    16.488]     LinBlueFieldPosition: 0
[    16.488]     LinRsvdMaskSize: 0
[    16.488]     LinRsvdFieldPosition: 0
[    16.488]     MaxPixelClock: 0
[    16.488] Mode: 105 (1024x768)
[    16.488]     ModeAttributes: 0x9b
[    16.488]     WinAAttributes: 0x7
[    16.488]     WinBAttributes: 0x0
[    16.488]     WinGranularity: 64
[    16.488]     WinSize: 64
[    16.488]     WinASegment: 0xa000
[    16.488]     WinBSegment: 0x0
[    16.488]     WinFuncPtr: 0xc000863f
[    16.488]     BytesPerScanline: 1024
[    16.488]     XResolution: 1024
[    16.488]     YResolution: 768
[    16.488]     XCharSize: 8
[    16.488]     YCharSize: 16
[    16.488]     NumberOfPlanes: 1
[    16.488]     BitsPerPixel: 8
[    16.488]     NumberOfBanks: 1
[    16.488]     MemoryModel: 4
[    16.488]     BankSize: 0
[    16.488]     NumberOfImages: 41
[    16.488]     RedMaskSize: 0
[    16.488]     RedFieldPosition: 0
[    16.488]     GreenMaskSize: 0
[    16.488]     GreenFieldPosition: 0
[    16.488]     BlueMaskSize: 0
[    16.488]     BlueFieldPosition: 0
[    16.488]     RsvdMaskSize: 0
[    16.488]     RsvdFieldPosition: 0
[    16.488]     DirectColorModeInfo: 0
[    16.488]     PhysBasePtr: 0xb0000000
[    16.488]     LinBytesPerScanLine: 1024
[    16.488]     BnkNumberOfImagePages: 41
[    16.488]     LinNumberOfImagePages: 41
[    16.488]     LinRedMaskSize: 0
[    16.488]     LinRedFieldPosition: 0
[    16.488]     LinGreenMaskSize: 0
[    16.488]     LinGreenFieldPosition: 0
[    16.488]     LinBlueMaskSize: 0
[    16.488]     LinBlueFieldPosition: 0
[    16.488]     LinRsvdMaskSize: 0
[    16.488]     LinRsvdFieldPosition: 0
[    16.488]     MaxPixelClock: 230000000
[    16.489] Mode: 117 (1024x768)
[    16.489]     ModeAttributes: 0x9b
[    16.489]     WinAAttributes: 0x7
[    16.489]     WinBAttributes: 0x0
[    16.489]     WinGranularity: 64
[    16.489]     WinSize: 64
[    16.489]     WinASegment: 0xa000
[    16.489]     WinBSegment: 0x0
[    16.489]     WinFuncPtr: 0xc000863f
[    16.489]     BytesPerScanline: 2048
[    16.489]     XResolution: 1024
[    16.489]     YResolution: 768
[    16.489]     XCharSize: 8
[    16.489]     YCharSize: 16
[    16.489]     NumberOfPlanes: 1
[    16.489]     BitsPerPixel: 16
[    16.489]     NumberOfBanks: 1
[    16.489]     MemoryModel: 6
[    16.489]     BankSize: 0
[    16.489]     NumberOfImages: 20
[    16.489]     RedMaskSize: 5
[    16.489]     RedFieldPosition: 11
[    16.489]     GreenMaskSize: 6
[    16.489]     GreenFieldPosition: 5
[    16.489]     BlueMaskSize: 5
[    16.489]     BlueFieldPosition: 0
[    16.489]     RsvdMaskSize: 0
[    16.489]     RsvdFieldPosition: 0
[    16.489]     DirectColorModeInfo: 0
[    16.489]     PhysBasePtr: 0xb0000000
[    16.489]     LinBytesPerScanLine: 2048
[    16.489]     BnkNumberOfImagePages: 20
[    16.489]     LinNumberOfImagePages: 20
[    16.489]     LinRedMaskSize: 5
[    16.489]     LinRedFieldPosition: 11
[    16.489]     LinGreenMaskSize: 6
[    16.489]     LinGreenFieldPosition: 5
[    16.489]     LinBlueMaskSize: 5
[    16.489]     LinBlueFieldPosition: 0
[    16.489]     LinRsvdMaskSize: 0
[    16.489]     LinRsvdFieldPosition: 0
[    16.489]     MaxPixelClock: 230000000
[    16.489] *Mode: 118 (1024x768)
[    16.489]     ModeAttributes: 0x9b
[    16.489]     WinAAttributes: 0x7
[    16.489]     WinBAttributes: 0x0
[    16.489]     WinGranularity: 64
[    16.489]     WinSize: 64
[    16.489]     WinASegment: 0xa000
[    16.489]     WinBSegment: 0x0
[    16.489]     WinFuncPtr: 0xc000863f
[    16.489]     BytesPerScanline: 4096
[    16.489]     XResolution: 1024
[    16.489]     YResolution: 768
[    16.489]     XCharSize: 8
[    16.489]     YCharSize: 16
[    16.489]     NumberOfPlanes: 1
[    16.489]     BitsPerPixel: 32
[    16.489]     NumberOfBanks: 1
[    16.489]     MemoryModel: 6
[    16.489]     BankSize: 0
[    16.489]     NumberOfImages: 9
[    16.489]     RedMaskSize: 8
[    16.489]     RedFieldPosition: 16
[    16.489]     GreenMaskSize: 8
[    16.489]     GreenFieldPosition: 8
[    16.489]     BlueMaskSize: 8
[    16.489]     BlueFieldPosition: 0
[    16.489]     RsvdMaskSize: 8
[    16.489]     RsvdFieldPosition: 24
[    16.489]     DirectColorModeInfo: 0
[    16.489]     PhysBasePtr: 0xb0000000
[    16.489]     LinBytesPerScanLine: 4096
[    16.489]     BnkNumberOfImagePages: 9
[    16.489]     LinNumberOfImagePages: 9
[    16.489]     LinRedMaskSize: 8
[    16.489]     LinRedFieldPosition: 16
[    16.489]     LinGreenMaskSize: 8
[    16.489]     LinGreenFieldPosition: 8
[    16.489]     LinBlueMaskSize: 8
[    16.489]     LinBlueFieldPosition: 0
[    16.489]     LinRsvdMaskSize: 8
[    16.489]     LinRsvdFieldPosition: 24
[    16.489]     MaxPixelClock: 230000000
[    16.490] *Mode: 112 (640x480)
[    16.490]     ModeAttributes: 0x9b
[    16.490]     WinAAttributes: 0x7
[    16.490]     WinBAttributes: 0x0
[    16.490]     WinGranularity: 64
[    16.490]     WinSize: 64
[    16.490]     WinASegment: 0xa000
[    16.490]     WinBSegment: 0x0
[    16.490]     WinFuncPtr: 0xc000863f
[    16.490]     BytesPerScanline: 2560
[    16.490]     XResolution: 640
[    16.490]     YResolution: 480
[    16.490]     XCharSize: 8
[    16.490]     YCharSize: 16
[    16.490]     NumberOfPlanes: 1
[    16.490]     BitsPerPixel: 32
[    16.490]     NumberOfBanks: 1
[    16.490]     MemoryModel: 6
[    16.490]     BankSize: 0
[    16.490]     NumberOfImages: 25
[    16.490]     RedMaskSize: 8
[    16.490]     RedFieldPosition: 16
[    16.490]     GreenMaskSize: 8
[    16.490]     GreenFieldPosition: 8
[    16.490]     BlueMaskSize: 8
[    16.490]     BlueFieldPosition: 0
[    16.490]     RsvdMaskSize: 8
[    16.490]     RsvdFieldPosition: 24
[    16.490]     DirectColorModeInfo: 0
[    16.490]     PhysBasePtr: 0xb0000000
[    16.490]     LinBytesPerScanLine: 2560
[    16.490]     BnkNumberOfImagePages: 25
[    16.490]     LinNumberOfImagePages: 25
[    16.490]     LinRedMaskSize: 8
[    16.490]     LinRedFieldPosition: 16
[    16.490]     LinGreenMaskSize: 8
[    16.490]     LinGreenFieldPosition: 8
[    16.490]     LinBlueMaskSize: 8
[    16.490]     LinBlueFieldPosition: 0
[    16.490]     LinRsvdMaskSize: 8
[    16.490]     LinRsvdFieldPosition: 24
[    16.490]     MaxPixelClock: 230000000
[    16.490] Mode: 114 (800x600)
[    16.490]     ModeAttributes: 0x9b
[    16.490]     WinAAttributes: 0x7
[    16.490]     WinBAttributes: 0x0
[    16.490]     WinGranularity: 64
[    16.490]     WinSize: 64
[    16.490]     WinASegment: 0xa000
[    16.490]     WinBSegment: 0x0
[    16.490]     WinFuncPtr: 0xc000863f
[    16.490]     BytesPerScanline: 1600
[    16.490]     XResolution: 800
[    16.490]     YResolution: 600
[    16.490]     XCharSize: 8
[    16.490]     YCharSize: 16
[    16.490]     NumberOfPlanes: 1
[    16.490]     BitsPerPixel: 16
[    16.490]     NumberOfBanks: 1
[    16.490]     MemoryModel: 6
[    16.490]     BankSize: 0
[    16.490]     NumberOfImages: 33
[    16.490]     RedMaskSize: 5
[    16.490]     RedFieldPosition: 11
[    16.490]     GreenMaskSize: 6
[    16.490]     GreenFieldPosition: 5
[    16.490]     BlueMaskSize: 5
[    16.490]     BlueFieldPosition: 0
[    16.490]     RsvdMaskSize: 0
[    16.491]     RsvdFieldPosition: 0
[    16.491]     DirectColorModeInfo: 0
[    16.491]     PhysBasePtr: 0xb0000000
[    16.491]     LinBytesPerScanLine: 1600
[    16.491]     BnkNumberOfImagePages: 33
[    16.491]     LinNumberOfImagePages: 33
[    16.491]     LinRedMaskSize: 5
[    16.491]     LinRedFieldPosition: 11
[    16.491]     LinGreenMaskSize: 6
[    16.491]     LinGreenFieldPosition: 5
[    16.491]     LinBlueMaskSize: 5
[    16.491]     LinBlueFieldPosition: 0
[    16.491]     LinRsvdMaskSize: 0
[    16.491]     LinRsvdFieldPosition: 0
[    16.491]     MaxPixelClock: 230000000
[    16.491] *Mode: 115 (800x600)
[    16.491]     ModeAttributes: 0x9b
[    16.491]     WinAAttributes: 0x7
[    16.491]     WinBAttributes: 0x0
[    16.491]     WinGranularity: 64
[    16.491]     WinSize: 64
[    16.491]     WinASegment: 0xa000
[    16.491]     WinBSegment: 0x0
[    16.491]     WinFuncPtr: 0xc000863f
[    16.491]     BytesPerScanline: 3200
[    16.491]     XResolution: 800
[    16.491]     YResolution: 600
[    16.491]     XCharSize: 8
[    16.491]     YCharSize: 16
[    16.491]     NumberOfPlanes: 1
[    16.491]     BitsPerPixel: 32
[    16.491]     NumberOfBanks: 1
[    16.491]     MemoryModel: 6
[    16.491]     BankSize: 0
[    16.491]     NumberOfImages: 16
[    16.491]     RedMaskSize: 8
[    16.491]     RedFieldPosition: 16
[    16.491]     GreenMaskSize: 8
[    16.491]     GreenFieldPosition: 8
[    16.491]     BlueMaskSize: 8
[    16.491]     BlueFieldPosition: 0
[    16.491]     RsvdMaskSize: 8
[    16.491]     RsvdFieldPosition: 24
[    16.491]     DirectColorModeInfo: 0
[    16.491]     PhysBasePtr: 0xb0000000
[    16.491]     LinBytesPerScanLine: 3200
[    16.491]     BnkNumberOfImagePages: 16
[    16.491]     LinNumberOfImagePages: 16
[    16.491]     LinRedMaskSize: 8
[    16.491]     LinRedFieldPosition: 16
[    16.491]     LinGreenMaskSize: 8
[    16.491]     LinGreenFieldPosition: 8
[    16.491]     LinBlueMaskSize: 8
[    16.491]     LinBlueFieldPosition: 0
[    16.491]     LinRsvdMaskSize: 8
[    16.491]     LinRsvdFieldPosition: 24
[    16.491]     MaxPixelClock: 230000000
[    16.491] Mode: 101 (640x480)
[    16.491]     ModeAttributes: 0x9b
[    16.491]     WinAAttributes: 0x7
[    16.491]     WinBAttributes: 0x0
[    16.491]     WinGranularity: 64
[    16.491]     WinSize: 64
[    16.491]     WinASegment: 0xa000
[    16.491]     WinBSegment: 0x0
[    16.491]     WinFuncPtr: 0xc000863f
[    16.491]     BytesPerScanline: 640
[    16.491]     XResolution: 640
[    16.491]     YResolution: 480
[    16.491]     XCharSize: 8
[    16.492]     YCharSize: 16
[    16.492]     NumberOfPlanes: 1
[    16.492]     BitsPerPixel: 8
[    16.492]     NumberOfBanks: 1
[    16.492]     MemoryModel: 4
[    16.492]     BankSize: 0
[    16.492]     NumberOfImages: 101
[    16.492]     RedMaskSize: 0
[    16.492]     RedFieldPosition: 0
[    16.492]     GreenMaskSize: 0
[    16.492]     GreenFieldPosition: 0
[    16.492]     BlueMaskSize: 0
[    16.492]     BlueFieldPosition: 0
[    16.492]     RsvdMaskSize: 0
[    16.492]     RsvdFieldPosition: 0
[    16.492]     DirectColorModeInfo: 0
[    16.492]     PhysBasePtr: 0xb0000000
[    16.492]     LinBytesPerScanLine: 640
[    16.492]     BnkNumberOfImagePages: 101
[    16.492]     LinNumberOfImagePages: 101
[    16.492]     LinRedMaskSize: 0
[    16.492]     LinRedFieldPosition: 0
[    16.492]     LinGreenMaskSize: 0
[    16.492]     LinGreenFieldPosition: 0
[    16.492]     LinBlueMaskSize: 0
[    16.492]     LinBlueFieldPosition: 0
[    16.492]     LinRsvdMaskSize: 0
[    16.492]     LinRsvdFieldPosition: 0
[    16.492]     MaxPixelClock: 230000000
[    16.492] Mode: 103 (800x600)
[    16.492]     ModeAttributes: 0x9b
[    16.492]     WinAAttributes: 0x7
[    16.492]     WinBAttributes: 0x0
[    16.492]     WinGranularity: 64
[    16.492]     WinSize: 64
[    16.492]     WinASegment: 0xa000
[    16.492]     WinBSegment: 0x0
[    16.492]     WinFuncPtr: 0xc000863f
[    16.492]     BytesPerScanline: 832
[    16.492]     XResolution: 800
[    16.492]     YResolution: 600
[    16.492]     XCharSize: 8
[    16.492]     YCharSize: 16
[    16.492]     NumberOfPlanes: 1
[    16.492]     BitsPerPixel: 8
[    16.492]     NumberOfBanks: 1
[    16.492]     MemoryModel: 4
[    16.492]     BankSize: 0
[    16.492]     NumberOfImages: 62
[    16.492]     RedMaskSize: 0
[    16.492]     RedFieldPosition: 0
[    16.492]     GreenMaskSize: 0
[    16.492]     GreenFieldPosition: 0
[    16.492]     BlueMaskSize: 0
[    16.492]     BlueFieldPosition: 0
[    16.492]     RsvdMaskSize: 0
[    16.492]     RsvdFieldPosition: 0
[    16.492]     DirectColorModeInfo: 0
[    16.492]     PhysBasePtr: 0xb0000000
[    16.492]     LinBytesPerScanLine: 832
[    16.492]     BnkNumberOfImagePages: 62
[    16.492]     LinNumberOfImagePages: 62
[    16.492]     LinRedMaskSize: 0
[    16.492]     LinRedFieldPosition: 0
[    16.492]     LinGreenMaskSize: 0
[    16.492]     LinGreenFieldPosition: 0
[    16.492]     LinBlueMaskSize: 0
[    16.492]     LinBlueFieldPosition: 0
[    16.492]     LinRsvdMaskSize: 0
[    16.492]     LinRsvdFieldPosition: 0
[    16.492]     MaxPixelClock: 230000000
[    16.492] Mode: 111 (640x480)
[    16.492]     ModeAttributes: 0x9b
[    16.492]     WinAAttributes: 0x7
[    16.492]     WinBAttributes: 0x0
[    16.492]     WinGranularity: 64
[    16.492]     WinSize: 64
[    16.492]     WinASegment: 0xa000
[    16.492]     WinBSegment: 0x0
[    16.492]     WinFuncPtr: 0xc000863f
[    16.493]     BytesPerScanline: 1280
[    16.493]     XResolution: 640
[    16.493]     YResolution: 480
[    16.493]     XCharSize: 8
[    16.493]     YCharSize: 16
[    16.493]     NumberOfPlanes: 1
[    16.493]     BitsPerPixel: 16
[    16.493]     NumberOfBanks: 1
[    16.493]     MemoryModel: 6
[    16.493]     BankSize: 0
[    16.493]     NumberOfImages: 50
[    16.493]     RedMaskSize: 5
[    16.493]     RedFieldPosition: 11
[    16.493]     GreenMaskSize: 6
[    16.493]     GreenFieldPosition: 5
[    16.493]     BlueMaskSize: 5
[    16.493]     BlueFieldPosition: 0
[    16.493]     RsvdMaskSize: 0
[    16.493]     RsvdFieldPosition: 0
[    16.493]     DirectColorModeInfo: 0
[    16.493]     PhysBasePtr: 0xb0000000
[    16.493]     LinBytesPerScanLine: 1280
[    16.493]     BnkNumberOfImagePages: 50
[    16.493]     LinNumberOfImagePages: 50
[    16.493]     LinRedMaskSize: 5
[    16.493]     LinRedFieldPosition: 11
[    16.493]     LinGreenMaskSize: 6
[    16.493]     LinGreenFieldPosition: 5
[    16.493]     LinBlueMaskSize: 5
[    16.493]     LinBlueFieldPosition: 0
[    16.493]     LinRsvdMaskSize: 0
[    16.493]     LinRsvdFieldPosition: 0
[    16.493]     MaxPixelClock: 230000000
[    16.493] 
[    16.493] (II) VESA(0): Total Memory: 511 64KB banks (32704kB)
[    16.493] (II) VESA(0): <default monitor>: Using hsync value of 46.82 kHz
[    16.493] (II) VESA(0): <default monitor>: Using vrefresh value of 60.03 Hz
[    16.493] (WW) VESA(0): Unable to estimate virtual size
[    16.493] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    16.493] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    16.493] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    16.493] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    16.493] (II) VESA(0): <default monitor>: Using hsync value of 46.82 kHz
[    16.493] (II) VESA(0): <default monitor>: Using vrefresh value of 60.03 Hz
[    16.493] (WW) VESA(0): Unable to estimate virtual size
[    16.493] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    16.493] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    16.493] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    16.493] (WW) VESA(0): No valid modes left. Trying aggressive sync range...
[    16.493] (II) VESA(0): <default monitor>: Using hsync range of 31.50-46.82 kHz
[    16.493] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-60.03 Hz
[    16.493] (WW) VESA(0): Unable to estimate virtual size
[    16.493] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    16.493] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    16.493] (**) VESA(0): *Built-in mode "1024x768"
[    16.493] (**) VESA(0): *Built-in mode "800x600"
[    16.493] (**) VESA(0): Display dimensions: (340, 190) mm
[    16.493] (**) VESA(0): DPI set to (76, 102)
[    16.493] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    16.493] (**) VESA(0): Using "Shadow Framebuffer"
[    16.493] (II) Loading sub module "shadow"
[    16.493] (II) LoadModule: "shadow"
[    16.493] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    16.493] (II) Module shadow: vendor="X.Org Foundation"
[    16.493]     compiled for 1.11.3, module version = 1.1.0
[    16.493]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.493] (II) Loading sub module "fb"
[    16.493] (II) LoadModule: "fb"
[    16.494] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.494] (II) Module fb: vendor="X.Org Foundation"
[    16.494]     compiled for 1.11.3, module version = 1.0.0
[    16.494]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.494] (II) UnloadModule: "fbdev"
[    16.494] (II) Unloading fbdev
[    16.494] (II) UnloadModule: "fbdevhw"
[    16.494] (II) Unloading fbdevhw
[    16.494] (==) Depth 24 pixmap format is 32 bpp
[    16.494] (II) Loading sub module "int10"
[    16.494] (II) LoadModule: "int10"
[    16.494] (II) Loading /usr/lib/xorg/modules/libint10.so
[    16.494] (II) Module int10: vendor="X.Org Foundation"
[    16.494]     compiled for 1.11.3, module version = 1.0.0
[    16.494]     ABI class: X.Org Video Driver, version 11.0
[    16.494] (II) VESA(0): initializing int10
[    16.494] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    16.494] (II) VESA(0): VESA BIOS detected
[    16.495] (II) VESA(0): VESA VBE Version 3.0
[    16.495] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[    16.495] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[    16.495] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    16.495] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    16.495] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[    16.495] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    16.502] (II) VESA(0): virtual address = 0x7f374386c000,
    physical address = 0xb0000000, size = 33488896
[    16.508] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    16.580] (==) VESA(0): Default visual is TrueColor
[    16.580] (==) VESA(0): Backing store disabled
[    16.580] (==) VESA(0): DPMS enabled
[    16.580] (==) RandR enabled
[    16.580] (II) Initializing built-in extension Generic Event Extension
[    16.580] (II) Initializing built-in extension SHAPE
[    16.580] (II) Initializing built-in extension MIT-SHM
[    16.580] (II) Initializing built-in extension XInputExtension
[    16.580] (II) Initializing built-in extension XTEST
[    16.580] (II) Initializing built-in extension BIG-REQUESTS
[    16.580] (II) Initializing built-in extension SYNC
[    16.580] (II) Initializing built-in extension XKEYBOARD
[    16.580] (II) Initializing built-in extension XC-MISC
[    16.580] (II) Initializing built-in extension SECURITY
[    16.580] (II) Initializing built-in extension XINERAMA
[    16.580] (II) Initializing built-in extension XFIXES
[    16.580] (II) Initializing built-in extension RENDER
[    16.580] (II) Initializing built-in extension RANDR
[    16.581] (II) Initializing built-in extension COMPOSITE
[    16.581] (II) Initializing built-in extension DAMAGE
[    16.586] (II) AIGLX: Screen 0 is not DRI2 capable
[    16.586] (II) AIGLX: Screen 0 is not DRI capable
[    16.596] (II) AIGLX: Loaded and initialized swrast
[    16.597] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    16.606] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.608] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.608] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.608] (II) LoadModule: "evdev"
[    16.609] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.609] (II) Module evdev: vendor="X.Org Foundation"
[    16.609]     compiled for 1.11.3, module version = 2.7.0
[    16.609]     Module class: X.Org XInput Driver
[    16.609]     ABI class: X.Org XInput driver, version 16.0
[    16.609] (II) Using input driver 'evdev' for 'Power Button'
[    16.609] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.609] (**) Power Button: always reports core events
[    16.609] (**) evdev: Power Button: Device: "/dev/input/event2"
[    16.609] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.609] (--) evdev: Power Button: Found keys
[    16.609] (II) evdev: Power Button: Configuring as keyboard
[    16.609] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    16.609] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.609] (**) Option "xkb_rules" "evdev"
[    16.609] (**) Option "xkb_model" "pc105"
[    16.609] (**) Option "xkb_layout" "us"
[    16.609] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    16.609] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.609] (II) Using input driver 'evdev' for 'Video Bus'
[    16.609] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.609] (**) Video Bus: always reports core events
[    16.609] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    16.610] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.610] (--) evdev: Video Bus: Found keys
[    16.610] (II) evdev: Video Bus: Configuring as keyboard
[    16.610] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    16.610] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.610] (**) Option "xkb_rules" "evdev"
[    16.610] (**) Option "xkb_model" "pc105"
[    16.610] (**) Option "xkb_layout" "us"
[    16.610] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.610] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.610] (II) Using input driver 'evdev' for 'Power Button'
[    16.610] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.610] (**) Power Button: always reports core events
[    16.610] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.610] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.610] (--) evdev: Power Button: Found keys
[    16.610] (II) evdev: Power Button: Configuring as keyboard
[    16.610] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    16.610] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.610] (**) Option "xkb_rules" "evdev"
[    16.610] (**) Option "xkb_model" "pc105"
[    16.610] (**) Option "xkb_layout" "us"
[    16.611] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.611] (II) No input driver specified, ignoring this device.
[    16.611] (II) This device may have been added with another device file.
[    16.611] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    16.611] (II) No input driver specified, ignoring this device.
[    16.611] (II) This device may have been added with another device file.
[    16.611] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[    16.611] (II) No input driver specified, ignoring this device.
[    16.611] (II) This device may have been added with another device file.
[    16.611] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    16.611] (II) No input driver specified, ignoring this device.
[    16.611] (II) This device may have been added with another device file.
[    16.612] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/event5)
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: Applying InputClass "evdev pointer catchall"
[    16.612] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400a'
[    16.612] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: always reports core events
[    16.612] (**) evdev: Logitech Unifying Device. Wireless PID:400a: Device: "/dev/input/event5"
[    16.612] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Vendor 0x46d Product 0xc52b
[    16.612] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found 20 mouse buttons
[    16.612] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found scroll wheel(s)
[    16.612] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found relative axes
[    16.612] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found x and y relative axes
[    16.612] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Configuring as mouse
[    16.612] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Adding scrollwheel support
[    16.612] (**) evdev: Logitech Unifying Device. Wireless PID:400a: YAxisMapping: buttons 4 and 5
[    16.612] (**) evdev: Logitech Unifying Device. Wireless PID:400a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.612] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input5/event5"
[    16.612] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400a" (type: MOUSE, id 9)
[    16.612] (II) evdev: Logitech Unifying Device. Wireless PID:400a: initialized for relative axes.
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: (accel) keeping acceleration scheme 1
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration profile 0
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration factor: 2.000
[    16.612] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration threshold: 4
[    16.612] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/mouse0)
[    16.612] (II) No input driver specified, ignoring this device.
[    16.612] (II) This device may have been added with another device file.
[    16.613] (II) config/udev: Adding input device HP Webcam-101 (/dev/input/event6)
[    16.613] (**) HP Webcam-101: Applying InputClass "evdev keyboard catchall"
[    16.613] (II) Using input driver 'evdev' for 'HP Webcam-101'
[    16.613] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.613] (**) HP Webcam-101: always reports core events
[    16.613] (**) evdev: HP Webcam-101: Device: "/dev/input/event6"
[    16.613] (--) evdev: HP Webcam-101: Vendor 0x461 Product 0x4de7
[    16.613] (--) evdev: HP Webcam-101: Found keys
[    16.613] (II) evdev: HP Webcam-101: Configuring as keyboard
[    16.613] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input6/event6"
[    16.613] (II) XINPUT: Adding extended input device "HP Webcam-101" (type: KEYBOARD, id 10)
[    16.613] (**) Option "xkb_rules" "evdev"
[    16.613] (**) Option "xkb_model" "pc105"
[    16.613] (**) Option "xkb_layout" "us"
[    16.613] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.613] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.613] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.613] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.613] (**) AT Translated Set 2 keyboard: always reports core events
[    16.613] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.613] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.613] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.613] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.613] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    16.613] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    16.613] (**) Option "xkb_rules" "evdev"
[    16.613] (**) Option "xkb_model" "pc105"
[    16.613] (**) Option "xkb_layout" "us"
[    16.614] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    16.614] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.614] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.614] (II) LoadModule: "synaptics"
[    16.614] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.614] (II) Module synaptics: vendor="X.Org Foundation"
[    16.614]     compiled for 1.11.3, module version = 1.6.2
[    16.614]     Module class: X.Org XInput Driver
[    16.614]     ABI class: X.Org XInput driver, version 16.0
[    16.614] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.614] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.614] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.614] (**) Option "Device" "/dev/input/event8"
[    16.620] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5634
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4598
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    16.620] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.620] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.626] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[    16.626] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    16.626] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.626] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    16.626] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    16.626] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.626] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.626] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.626] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.626] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.626] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    16.626] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.628] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    16.628] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    16.628] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    16.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.628] (**) HP WMI hotkeys: always reports core events
[    16.628] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    16.628] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    16.628] (--) evdev: HP WMI hotkeys: Found keys
[    16.628] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    16.628] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    16.628] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    16.628] (**) Option "xkb_rules" "evdev"
[    16.628] (**) Option "xkb_model" "pc105"
[    16.628] (**) Option "xkb_layout" "us"
[    40.783] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
```I hope this will help. I made a live DVD of 12.10 and I had to set "nomodeset" just to use the live DVD so I guess the Sandybridge drivers still aren't updated in 12.10. Maybe if installed it might work better. I just grabbing straws so to speak hoping this problem will be solved.

---

### Post by BicyclerBoy on 2012-09-13
Not really.. it shows vesa driver is loaded (because of grub nomodeset).

And it is kernel 3.2, so sandybridge graphics will be limited/non-functional.

---

### Post by rickm1945 on 2012-09-13
> **BicyclerBoy said:**
> Not really.. it shows vesa driver is loaded (because of grub nomodeset).

And it is kernel 3.2, so sandybridge graphics will be limited/non-functional.
Epodx64 was saying if I installed Intel xorg-server then installed i965 driver that it would remove "nomodeset" and install i965 driver which would work with the i915 driver. I can manually remove nomodeset and boot into recovery mode and do this. Even on 12.10 live beta DVD I had to use nomodeset just to use the live DVD.  The 12.10 version uses the 3.5 kernel but for some reason still don't work. Any other ideas. Did I miss something you were telling me? I would like this laptop to run Ubuntu as it should run.

AS far as the Intel xorg-server I downloaded the Deb package and tried to install and got error shown in the screen shot attach: at the bottom of the post.
[http://ubuntuforums.org/showthread.php?t=2054992](http://ubuntuforums.org/showthread.php?t=2054992)

I have been trying all these suggestions since April.

---

### Post by rickm1945 on 2012-09-13
I installed synaptic package manager. I looked up the xorg-server-intel driver package and it was already installed. I removed nomodeset from grub and reinstalled and updated grub booted  and got to the first screen and then black screen so had to add nomodeset again. If this driver package is supposed to help why isn't it working. Will it work if I install xorg-server-intel again after install of Ubuntu 12.10 or am I wasting my time. I am beginning to think it is this computer.

---

### Post by rickm1945 on 2012-09-14
> **BicyclerBoy said:**
> Ouch that sucks..

The later kernels break the broadcomm wifi b43 driver.
You can boot with an older kernel image:
- reboot & tap/hold down shift key
- select previous kernel image

Then you can uninstall the 3.5 image or just make the 3.2 image the grub default.
The later kernel is required for the video driver.

My Fix for the b43 driver:
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*
(network connection required)

The fix to the broadcomm wifi driver code is a couple of lines:
Attached are my notes on it..

But how is the graphics ?
Can you post your /var/log/Xorg.0.log?
You did remove the nomodeset ?

Are saying that after I install xorg-edgers, I can get the b43 driver back by adding

sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*

These two lines that they will repair/restore the b43 drivers? I
I'm still working on your solution to my video problem. I installed the xorg-edgers again. I'm waiting till I hear from you before I go on. Can I do your fix for b43 before I reboot after install of xorg-edgers.
Nomodeset has been removed.

I have 69 updates waiting, should I install them now before I reboot after install of xorg-edgers. Most of these updates apply to xorg-edgers and the Intel drivers.

---

### Post by Segofam on 2012-09-14
Was it the screen resolution i.e. desktop would not fit the screen?

---

### Post by rickm1945 on 2012-09-14
> **Segofam said:**
> Was it the screen resolution i.e. desktop would not fit the screen?
No, resolution is 1024x768 and should be 1366x768.

---

### Post by rickm1945 on 2012-09-14
I closing this thread. The resolution is not corrected at this time and after 5 months of resetting, installing, and reinstalling the OS and various fixes noe of which worked I have given up. I even tried Ubuntu 12.10 Beta 1 and it won't setup my graphics right either. So will leave it alone. I will most likely keep 12.04 since I don't see any point in upgrading if it isn't an upgrade.

---

### Post by BicyclerBoy on 2012-09-14
Just for completeness & to attempt answer some of post #40.
Sadly this answer/explanation does not do justice to the subject..

The xorg-edgers ppa updates the intel driver & the kernel because:
The video drivers for intel (& AMD nVidia etc) are part kernel module & part user space.

Xorg-edgers recommended using all their packages together but you can run the latest i965 or vesa with older kernel (YMMV).
Sandybridge/Ivybridge needs the latest kernel.
Xorg-edgers is updated daily, the ground is constantly moving.

If xorg-edgers kernel & intel driver does not work on your h/w then you have real problems..

Kernel 3.5 breaks the broadcomm b43 kernel module but the fix is a couple code edits as tabled in previously attached txt file.

By running 2 diff kernels from grub, you can keep using wifi etc & try the 3.5 kernel to see if it ever works..
 
The 2 apt-get install commands, I tabled, are the commonly suggested re-install fixes that gets the right driver to load etc.
But just that is not enough..you need to edit the source code.
There is no point doing this (no need?) unless kernel 3.5 is installed.
Only do it from running kernel 3.5.

The hack:
The b43 module is loaded by dkms & is automatically compiled from source with every kernel update/trigger; the (open) source is already on your PC.
You are meant to download the source package & edit..I just hacked the code in the installed b43 package & retriggered the dkms process.
This way I can forget about rebuilding b43 with every kernel update.
Eventually the b43 package will be fixed.

Note: do **not** do the hack edit/dkms trigger when running kernel 3.2, it will fail at best, stuff up wifi at worst.
Note: If you reinstall the b43 packages after the 'hack' edit the changes will be lost or recovered/repaired depending on your POV..

Note: you can reboot into a older/earlier kernel by using grub..
So you can have old kernel 3.2 (with nomodeset & working wifi) & 3.5 (for testing) & both should not break X server (VESA loads with nomodeset).

---

### Post by silbar on 2012-09-14
I come into this thread very late, but have the same problem, on just installing 12.04.  From xrandr I got the following options:
[INDENT]
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 4096 x 4096
VGA1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
   1400x1050      60.0  
   1280x1024      60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  [/INDENT]

I suspect there is a way to get to 1600x900 but System Settings > Display says I am a laptop and 1024x768 is the highest I can go.  (I am not a laptop.)  I didn't see how, in my brief whiz through this thread, to get there.

Rico Silbar

Note added: on restarting 12.04 today the desktop came up automatically in higher resolution!  I certainly didn't do anything special to get this.  Going to System Setting > Display, it now recognizes my Hannspree monitor as HSG 20" and at 1600 by 900 display.  Amazing!

RRS

---

### Post by rickm1945 on 2012-09-15
> **BicyclerBoy said:**
> Just for completeness & to attempt answer some of post #40.
Sadly this answer/explanation does not do justice to the subject..

The xorg-edgers ppa updates the intel driver & the kernel because:
The video drivers for intel (& AMD nVidia etc) are part kernel module & part user space.

Xorg-edgers recommended using all their packages together but you can run the latest i965 or vesa with older kernel (YMMV).
Sandybridge/Ivybridge needs the latest kernel.
Xorg-edgers is updated daily, the ground is constantly moving.

If xorg-edgers kernel & intel driver does not work on your h/w then you have real problems..

Kernel 3.5 breaks the broadcomm b43 kernel module but the fix is a couple code edits as tabled in previously attached txt file.

By running 2 diff kernels from grub, you can keep using wifi etc & try the 3.5 kernel to see if it ever works..
 
The 2 apt-get install commands, I tabled, are the commonly suggested re-install fixes that gets the right driver to load etc.
But just that is not enough..you need to edit the source code.
There is no point doing this (no need?) unless kernel 3.5 is installed.
Only do it from running kernel 3.5.

The hack:
The b43 module is loaded by dkms & is automatically compiled from source with every kernel update/trigger; the (open) source is already on your PC.
You are meant to download the source package & edit..I just hacked the code in the installed b43 package & retriggered the dkms process.
This way I can forget about rebuilding b43 with every kernel update.
Eventually the b43 package will be fixed.

Note: do **not** do the hack edit/dkms trigger when running kernel 3.2, it will fail at best, stuff up wifi at worst.
Note: If you reinstall the b43 packages after the 'hack' edit the changes will be lost or recovered/repaired depending on your POV..

Note: you can reboot into a older/earlier kernel by using grub..
So you can have old kernel 3.2 (with nomodeset & working wifi) & 3.5 (for testing) & both should not break X server (VESA loads with nomodeset).

I the xorg-server package is installed now. Yesterday I removed "nomodeset" and then installed the 3.5 kernel.  Then the update manager said there were 67 updates and so I installed them. I rebooted and nothing was changed except for the loss of wifi. I used power switch to turn off and reboot. I was then able to boot through recovery mode.
I am pretty familiar with using computers and repairs sine I'm a tech, but when you say editing source code. I' am at a total loss. 

Maybe it is this laptop, as I mentioned before my battery discharges when the even when I shut down and turn off the power. There are so many things possibly wrong that it is hard to troubleshoot. I have been in contact with HP about the battery, but if I mention Linux they say they don't support Linux and that this laptop was built for Windows 7. Everything works ok in Windows 7 although I haven't used Windows since I've had this Laptop except to download Ubuntu and Partition Master. I had to change my HD from Dynamic to Basic. That is all he time I spent in Windows. Maybe I should use Windows and see If I have any graphics problems there.

I really appreciate all your help and wish I could get this Laptop right. Thanks for your reply.

---

### Post by rickm1945 on 2012-09-15
> **silbar said:**
> I come into this thread very late, but have the same problem, on just installing 12.04.  From xrandr I got the following options:[INDENT]
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 4096 x 4096
VGA1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
   1400x1050      60.0  
   1280x1024      60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  [/INDENT]I suspect there is a way to get to 1600x900 but System Settings > Display says I am a laptop and 1024x768 is the highest I can go.  (I am not a laptop.)  I didn't see how, in my brief whiz through this thread, to get there.

Rico Silbar
What is the brand of your PC? Just curious.

---

### Post by silbar on 2012-09-15
Rickm1945 asks what my machine is: HP Pavillion desktop.  As edited above, the monitor is a Hannspree 20" LCD.

RRS

---

### Post by rickm1945 on 2012-09-15
> **silbar said:**
> Rickm1945 asks what my machine is: HP Pavillion desktop.  As edited above, the monitor is a Hannspree 20" LCD.

RRS

The reason I asked is if your graphics adapter is using Sandybridge drivers you may have to do some tweaking and hope it works for you. I have a HP Pavilion Laptop,my first and  last HP computer. Read my thread here there is a lot of information on possible ways to attempt to correct the situation. Good luck.

---

