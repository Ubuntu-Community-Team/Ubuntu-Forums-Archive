---
title: "Nvidia 6200 - Olevia 26&quot; TV - DPMS Suspend"
date: 2012-12-01
forum: Multimedia Software
---

### Post by dannyboy79 on 2012-12-01
I switched out an old MX440 with an Nvidia 6200 and also switched from a Princton 17" monitor to an Olevia 23" TV. My tv keeps going into DPMS Suspend mode right after ubuntu gets to a GUI. I see the login manager (gdm or plymouth?) and immediately the screen goes into DPMS SUSPEND. I went to tty1 session and removed the old nvidia 96.43 module and install nvidia-current but for some reason the TV Monitor (hooked up via VGA) keeps entering DPMS Suspend mode no matter what. I have even turned off DPMS mode within the TV Setup. I don't know what else to do? Can anyone help please?

---

### Post by BicyclerBoy on 2012-12-01
Assuming you can still console login with a usable video mode.. Run:
sudo nvidia-xconfig

post your /var/log/Xorg.0.log

The monitor/TV ? may be suspending due to unsupported video mode from previous.

The VGA / TV monitor thing you speak of ??
Is this a VGA to s-video/composite converter ?

---

### Post by dannyboy79 on 2012-12-01
it's straight VGA, no s-video used at all. I did the fresh xorg.conf using nvidia-xconfig, whats very strange is that it shows boot up info (since I use splash option in grub line) and it even shows Ubuntu with 4 little dots under it where they blink in succession but as soon as it tries to go to my login manager (is it plymouth?) the screen goes blue and the monitor states in the lower left corner DPMS SUSPEND or DPMS STANDBY. Very frustrating. 

