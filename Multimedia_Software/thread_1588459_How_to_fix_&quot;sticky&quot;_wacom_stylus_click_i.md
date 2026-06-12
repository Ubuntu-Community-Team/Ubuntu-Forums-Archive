---
title: "How to fix &quot;sticky&quot; wacom stylus click in Ubuntu 10.10"
date: 2010-10-04
forum: Multimedia Software
---

### Post by stephanecharette on 2010-10-04
I don't know when it started, but my Wacom stylus clicks haven't been working right.  It seems to do the "click down" correctly, but hasn't always been doing the "click up" when I release the pressure on my stylus.  This leads to a bunch of problems when Ubuntu thinks I'm holding down the mouse button, when in reality I'm not holding anything down.

I have an older Wacom GD (Intuos 1) USB tablet.  I finally figured out how to fix the problem tonight.  Here is what I did:

1) Determine that "name" of the tablet:

[INDENT][FONT="Courier New"]lsusb | grep -i wacom
Bus 002 Device 003: ID 056a:0022 Wacom Co., Ltd Intuos 9x12[/FONT][/INDENT]

So in my case, I'm dealing with an Intuos 9x12 tablet.  This becomes important at step #3.

2) Edit the right xorg.conf file:

[INDENT][FONT="Courier New"]cd /usr/share/X11/xorg.conf.d/
sudo gedit 50-wacom.conf[/FONT][/INDENT]

3) At the end of this file, add the following block:

[INDENT][FONT="Courier New"]Section "InputClass"
[INDENT]Identifier "Intuos 9x12"
MatchProduct "Intuos 9x12"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
Option "Type" "stylus"
Option "Button2" "3"
Option "Mode" "Absolute"
Option "TPCButton" "off"
Option "Threshold" "200"
[/INDENT]EndSection[/FONT][/INDENT]

4) Log back out and back in, or restart your Ubuntu system.

Note the following special values:

A) [FONT="Courier New"]MatchProduct "Intuos 9x12"[/FONT] must be the name of the tablet discovered at step #1.  If the name doesn't match, the section wont load and none of the changes you are trying to make will take effect.

B) [FONT="Courier New"]"Button2" "3"[/FONT] means the bottom of the rocker switch on the stylus works like a right-mouse-button.

C) [FONT="Courier New"]"TPCButton" "off"[/FONT] means when I press the right-mouse-button, I don't have to click at the same time.  I normally just "hover" the pen over the tablet while I'm right-mouse-clicking.  If you prefer the other style, set that to "on".

D) [FONT="Courier New"]"Threshold" "200"[/FONT] is the click threshold.  I think the default is something like 27.  If you set it to "1", then all you have to do is hover over the tablet and it will think you clicked.  If you set it to "10000" then no matter how hard you press you wont get a click.  I found "200" seems right for me and my tablet.

This problem started just recently when I was still on Ubuntu 10.04.  I upgraded to 10.10 beta to see if the problem would go away, but it didn't.  I hope the solution I've described helps out other people.

Stéphane Charette

---

### Post by statmech on 2011-03-12
Hi I have a Wacom Bamboo Fun CTH-661/S.  I encountered the same sticky stylus you described, i.e., when I click at the top taskbar of jarnal (similar to Windows Journal), the cursor just got stuck there.  I had to move the pen up, beyond the top of the window to release the cursor. In addition, after I wrote on jarnal, and lifted the pen, the cursor got stuck in the page.  Again, I needed to move the pen up and beyond the top border of the jarnal window to release the cursor.

I tried to follow your step, but the output of the lsusb command did not give the name of the devide, just the ID number:

[INDENT]vql@io4: tcsh 25> lsusb | grep Wacom
Bus 007 Device 002: ID 056a:00d3 Wacom Co., Ltd 
vql@io4: tcsh 26>[/INDENT]

What should I put in the line "Identifier" ?

Note that linuxwacom used to work for ubuntu 10.04 until there is a recent upgrade of the linux kernel that use a new version of X11.  Some web site said that linuxwacom is no longer working for the new X11 version; one has to use xf86-input-wacom; but my installation of xf86-input-wacom did not resolve the sticky stylus problem.

