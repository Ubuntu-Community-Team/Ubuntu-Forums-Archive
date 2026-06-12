---
title: "Install video drivers Intel"
date: 2008-09-23
forum: Multimedia Software
---

### Post by chanfle on 2008-09-23
hi...
how i can install video drivers intel....
because not appear anything on the enable driver....
i waiting your response

---

### Post by Whiffle on 2008-09-23
Which version of Ubuntu?  If its 8.04 or even 7.10, I think, they should already be installed.

---

### Post by chanfle on 2008-09-23
> **Whiffle said:**
> Which version of Ubuntu?  If its 8.04 or even 7.10, I think, they should already be installed.

I use ubuntu 8.04....

---

### Post by Whiffle on 2008-09-23
Go to Applications > Accessories > Terminal and run

glxinfo | grep direct


If it says "direct rendering: Yes", they're installed.

---

### Post by chanfle on 2008-09-23
> **Whiffle said:**
> Go to Applications > Accessories > Terminal and run

glxinfo | grep direct


If it says "direct rendering: Yes", they're installed.

ok...appear "yes"
but this is my problem....
"yesterday I buyed a new PC, Dell inspiron 530s, Pentium 1.8ghz dual core, 3 gigas ram, 250 hdd, Integrated Intel Graphics Media Accelerator 3100.
when i created a new user, the 2 accounts work very fine desktop effects, but when i logon with other user the desktop effects disable are disable, and I try enable and appear me the next message: "Desktop effects could not be enable"
But with my user the effects is enable....
How i can fix this issue...???"
and this is my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

what i need to do...???

regards

---

### Post by Whiffle on 2008-09-23
Sounds to me like the user you added may not be in the "video" group.

In terminal, do:

groups <name of user>

It should return a list of the groups that the user is in.  It might need to be run with sudo, I'm not sure (not on Ubuntu right now).  

If the video group isn't listed, I think the command

sudo gpasswd -a <name of user> video

should add them to the correct group.  There is probably a way to do this by going through the Administration menu, but I don't have one of those in front of me at the moment.  Once they're added, they'll have to logout/login for it to take effect.

---

### Post by chanfle on 2008-09-23
> **Whiffle said:**
> Sounds to me like the user you added may not be in the "video" group.

In terminal, do:

groups <name of user>

It should return a list of the groups that the user is in.  It might need to be run with sudo, I'm not sure (not on Ubuntu right now).  

If the video group isn't listed, I think the command

sudo gpasswd -a <name of user> video

should add them to the correct group.  There is probably a way to do this by going through the Administration menu, but I don't have one of those in front of me at the moment.  Once they're added, they'll have to logout/login for it to take effect.

ok let me check...and post later....on this moment I'm at work

thanks

---

### Post by chanfle on 2008-09-23
> **chanfle said:**
> ok let me check...and post later....on this moment I'm at work

thanks

after type groups <user>
return this
```
root adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse admin

```
so...what i do?

---

### Post by chanfle on 2008-09-23
> **chanfle said:**
> after type groups <user>
return this
```
root adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse admin

```
so...what i do?

any update...???

---

### Post by chanfle on 2008-09-23
> **chanfle said:**
> any update...???

i check the log .xsession-errors:
 
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA contr
oller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: Initializing nautilus-share extension
seahorse nautilus module initialized
present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn'
t going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.
0

```

i hope this help us....

---

### Post by Whiffle on 2008-09-23
According to this, it might be fixed by doing the xorg reconfigure:
[http://ph.ubuntuforums.com/showthread.php?t=895902](http://ph.ubuntuforums.com/showthread.php?t=895902)

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by chanfle on 2008-09-24
> **Whiffle said:**
> According to this, it might be fixed by doing the xorg reconfigure:
[http://ph.ubuntuforums.com/showthread.php?t=895902](http://ph.ubuntuforums.com/showthread.php?t=895902)

sudo dpkg-reconfigure -phigh xserver-xorg

maybe the intel video card not uspport 2 sessions witj compiz and desktop effects, hardy not have drm multi-master...
any comments...???

---