Here's the .xsession-errors
[http://pastebin.com/XsTDkKXF](http://pastebin.com/XsTDkKXF)

Here's the Xorg.0.log
[http://pastebin.com/y2jJt75C](http://pastebin.com/y2jJt75C)


Here's the xorg.conf file. I am using 10.04.4 Ubuntu
[http://pastebin.com/4RBZdAmY](http://pastebin.com/4RBZdAmY)

---

### Post by BicyclerBoy on 2012-12-01
You could try backup/delete:
/home/daniel/.nvidia-settings-rc

The driver is defaulting to 1360x768

and you did not run:
sudo nvidia-xconfig

---

### Post by dannyboy79 on 2012-12-01
i already renamed /home/daniel/.nvidia-settings-rc to /home/daniel/.nvidia-settings-rc_OLD and yes I did run sudo nvidia-xconfig. I am now trying the latest Nvidia driver from the website which is 304.64 per their website says is for a 6200 series. Still doesn't work, right after the splash screen it goes blue and says DPMS SUSPEND. I am at a loss. I can run it using low res graphics in 1024x768 but this card can do way more!

---

### Post by BicyclerBoy on 2012-12-01
There is little point using the latest driver for an old card..
The 6200 has no video decode capability (PureVideo VP1 does not really count).

A point to note is the nVidia driver is an X server driver only. The boot screen & greeter screens are a kernel framebuffer driver not nVidia.

It could be the horizontal freq range is to tight or that EDID over VGA is not working 
right..
HorizSync       23.0 - 48.0
could be more like it..depends on if TV can handle progressive scan or not..

Could add this to /etc/X11/xorg.conf:
Option "ModeDebug"   "True"

Or:
Do a console login
sudo service gdm stop
nvidia-xconfig --mode-debug
sudo service gdm start

look in Xorg.0.log..

---

### Post by dannyboy79 on 2012-12-02
whats weird is that ubuntu 12.04.1 ran from a live usb stick using nouveau seems to work with 1440x900 per this photo.
[https://lh5.googleusercontent.com/-ZWZK2Q2prUU/ULu8-BHNRuI/AAAAAAAAAqQ/VR7fIZhi4V4/s800/1440x900.png]("https://lh5.googleusercontent.com/-ZWZK2Q2prUU/ULu8-BHNRuI/AAAAAAAAAqQ/VR7fIZhi4V4/s800/1440x900.png")

It has randomly entered DPMS SUSPEND mode once. So, something must be wrong with the TV VGA port not being able to tell when there is an active signal. Like I said, I turned off DPMS within the TV setup menu. I can't seem to find an xorg.conf file in this live usb session.

---

### Post by dannyboy79 on 2012-12-03
would really love some help here. currently I am trying to get the nouveau driver working (because that's what's used within the usb live session to get 1440x900) but it fails with the following errors.
[http://pastebin.com/f9JYWcdd](http://pastebin.com/f9JYWcdd)

---

### Post by dannyboy79 on 2012-12-03
please help me. :(

---

### Post by BicyclerBoy on 2012-12-03
Use synaptic package manager or the jockey tool (additional drivers) & disable/remove the nVidia proprietary driver.

The nouveau driver is already installed as part of the kernel & distro.

The /var/log/Xorg.0.log will reveal which driver has claimed the GPU adapter.


Have you bought an old 8400GS ? I guess you are stuck with AGP?

Most (all) modern digital TVs do **not** allow native resolution over VGA (analogue hole) so HDMI connection should be better.

---

### Post by dannyboy79 on 2012-12-03
> **BicyclerBoy said:**
> Use synaptic package manager or the jockey tool (additional drivers) & disable/remove the nVidia proprietary driver.

The nouveau driver is already installed as part of the kernel & distro.

The /var/log/Xorg.0.log will reveal which driver has claimed the GPU adapter.


Have you bought an old 8400GS ? I guess you are stuck with AGP?

Most (all) modern digital TVs do **not** allow native resolution over VGA (analogue hole) so HDMI connection should be better.
i believe I have removed all the nvidia binaries to the best of my knowledge, i posted my latest Xorg.0.log, did you not notice it a couple posts back? Nothing shows up at all in Jockey (additional hardware drivers menu item)

I have an AsRock 775Dual-VSTA which has 1 PCIe @4x mode and the AsRock website shows that a 8400GS PCIe will work with it so I bought one. I was just hoping to get this Nvidia GeForce 6200 working with Nouveau within 10.04.4 since it works with 1440x900 within a live usb install in 12.04.

---

### Post by BicyclerBoy on 2012-12-03
Sorry missed the "pastebin" copy of Xor.0.log with nouveau driver..

Don't know why the nouveau driver has not found the card..

Check all the /etc/modprobe.d/*.conf files for any "blacklist nouveau"..
The nVidia driver pre-install scripts sets up some blacklists..
I believe there are a couple of other locations for blacklists..

The nVidia driver has some advantages (VDPAU) with 8400GS & weak CPUs.

---

### Post by dannyboy79 on 2012-12-03
shoot, i wonder if I made a mistake ordering the card I did. The Asrock website here: [http://www.asrock.com/mb/overview.asp?cat=VGA&Model=775Dual-VSTA](http://www.asrock.com/mb/overview.asp?cat=VGA&Model=775Dual-VSTA)
states a few 8400 GS models and I am noticeing they all show what I am assumiung is 256mb for RAM, example: 
Foxconn GF 8400GS/256M
and
Gigabyte GV-NX84G256H

BUT the one I ordered from Newegg has 1GB of DDR3. The compatitability chart probably says those are compatible from around 2007 when the 8400 GS was based on PCIe (NOT PCIe 2.0) and when it only had DDR2 since my motherboard is that old.

Guess I'll find out soon enough when it arrives BUT I still want to get my 6200 working at 1440x900.

---

### Post by BicyclerBoy on 2012-12-03
There were 3 versions of 8400GS (G86, G98 & G218)

I think the GT218 version is PCIe.
I guess yours is the GT218 & equivalent to GT205/210/310.
Decoder is okay but shaders are too slow..

There is no value in an old GT205 PCI-e card..The GT220 is absolute lowest spec video card for HTPC video etc..

The best PCIe HTPC cards : (best first)
GT630   (real kepler is it avail yet?)
GT620   (rebadged fermi 500 series == GT530?)
GT430
GT240   (over spec openGL shaders)
GT220   (limited de-interlace/scaler)

---

### Post by dannyboy79 on 2012-12-03
BUT I am limited by my motherboard. this is my main workstation which i use for daily computing tasks, video editing, etc etc. Its not a HTPC.

I will have to return the 8400 GS because I doubt it will be compatible with the ASrock 775dual-vsta. I certainly will need help getting 1440x900 graphics working on my 6200 using Nouveau OR figuring out why DPMS SUSPEND is activated with the binary drivers. Would really appreciate it.

---

### Post by BicyclerBoy on 2012-12-04
I am fairly sure any PCIe card will work in any PCIe slot..(assuming the right socket length & any req. power plug)
PCIe 2.0 cards are generally compatible with PCIe 1.0 slots.
The opposite use case is mandatory..
PCIe 2.1 cards may require mobo BIOS update.
[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

nVidia driver route:
Add to file /etc/X11/xorg.conf (any section)
Option  "ModeDebug"  "True"

I don't have any experience using/debugging the nouveau driver.
It is very likely the verbosity of logs can be increased.

---

### Post by dannyboy79 on 2012-12-04
I am just at wits end here!!! No matter which propritary nvidia driver I use, imeedaitely following the a screen where it says Ubunut and shows 4 little dots blinking in succession the monitor goes into DPMS STANDBY or DPMS SUSPEND. Once the monitor is in this state there's no getting it out of it, I have tried ctrl-alt-f1 thru f7, i have tried ctrl-alt-del but nothing will wake the monitor. If I get the timing just right, I can get into tty1.

So I am stuck using either the nv, vesa, or nouveau driver. Currently I am trying to use the nouveau driver but DMESG is filled with stuff about VESA and I am stuck at a resolution of 1024x768. It tried to use the nouveau driver but fails with some drm issue so it goes to failsafe mode and low resolution. I don't know what else to try. I have upgraded to the latest possible kernel in lucid which is 3.0.0-28 I think and I am still plauged with these X issues. I don't even care about 3d rendering, all I want is a decent desktop size to do work. I am not asking for some high frame rate and gaming. Seems rediculous that Linux is plagued with these graphics issues.

---

### Post by NikTh on 2012-12-04
Hi , 
Lets start from scratch and see ... 

First remove everything related to nvidia 
```
sudo apt-get remove  --purge nvidia-* 
sudo rm /etc/X11/xorg.conf
```Then add the X - Swat PPA , it has the 304.64 driver and install the driver,  and if I'm correct  is the latest (newer) driver that supports Nvidia 6200. 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get dist-upgrade
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
```The dist-upgrade command needed here in case  new driver needs some upgraded libraries. 

Reboot and see the results. 

If not work , give again the results of 
```
cat /var/log/Xorg.0.log
```Thanks

---

### Post by dannyboy79 on 2012-12-04
awesome, thanks for coming to try and help. I will test it out later tonight after work but I will say I have tried this already and the TV gets put into DPMS SUSPEND/STANDBY BUT I will try it out and post up the Xorg.0.log file for you

---

### Post by BicyclerBoy on 2012-12-04
Don't start blaming anything until you establish root cause.
It is most likely your display/TV.
Can you:-
- swap the screen 
- swap the PC
- swap the VGA cable
- swap to diff connection DVI-D(single)-->hdmi

nVidia drivers have been plagued with EDID read problems over VGA & it could be worse on 64bit.
I suspect the windows driver has a shed-load of EDID patches/work-arounds.

Try adding the "ModeDebug" option for nVidia driver & then after DPMS occurs...login to console & copy /var/log/Xorg.0.log to somewhere safe & post it here..

---

### Post by dannyboy79 on 2012-12-04
I have no doubt it's the new 23" Olevia LT23HVX (Syntax brand) TV's fault (VGA EDID handshake info). The 6200 card has worked with a 17" princton 4:3 monitor over DVI just fine in 1280x1024 for years, even worked in a dual display setup with a panasonic 17" widescreen tv over VGA. That was long ago when my computers were in my bedroom so I don't remember which nvidia drivers I was using then. BUt then I moved all hardware downstairs and switched out the 6200 for an older MX440 so I could use the 6200 in an HTCP unit in the family room that never took shape.

The problem with waiting for it to go into DPMS SUSPEND mode (which happens almost immediately) is that I can't do anything after that, not even go to other tty sessions. I will setup ssh in low screen res so when using the nvidia driver and it goes into DPMS SUSPEND, i will at least be able to ssh in and get the log file.

When I got the new TV from my dad, I swaped out the old MX440 again for the GeForce 6200 because I thought I would get a better resolution on the TV. Maybe I should try the MX440 with the Nvidia 96.43 again just to see what sort of resolution I can get from it.

BUT, I will do as NikTH suggested first and also add the ModeDebug" option that BiclyclerBoy suggested.

PS I forgot to mention that last night I tried read-edid | parse-edid and it didn't give me any usedful information and said the data waas probably corrupt. I'll run it again tonight and post the actual output.

---

### Post by BicyclerBoy on 2012-12-04
The read-edid only seems to work on 32 bit machines & even then it is a bit dodgy.

nvidia-settings can do this from the GUI ...which you can not use..

If you can't login to console then we can make a script that runs as X server starts ..

Make a script
```
#!/bin/sh
export DISPLAY=":0.0"
nvidia-settings --query screens > dump.txt
nvidia-settings --query all >> dump.txt

```

make it executable & set it up to start in ~/.xinitrc

(does not work same from in script due to missing env variables..)

If you use Option "ModeDebug" "True" the nVidia X server will write the EDID as raw bin data to log file..
nvidia-xconfig --extract-edids-from-file=copy_of_Xorg.0.log --extract-edids-output-file=edid-dump.bin
Then have to find an EDID decoder tool..

---

### Post by dannyboy79 on 2012-12-04
> **BicyclerBoy said:**
> The read-edid only seems to work on 32 bit machines & even then it is a bit dodgy.

nvidia-settings can do this from the GUI ...which you can not use..

If you can't login to console then we can make a script that runs as X server starts ..

Make a script
```
#!/bin/sh
export DISPLAY=":0.0"
nvidia-settings --query screens > dump.txt
nvidia-settings --query all >> dump.txt

```

make it executable & set it up to start in ~/.xinitrc

(does not work same from in script due to missing env variables..)

If you use Option "ModeDebug" "True" the nVidia X server will write the EDID as raw bin data to log file..
nvidia-xconfig --extract-edids-from-file=copy_of_Xorg.0.log --extract-edids-output-file=edid-dump.bin
Then have to find an EDID decoder tool..
i don't have a file at ~/ named .xinitrc but I found one located at /etc/X11/xinit/  and it's named xinitrc
it looks like this now since I added what you stated.
```
#!/bin/bash

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
export DISPLAY=":0.0"
nvidia-settings --query screens > dump.txt
nvidia-settings --query all >> dump.txt
```

---

### Post by BicyclerBoy on 2012-12-04
The hidden home file .xintrc does not exist by default.
AFAIK It is the user specific X server init settings.

You might like to try adding this to your grub boot cmd:
video=vesa:off vga=normal
You can interrupt grub in boot process & add those strings by hand..
These might (at least) allow the console login to have video framebuffer output.

I figured out some better (cleaner) nvidia-settings cmd options that don't create so much cruft..but that can wait..

---

### Post by dannyboy79 on 2012-12-04
> **NikTh said:**
> Hi , 
Lets start from scratch and see ... 

First remove everything related to nvidia 
```
sudo apt-get remove  --purge nvidia-* 
sudo rm /etc/X11/xorg.conf
```Then add the X - Swat PPA , it has the 304.64 driver and install the driver,  and if I'm correct  is the latest (newer) driver that supports Nvidia 6200. 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get dist-upgrade
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
```The dist-upgrade command needed here in case  new driver needs some upgraded libraries. 

Reboot and see the results. 

If not work , give again the results of 
```
cat /var/log/Xorg.0.log
```Thanks
here's the resulting output from performing all your commands. I am about to restart the machine but first I think I need to blacklist all the nouveau things right?
[http://pastebin.com/11HDcU9v](http://pastebin.com/11HDcU9v)

---

### Post by dannyboy79 on 2012-12-04
> **BicyclerBoy said:**
> The hidden home file .xintrc does not exist by default.
AFAIK It is the user specific X server init settings.

You might like to try adding this to your grub boot cmd:
video=vesa:off vga=normal
You can interrupt grub in boot process & add those strings by hand..
These might (at least) allow the console login to have video framebuffer output.

I figured out some better (cleaner) nvidia-settings cmd options that don't create so much cruft..but that can wait..so wait, am I suppose to create the .xinitrc file or is it fine that added those commands to the /etc/X11/xinit/xinitrc file?

---

### Post by NikTh on 2012-12-04
> **dannyboy79 said:**
> here's the resulting output from performing all your commands. I am about to restart the machine but first I think I need to blacklist all the nouveau things right?
[http://pastebin.com/11HDcU9v](http://pastebin.com/11HDcU9v)

@dannyboy79 , have you tried to boot from an older kernel ? From the Official (for Ubuntu 10.04) 2.6.x-xx . Do you have the Original kernel ? I see only 3.0.x-xx at your results. 

Thanks

---

### Post by dannyboy79 on 2012-12-04
> **NikTh said:**
> @dannyboy79 , have you tried to boot from an older kernel ? From the Official (for Ubuntu 10.04) 2.6.x-xx . Do you have the Original kernel ? I see only 3.0.x-xx at your results. 

Thanksi can try booting to an older kernel again but if you look at my older pastbin's I was booting to 2.6.53-22 but I switched to a newer one thinking it would help. Here's the Xorg.0.log file from a fresh restart

[http://pastebin.com/CuE64BWJ](http://pastebin.com/CuE64BWJ)

and of course the screen is blue and it says DPMS SUSPEND. I got the info from ssh'ing into it as nothing brings it out of DPMS SUSPEND, NOTHING. lol

BicylerBoy, I can't find any file named dump.txt so it must not have worked by adding it only the /etc/X11/xinit/xinitrc file.


I booted it again and it just keeps filling with the following:
```
(II) Dec 04 22:21:11 NVIDIA(GPU-0): --- End of ModePool for Synaptics Inc 323-S11 (CRT-0): ---
(II) Dec 04 22:21:11 NVIDIA(GPU-0):
(II) XKB: reuse xkmfile /var/lib/xkb/server-8199213BFD9155D5FF97EC02B93E2C9FEC5A1EBB.xkm
(WW) Dec 04 22:21:16 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00005b7c)
(WW) Dec 04 22:21:23 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00005b7c)
(WW) Dec 04 22:21:26 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00006384)
(WW) Dec 04 22:21:33 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00006384)
(WW) Dec 04 22:21:36 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00006b8c)
(WW) Dec 04 22:21:43 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00006b8c)
(WW) Dec 04 22:21:46 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00007394)
(WW) Dec 04 22:21:53 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00007394)
(WW) Dec 04 22:21:56 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00007b9c)
(WW) Dec 04 22:22:03 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00007b9c)
(WW) Dec 04 22:22:06 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x000083a4)
(WW) Dec 04 22:22:13 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x000083a4)
(WW) Dec 04 22:22:16 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x000094f8)
(WW) Dec 04 22:22:23 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x000094f8)
(WW) Dec 04 22:22:26 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x00009d94)
(WW) Dec 04 22:22:33 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x00009d94)
(WW) Dec 04 22:22:36 NVIDIA(0): WAIT (2, 6, 0x8000, 0xffffffff, 0x0000a5e8)
(WW) Dec 04 22:22:43 NVIDIA(0): WAIT (1, 6, 0x8000, 0xffffffff, 0x0000a5e8)
```

---

### Post by NikTh on 2012-12-05
Hi ,
Two things I would try , 
1st , to add the Option DPMS FALSE in xorg.conf.. and see if is better . E.g.
```
Section "Device" 
Driver "nvidia"
Option "DPMS" "FALSE"
``` 
and restart X .
2nd , a newer kernel (newer than 3.0.x-xx) from ppa-mainline . If this is ACPI problem , the newer kernel might fix it. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by dannyboy79 on 2012-12-05
> **NikTh said:**
> Hi ,
Two things I would try , 
1st , to add the Option DPMS FALSE in xorg.conf.. and see if is better . E.g.
```
Section "Device" 
Driver "nvidia"
Option "DPMS" "FALSE"
``` 
and restart X .
2nd , a newer kernel (newer than 3.0.x-xx) from ppa-mainline . If this is ACPI problem , the newer kernel might fix it. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)adding
```
Section "Device" 
Driver "nvidia"
Option "DPMS" "FALSE"
```
didn't fix anything, still blue screen that says DPMS SUSPEND. Looking at the mainline ppa kernels all the lucid kernels are no where near the 3.0.x-xx so I am not sure who to do that. The latest kernel I have in lucid repo's is 3.0.0-28-generic.

Any other suggestions? What is that mention of a xkm file? Can I try to rename that xkm file so I tries to create a new one? Also, what about trying to use my own edid file? I am not sure exactly how to do that though, some google search reveal some info but not exactly how to do it. Or what about creating my own modelines? I just don't understand why 12.04.1 froma  live usb stick uses nouveau and has a resolution of 1440x900 but I can't seem to duplicate that with 10.04.4.

This is just maddening!!

---

### Post by NikTh on 2012-12-05
Lets try another configuration that might help . Ohh and Option "DPMS" "FALSE" is wrong. The correct is Option "DPMS" "false" (lower case). 
OK. Lets try below...

First remove the current xorg.conf file and create a new.
```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```Then create a new configuration file inside /xorg.conf.d/ (if the folder does not exist, create it)
```
sudo mkdir /etc/X11/xorg.conf.d/
```Then ```
gksudo gedit /etc/X11/xorg.conf.d/10-monitor.conf
```add these lines inside
```
Section "Monitor"
    Identifier "LVDS0"
    Option "DPMS" "false"
EndSection

Section "ServerLayout"
    Identifier "ServerLayout0"
    Option "BlankTime"  "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection
```and save the file.** Important here** is to replace LVDS0 , with your actual monitor . E.g VGA1 or whatever it is.. find it with ```
xrandr
```Save the file and reboot. 

Thanks

---

### Post by dannyboy79 on 2012-12-05
> **NikTh said:**
> Lets try another configuration that might help . Ohh and Option "DPMS" "FALSE" is wrong. The correct is Option "DPMS" "false" (lower case). 
OK. Lets try below...

First remove the current xorg.conf file and create a new.
```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```Then create a new configuration file inside /xorg.conf.d/ (if the folder does not exist, create it)
```
sudo mkdir /etc/X11/xorg.conf.d/
```Then ```
gksudo gedit /etc/X11/xorg.conf.d/10-monitor.conf
```add these lines inside
```
Section "Monitor"
    Identifier "LVDS0"
    Option "DPMS" "false"
EndSection

Section "ServerLayout"
    Identifier "ServerLayout0"
    Option "BlankTime"  "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection
```and save the file.** Important here** is to replace LVDS0 , with your actual monitor . E.g VGA1 or whatever it is.. find it with ```
xrandr
```Save the file and reboot. 

Thanksxrandr output is 
```
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  

```

UPDATE: I used a live usb stick of 12.04.1 and this is what xrandr returned
```
xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1360x768       60.2*+   60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       84.9     74.9     59.8  
   1152x864       75.0  
   1280x768       84.8     74.9     59.9     60.1  
   1280x720       60.0  
   1024x768       85.0     75.1     75.0     70.1     60.0  
   800x600        85.1     72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        85.0     75.0     72.8     60.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
```
so i put VGA-1 within that 10-monitor.conf file and the system gets to the login manager but is unresponsive, no mouse movement or keyboard, can't go to tty sessions. 

I should mention that I have tried adding those parameters to the server  layout section of a xorg.conf file and it made no impact on the DPMS SUSPEND screen.. I am stumped!!  I should also note that when there is no xorg.conf file this is what an Xorg.0.log file looks like, notice the VESA mentions, also I believe nouveau is being loaded per lsmod but I have it blacklisted within a file within /etc/modprobe.d/   very strange.
[http://pastebin.com/n4nz9rHA](http://pastebin.com/n4nz9rHA)

---

### Post by dannyboy79 on 2012-12-06
bump, please help. :)

---

### Post by dannyboy79 on 2012-12-06
please help, where did bicyclerboy and NikJT go?

---

### Post by dannyboy79 on 2012-12-08
would really like some help with this. it's now entering DPMS SUSPEND with the nouveau driver. I gave up on 10.04.4 and installed Linux Mint 14 with Mate. Here's the Xorg.0.log file
[http://pastebin.com/sA8wCdp3](http://pastebin.com/sA8wCdp3)

I have no xorg.conf file.

---

### Post by BicyclerBoy on 2012-12-08
Minor points:
- post #22 the cmd lines have to go after the xserver has started..maybe that's where it when wrong.
- the posted Xorg.0.log is clipped; end is missing
- "0" & "FALSE" & "false" & "False" are equivalent in xorg.conf
- is possible the old /etc/xorg.conf.d/ folder contents is ignored.


xrandr is an Xorg tool & uses VGA-0 VGA-1 LVDS etc namespace.
nouveau uses this namespace.

nVidia driver uses CRT-0 CRT-1 DFP-0 etc namespace.
rrandr uses nVidia namespace.
(the PCI address nameapace is also inconsistent).
So can not use VGA-1 in xorg.conf with nVidia X server driver.

Because the log is clipped, can't tell what modeline was chosen..
But looks like 1360x768@60

Could try adding this somewhere..
xrandr --output CRT-1 --mode 1280x1024 --rate 60.0

At what point in the boot/greeter/login proces does screen go into suspend?
(with nouveau driver)..

---

### Post by dannyboy79 on 2012-12-08
> **BicyclerBoy said:**
> Minor points:
- post #22 the cmd lines have to go after the xserver has started..maybe that's where it when wrong.
- the posted Xorg.0.log is clipped; end is missing
- "0" & "FALSE" & "false" & "False" are equivalent in xorg.conf
- is possible the old /etc/xorg.conf.d/ folder contents is ignored.


xrandr is an Xorg tool & uses VGA-0 VGA-1 LVDS etc namespace.
nouveau uses this namespace.

nVidia driver uses CRT-0 CRT-1 DFP-0 etc namespace.
rrandr uses nVidia namespace.
(the PCI address nameapace is also inconsistent).
So can not use VGA-1 in xorg.conf with nVidia X server driver.

Because the log is clipped, can't tell what modeline was chosen..
But looks like 1360x768@60

Could try adding this somewhere..
xrandr --output CRT-1 --mode 1280x1024 --rate 60.0

At what point in the boot/greeter/login proces does screen go into suspend?
(with nouveau driver)..
it goes into DPMS SUSPEND at completely random times. With Mint 14 w/ Mate I can boot up open Google chrome, a terminal and be working and then out of no where it goes into DPMS SUSPEND. After logging in I have issued xet -dpms and checked xset -q and it states DPMS is disabled, doesn't matter, still goes into DPMS SUSPEND mode. The nouveau driver is not really working anyway because kdenlive is completely garbled and I can't see what I am doing. So the nvidia binaries go straight into DPMS SUSPEND where at least nouveau allows me to work for a tiny bit. Here's a newer Xorg.0.log file, i don't know why it's cutting it off but that's the complete log file
[http://pastebin.com/aTqmTA7G](http://pastebin.com/aTqmTA7G)
Here's a screenshot I took while it was still working
[IMG]https://lh6.googleusercontent.com/-cI-bqjN6vSE/UMOUzc9t3pI/AAAAAAAAArQ/aBU34vsjib4/s912/Screenshot.png[/IMG]



Here's a youtube video showing the problem.
[http://www.youtube.com/watch?v=LL8cBPqQE34](http://www.youtube.com/watch?v=LL8cBPqQE34)

---

### Post by BicyclerBoy on 2012-12-08
The screen corruption & the random nature of the "suspend" (heat/time?) starts to suggest h/w problems with GPU packaging or memory failing.

The nVidia FX5200 era was plagued with dodgy SMT assembly.
nVidia settled out-of-court with Apple.

The best nVidia AGP card is the old 1st gen 8400 or..an old PCI card..

---

### Post by dannyboy79 on 2012-12-08
wouldn't there be something in any log file about a GPU lockup or something if it were related to heat?

I just got the GeForce 8400 GS PCIe card so I am about to find out if it'll work with this old Asrock 775Dual-VSTA motherboard.


UPDATE: i installed the 8400 GS within the 1 PCIe slot which runs @4x, set the bios to video card being PCIe and disabled PCIE Downstream Pipeline and PCIE VC1 Request Queue within the BIOS per what I read on a lot of forums regarding these "DUAL" Asrock motherboards. I can report that everything is working great! I am running at 1440x900 using the Nvidia 304.51 version from Mint's repos. I wonder if I should push it and install the latest 310.19 version from the website, IF it will give me greater video game frames per second it may be worth a shot. There's a whole mess of changes in the release highlights for that driver. I'll post back if I do that but for now I get direct rendering
glxinfo | grep direct
direct rendering: Yes
GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

and glxgears shows:
302 frames in 5.0 seconds = 60.306 FPS
300 frames in 5.0 seconds = 59.885 FPS
300 frames in 5.0 seconds = 59.885 FPS
300 frames in 5.0 seconds = 59.885 FPS

---

### Post by BicyclerBoy on 2012-12-08
I'm not sure fatal memory errors in GPU would show up in normal logs.
My guess is there would need to be a special GPU memory test.

Sorry, I thought you only had an AGP slot mobo..
I still use a core2duo LGA775 mobo for HTPC.
An iCPU would use half the power & have much more transcoding grunt tho.

See if you have VDPAU working in MythTV or mplayer..

---

### Post by dannyboy79 on 2012-12-08
> **BicyclerBoy said:**
> I'm not sure fatal memory errors in GPU would show up in normal logs.
My guess is there would need to be a special GPU memory test.

Sorry, I thought you only had an AGP slot mobo..
I still use a core2duo LGA775 mobo for HTPC.
An iCPU would use half the power & have much more transcoding grunt tho.

See if you have VDPAU working in MythTV or mplayer..
i don't have a mythtv frontend installed on this machine because my backend is 0.23.1+fixes so the frontend that would be installed would be way newer and there'd be a protocol mismatch I am sure.

I am going to upgrade my Mythbuntu backend very soon though now that I know the analog PVR-? cards have been patched so they don't record zero byte files anymore.

I just ran mplayer from a command line on a file I created with kdenlive rendered to h264, this is the ouput
```
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
**[vdpau] Error when calling vdp_device_create_x11: 1**
[***] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 335.3 kbit/21.83% (ratio: 41907->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
A:  14.3 V:  14.4 A-V: -0.032 ct:  0.000   0/  0  5%  2%  0.4% 0 0 

Exiting... (Quit)

```
SO it doesnt appear that VDPAU is working, how do I get it working?

---

### Post by BicyclerBoy on 2012-12-09
Install:
libvdpau
vdpauinfo
vdpau-va-driver  (VA-API for VLC etc)
vainfo

Run the *info files to test configuration.

Nouveau driver has some initial VDPAU/VA-API support.
Requires proprietary driver for full potential.

---

### Post by soal on 2012-12-10
I have some problems with Nvidia Geforce 6200 256m / 128 bit AGP
recently I changed my widows XP and now the graphic card (as you mentioned above) is not correctly work because its installation file was missed and now I cannot install it. Although I checked this problem through Nvidia.com and also Gforce.com but at firs these sites cannot identify my card. Please help me in order to resolve this problem if you can.

---

### Post by dannyboy79 on 2012-12-10
> **soal said:**
> I have some problems with Nvidia Geforce 6200 256m / 128 bit AGP
recently I changed my widows XP and now the graphic card (as you mentioned above) is not correctly work because its installation file was missed and now I cannot install it. Although I checked this problem through Nvidia.com and also Gforce.com but at firs these sites cannot identify my card. Please help me in order to resolve this problem if you can.not sure what you're asking. Are you using Windows XP? If so, can't help here as this is an Ubuntu forum.

If you're using ubuntu, which driver are you trying to use? Nvidia-current? Binary from Nvidia website? Nouveau?

---

### Post by NikTh on 2012-12-22
I've had problems with login , sorry for the delay.. (was my fault , forums staff helped me to solve this). 

What happened with your problem ? I saw this corrupted picture you uploaded. It seems to me like a fault of GPU.. memory fault ? or power consumption fault ? 

Have you managed to fixed it ?

---

### Post by dannyboy79 on 2012-12-22
i am thinking it was a GPU overheating issue. I purchased a GeForce 8400 GS 1GB DDR3 PCIe card and all is well.

---

### Post by NikTh on 2012-12-22
> **dannyboy79 said:**
> i am thinking it was a GPU overheating issue. I purchased a GeForce 8400 GS 1GB DDR3 PCIe card and all is well.

Yes .. these are good news.. I mean you fixed it  .. even with the new purchased card. 

:)

---

