---
title: "Problem with NVIDIA 8800 GTS"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by Roig on 2007-11-02
Hello!

I have this problem:

When i do:

glxinfo | grep rendering

it says me:

dani@dani-habitacio:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I have an Nvidia 8800 GTS and Ubuntu 7.10, I installed the restricted drivers using the tool that comes with ubuntu. All worked fine, i have compiz working very well. 

My second problem is when i try to play Unreal Tournament 2004 some textures are black and glitches.. and i want to install World of Warcraft too but i can't because (direct rendering: No).. Well i don't know what i have to do to enable direct rendering. 

Anyone can help me? 

P.D. Sorry for my bad english.

---

### Post by Roig on 2007-11-02
Please? Anyone? 

You need more info?

---

### Post by American_Outcast on 2007-11-02
I am using a Nvidia 8400. It works fine for me. Maybe if you try and unistall the drivers and reinstall them again? Also have you tried sudo nvidia-settings in the terminal?


Edit: Don't worry about your English, it is fine :)

---

### Post by Roig on 2007-11-02
Ops!

When i did: 

sudo nvidia-settings

it opens the NVIDIA X Server Settings panel but with this error window too:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

but i ran nvidia-xconfig with sudo, this is root, no? >_<

What i have to edit and more important which file? O_o

Thanks for the help! :)

---

### Post by American_Outcast on 2007-11-02
Give me one sec and I will look up all that I have installed for nvidia and post it here.

---

### Post by American_Outcast on 2007-11-02
This is what I have installed for nvidia in the synaptic package manager.

nvidia-glx-new
nvidia-kernel-common
xserver-xorg-video-nv


This is what my etc>X11>xorg.conf file looks like,

> Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection
Hope this helps.

Edit: Remember to back up the xorg.conf file before you edit it :)

---

### Post by Roig on 2007-11-02
in synaptic i have:

Nvidia-glx-new
nvidia-kernel-common
xserver-xorg-video-nv

the same :)

and in xorg.conf:

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "Module"
	Load		"glx"
EndSection


>_< i don't know why it's not working..

---

### Post by American_Outcast on 2007-11-02
> **Roig said:**
> in synaptic i have:

Nvidia-glx-new
nvidia-kernel-common
xserver-xorg-video-nv

the same :)

and in xorg.conf:

Section "Device"
    Identifier    "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
EndSection

Section "Module"
    Load        "glx"
EndSection


>_< i don't know why it's not working..

I think I see the differences with our cards. Is yours a regular PCI card? Mine is an PCIE card.

---

### Post by Roig on 2007-11-02
> **American_Outcast said:**
> I think I see the differences with our cards. Is yours a regular PCI card? Mine is an PCIE card.

Yes yes, it's a PCIE card.

---

### Post by American_Outcast on 2007-11-02
> **Roig said:**
> Yes yes, it's a PCIE card.

Then that may be the problem. The Busid: PCI line, I don't have that in mine. Try something like mine after you back up the xorg.conf file, just in case, lol, and see if that helps.

---

### Post by Roig on 2007-11-02
> **American_Outcast said:**
> Then that may be the problem. The Busid: PCI line, I don't have that in mine. Try something like mine after you back up the xorg.conf file, just in case, lol, and see if that helps.

Can you specify what to edit exactly ? I am "new" to linux and i know nothing about that >_< ^^U. 

i have to replace this line

Busid "PCI:1:0:0" 

for ?

oh, and when i replace that, what i have to do? i suppose i will have to restart something but dont know how to xD **** im noob.

Thanks!

---

### Post by American_Outcast on 2007-11-02
> **Roig said:**
> Can you specify what to edit exactly ? I am "new" to linux and i know nothing about that >_< ^^U. 

i have to replace this line

Busid "PCI:1:0:0" 

for ?

oh, and when i replace that, what i have to do? i suppose i will have to restart something but dont know how to xD **** im noob.

Thanks!

Yes. Take that line out, the busid: pci and see if that helps at all. Back up the xorg.conf file. If it doesn't work and messes up the screen you can boot the livecd and just replace the xorg.conf you edited with the backed up xorg.conf file you created. I am not completely sure if this is the problem but that is one thing I noticed between our two xorg.conf entries for nvidia . If anyone else has any thoughts please jump in.

---

### Post by Roig on 2007-11-02
Uhm before that, i found something in nvidia forums, should i try this?

[http://www.nvnews.net/vbulletin/showthread.php?p=1368304#post1368304](http://www.nvnews.net/vbulletin/showthread.php?p=1368304#post1368304)

"yes! I have remove xserver-xgl and now it works!

Thanks!

I'll report this problem to ubuntu's folks

Julio" 

Removing the xserver-xgl ?

---

### Post by American_Outcast on 2007-11-02
> **Roig said:**
> Uhm before that, i found something in nvidia forums, should i try this?

[http://www.nvnews.net/vbulletin/showthread.php?p=1368304#post1368304](http://www.nvnews.net/vbulletin/showthread.php?p=1368304#post1368304)

"yes! I have remove xserver-xgl and now it works!

Thanks!

I'll report this problem to ubuntu's folks

Julio" 

Removing the xserver-xgl ?

Yes. Always use the information there first and see if it works. Just make a backup file just in case their solution doesn't work or makes it worse. I am guessing at what they problem may be. I just know how mine looks, xorg.conf, and that it works perfectly.

---

### Post by Roig on 2007-11-02
Oh hell! Worked...

dani@dani-habitacio:~$ glxinfo | grep rendering
direct rendering: Yes
dani@dani-habitacio:~$ 

Only removing the xserver-xgl >_<

Thanks for your time american_outcast! :)

Problem solved.

---

### Post by American_Outcast on 2007-11-02
> **Roig said:**
> Oh hell! Worked...

dani@dani-habitacio:~$ glxinfo | grep rendering
direct rendering: Yes
dani@dani-habitacio:~$ 

Only removing the xserver-xgl >_<

Thanks for your time american_outcast! :)

Problem solved.

Your welcome. I am glad you got it working.

---

