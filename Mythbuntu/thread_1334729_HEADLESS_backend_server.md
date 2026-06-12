---
title: "HEADLESS backend server"
date: 2009-11-22
forum: Mythbuntu
---

### Post by bubu2000 on 2009-11-22
Hi all,

 I have just upgraded from Xubuntu to Mythbuntu 9.10 and I am having problems configuring a headless mythbuntu backend server like I could do with previous mythbuntu versions :

 Xfce desktop refuses to back off (it obviously loads with a new script, which I have no idea where it resides)..

And the server will not boot past a certain point without a monitor attached to it...

Any ideas will be greatly appreciated...

---

### Post by SiHa on 2009-11-23
It might be because the X Server can't validate any resolutions (although, in my experience, it then just defaults to low-rez).
I had a similar issue getting my Frontend to boot into the right resolution when the TV is turned off.

If you have nVidia gfx, and have a monitor connected for setup:

Run nvidia settings```
sudo nvidia-settings
```run with sudo so that the process has sufficient permissions to write to /etc/X11/.

On one of the tabs there is a 'Aquire EDID' button. Click this, and specify the location to save to (something like /etc/X11/edid.bin)

Add the following to the "Screen" section of your xorg.conf:
```
Option      "UseDisplayDevice" "DFP-0"
Option      "CustomEDID" "DFP-0:/etc/X11/edid.bin"
```
-changing DFP-0 to whatever nVidia Settings reports as the active device.

This should give the X server a display mode it can use, and also has the advantage that when you someday need to connect a monitor (and let's face it, you will) the server will correctly setup already.

If you're unfamiliar with xorg, maybe backup your xorg.conf first, so you can drop to a root prompt at boot and restore it if the changes make things worse!

---

### Post by bubu2000 on 2009-11-23
If you have nVidia gfx,
[COLOR=Red]THERE IS AN INTEL INTEGRATED ADAPTOR ,NO NVIDIA[/COLOR]


On one of the tabs there is a 'Aquire EDID' button. Click this, and specify the location to save to (something like /etc/X11/edid.bin)

Add the following to the "Screen" section of your xorg.conf:
[COLOR=Red] THERE IS NO XORG.CONF IN THE CURRENT UBUNTU RELEASE[/COLOR]...

[COLOR=Red]CAN I GENERATE ONE AND FORCE THE USE OF IT?
THANKS AGAIN[/COLOR]

---

### Post by uncle hammy on 2009-11-23
> **bubu2000 said:**
> [COLOR=Red] THERE IS NO XORG.CONF IN THE CURRENT UBUNTU RELEASE[/COLOR]
Really? xorg.conf was installed on all 3 of my 9.10 installs, albeit a very basic one...

---

### Post by bubu2000 on 2009-11-23
> **uncle hammy said:**
> Really? xorg.conf was installed on all 3 of my 9.10 installs, albeit a very basic one...
[COLOR=Red]
UHAMMY, I HAVE NO IDEA HOW YOU GOT ONE, BUT IT LOOKS LIKE THE NEW NORM IS FOR UXA OR WHATEVER...HAVE A LOOK
[http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)
[http://ubuntuforums.org/showthread.php?t=1221226](http://ubuntuforums.org/showthread.php?t=1221226)[/COLOR]

---

### Post by SiHa on 2009-11-24
> **uncle hammy said:**
> Really? xorg.conf was installed on all 3 of my 9.10 installs, albeit a very basic one...

And on both of mine, and they are used. Maybe nVidia settings generates one.

Anyway, sorry, limited exposure to Intel. I had integrated Intel on my old frontend, and went nVidia in the end to solve the same problem.

---

### Post by bubu2000 on 2009-11-24
> **siha said:**
> and on both of mine, and they are used. Maybe nvidia settings generates one.

Anyway, sorry, limited exposure to intel. I had integrated intel on my old frontend, and went nvidia in the end to solve the same problem.

[COLOR=Red]i went on and generated and installed an xorg.conf (driver=vesa etc.) file inside x11, which is seen and used, but -WITHOUT A MONITOR- the pc will still not boot past ..whatever (i cant see) , early enough to not load mythbackend or even network...
I am thinkinf of going back to 8.10  ...
Jee, this version is a total headache, they ve mucked up grub, they ve removed "services", they hid the Xfce init script, removed xorg.conf, what next..? ..an os for total idiots perhaps..[/COLOR]

---

### Post by tartan-caber on 2009-11-24
I've a headless server running backend only,built in the following manner.

Installed Ubuntu 9.10 server
Installed mysql-server
Installed mythtv-backend mythtv-database

To run mythtv-setup, I use one of two options

1. M$ Windoze laptop with cygwyn using putty with X forwarding
2. Mythbuntu frontend cli: ssh -X <user>@<backend> /usr/bin/mythtv-setup

---

### Post by bubu2000 on 2009-11-24
> **tartan-caber said:**
> I've a headless server running backend only,built in the following manner.

Installed Ubuntu 9.10 server
Installed mysql-server
Installed mythtv-backend mythtv-database

To run mythtv-setup, I use one of two options

1. M$ Windoze laptop with cygwyn using putty with X forwarding
2. Mythbuntu frontend cli: ssh -X <user>@<backend> /usr/bin/mythtv-setup

[COLOR=Red]I can manage that, thanks [tartan-caber]("http://ubuntuforums.org/member.php?u=868455").
One thing about option1: I usually run putty from within WINDowZ. Can I run X like that, without Cygwin, 'cause i dont think i will be installing Cygwin on my slow old laptop..
And before you go, I dont quite get your #2 option -is this a command i need to run from another linux machine running myth-frontend? 'Cause this will be the easiest option by far !! Thanks again -[/COLOR]

---

### Post by grandtheftautumn on 2009-11-24
I had the same problem on my Dell Dimension 3000 - Intel integrated video, got stuck during boot, etc. 

I solved the problem by adding a graphics card to the PCI slot - don't know why or how it worked, but it worked. I don't think I even had to turn off the integrated adapter in the BIOS. Now my system boots up normally without a monitor connected.

Give that a shot.

---

### Post by bubu2000 on 2009-11-24
> **grandtheftautumn said:**
> I had the same problem on my Dell Dimension 3000 - Intel integrated video, got stuck during boot, etc. 

I solved the problem by adding a graphics card to the PCI slot - don't know why or how it worked, but it worked. I don't think I even had to turn off the integrated adapter in the BIOS. Now my system boots up normally without a monitor connected.

Give that a shot.

[COLOR=Red]Will DO STRAIGHT AWAY and let you know, THANKS grandtheftautumn.[/COLOR]

---

### Post by bubu2000 on 2009-11-25
Yea, it worked in the end (after a few restarts) , but now other things arent working...
 I am getting rid of 9.10   ...it's a fiasko. Thanks guys.

---