Thanks for any help.

---

### Post by gulincho on 2011-03-23
You cat get your wacom identifier by this command:

```
pablo@melli:~$  xsetwacom --list

```

my output is:
    
```
Wacom BambooFun 6x8 stylus STYLUS
Wacom BambooFun 6x8 eraser ERASER    
Wacom BambooFun 6x8 cursor CURSOR    
Wacom BambooFun 6x8 pad PAD       

```

Regards

---

### Post by cnr_roxx on 2011-04-08
@gulincho

> $  xsetwacom --list

This command returns no result for wacom driver compiled by myself (which is the only solution for Bamboo Fun Pen & Touch tablet series).

Does anybody know how to remove this "sticky" effect for Bamboo Fun Pen & Touch (CTH-661/S) in Ubuntu 10.04?

---

### Post by cnr_roxx on 2011-04-11
Ok, I've solved this too :)

1. Command "**$xsetwacom --list**" returned no result in my case because I was using "wacom kernel usb driver" (wacom.ko)compiled by myself but the "x driver" (**xf86-input-wacom**) originated from Lucid distribution and this driver doesn't recognize Bamboo Fun Pen & Touch tablets. So the solution was to compile also the second driver and here is the whole great tutorial for this: [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

2. But I've chosen another way: I've simply upgraded my system to Maverick (10.10) and then installed 2 packages **wacom.dkms** and **xserver-xorg-input-wacom** from excelent Irie's private repository: **ppa:irie/wacom**. This "x driver" doesn't even require re-configuring after installation (as in [stephanecharette]("http://ubuntuforums.org/member.php?u=349009")'s original post) and there is no "sticky effect" out-of-the-box.

---

### Post by kc7rwx on 2011-07-13
Fixed my problems.

Thank you:)

---

### Post by VaclavC on 2011-08-04
I have the same problem with Intuos 3 and Natty but this fix does not work for me. Setting TCPButton (TabletPCButton, now) makes no difference. When I try to change threshold, I must hardly press on pen, but result is the same: it generates ButtonPress event but does not generate ButtonRelease. It sends ButtonRelease when I put away pen from tablet. Other buttons work fine. Here is information about my hw:

```

xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Chicony USB Wireless HID Receiver       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; KYE NetScroll Eye                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 stylus                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 eraser                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                   	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Chicony USB Wireless HID Receiver       	id=8	[slave  keyboard (3)]
    &#8627; Chicony USB Wireless HID Receiver       	id=9	[slave  keyboard (3)]

```

```

xsetwacom --list devices
Wacom Intuos3 6x8 stylus        	id: 12	type: STYLUS    
Wacom Intuos3 6x8 eraser        	id: 13	type: ERASER    
Wacom Intuos3 6x8 cursor        	id: 14	type: CURSOR    
Wacom Intuos3 6x8 pad           	id: 15	type: PAD

```

I'am running kernel 2.6.39-0-generic from Natty and compiled 0.11.99 wacom driver (stock Natty driver also has this issue).

Anybody has any ideas?

---

### Post by Favux on 2011-09-06
Has anyone tried replacing the stylus tip or nib?

---

### Post by VaclavC on 2011-09-06
Yes, it was my first idea: that my pen is broken. But it didn't help.

---

### Post by mylhause on 2012-06-12
First of all, sorry for bring this topic from the deeper dungeons of the forum.


Ok guys, i don't even know how to use this, but i'm here to try some 
helping

I got problems like this, my pen could hover and move the cursor, but when i 
touch the table, the cursor stuck. This happend when i installed an update to 
ubuntu Kernel. 
I'm very newb and i'm just beginning in Linux, so i can't say clearly how this 
hppens, but i got the solution after some days of researching.
I solved my problem by downgrading the xorg to the following version:

xserver-xorg-input-wacom ver.1:0.10.5-0ubuntu4

The problematic version was xserver-xorg-input-wacom ver.1:0.10.11-0ubuntu7, and 
i uninstalled it and forced the installation of the older version. It worked as 
a glove when i restarted my computer

So, if you are experiencing this kind of problem on Lucid, try this and pass 
this message forward.

Cya guys

(sorry my bad english)

---

