---
title: "help a newb put in a 5200?"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by pantsroptional on 2007-01-08
I'm running Ubuntu 6.06, and I'm trying to install a Nvidia FX 5200 PCI. I opened up my case and put it in, restarted and I'm getting a blank screen when I attach my monitor to the card. I'm using my on board video right now. I tried the tutorial in the sticky and I could not get anything to work. I think I must be doing something stupid since this is supposedly one of the easiest cards to get working under linux (which is why I bought it). :-k

---

### Post by teaker1s on 2007-01-08
first disable onboard vga in bios
then you will need recovery mode at grub screen
login in txt mode
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

follow instructions choose "nv" as driver

[COLOR="Red"]sudo reboot[/COLOR]

you now should have working gui, the "nv" driver is not open gl if you need open gl search nvidia open gl in forums:mrgreen:

---

### Post by pantsroptional on 2007-01-09
> **teaker1s said:**
> first disable onboard vga in bios
then you will need recovery mode at grub screen
login in txt mode
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

follow instructions choose "nv" as driver

[COLOR="Red"]sudo reboot[/COLOR]

you now should have working gui, the "nv" driver is not open gl if you need open gl search nvidia open gl in forums:mrgreen:

i changed bios settings but when i try to boot into recovery moot the kernel fails at loading!
](*,)

---

### Post by teaker1s on 2007-01-09
:-k okay you may have to enable onboard, boot recovery 
sudo dpkg-reconfigure xserver-xorg
change to "nv" driver

shutdown and enter bios and disable onboard vga and let it boot

---

### Post by pantsroptional on 2007-01-16
sorry it's been a while..bump!

this doesnt work either.. when I make all those changes to the xserver configuration and restart, ubuntu loading freezes during the "loading hardware drivers" phase.. i think its configured properly because after that restart with the bios change I can see things off my 5200, but i don;t think th nvidia driver is installed.. PLEASE HELP! thanks!!

---

### Post by teaker1s on 2007-01-16
my apologies, all the cards I use are quite old generally in xserver-xorg
"nv" is basic non open gl driver
if you want open gl you will need to boot into ubuntu and terminal

[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR] uncomment any commented out repositories by removing [COLOR="Red"]#
[/COLOR]
[COLOR="Red"]gksudo synaptic[/COLOR]

search title and description nvidia

you will have a choice of either 
[COLOR="Red"]nvidia-glx[/COLOR] or [COLOR="Red"]nvidia-glx-legacy [/COLOR]

**depending on your card quote:**

NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

you will also see that when we searched [COLOR="Red"]linux-restricted-modules[/COLOR] we need to also install the correct kernel version for the driver to work

if your not sure of your kernel then
[COLOR="Red"]uname -r[/COLOR]

from terminal 
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
choosing
[COLOR="Red"]Nvidia [/COLOR] =open GL

then you need to reboot and disable onboard in bios again

---

### Post by pantsroptional on 2007-01-18
i installed the nvidia-glx driver which with a little research seemed like the correct driver for the geforce fx 5200. i'm pretty sure the download and installation of that driver went fine. i've gotten pretty good at configuring the xserver-xorg to work with my onboard video but with the nvidia card, it still is freezing after the grub menu after the kernel loads but the other processes are still loading (with the ubuntu logo and the status bar) it freezes at the process "Loading hardware drivers'. This step normally takes a couple seconds at the most, but I've let it churn for at least 20 minutes without any budge. ALSO, for some reason, everything is purple haha. Seriously.

I think I must be messing up the configuration of xserver-xorg. I was confused by what you wrote here:

> **teaker1s said:**
> 
choosing
[COLOR="Red"]Nvidia [/COLOR] =open GL

I'm not sure what that means. On the list of drivers (i.e. my onboard video runs with the i810 driver) i've tried both 'nv' and 'nvidia', The nvidia driver is the one which causes my screen to tint everything purple. Both freeze at the same point. There was another point in the configuration that confused me. After choosing which driver to use, I left most of the fields their default, but there was a point that asked me how much memory the card had. It said to leave it blank for onboard, but I was configuring my 5200 now. The fx 5200 comes with 128MB of memory, but the configuration utility wanted the amount in kB. I tried 128000, 136000 (closer to a true amount) and neither seemed to affect anything, Shouldn't the driver autodetect this?

---

### Post by teaker1s on 2007-01-18
mb x 1024 =kb so 128mb  =131072kb

open GL is used for fast drawing of game textures etc.
now you should boot ubuntu and select the nvidia driver which will activate the driver we installed rather than the crappy non GL "nv" driver

shutdown
enter bios disable onboard and reboot.
If this doesn't work Automatix can install nvidia drivers for you search the forums for it;)

---

### Post by pantsroptional on 2007-01-22
yea I meant 131072, i calculated it earlier just hadn't remembered the exact number

i'm still experiencing the same problem.. screen is purpleish and freezes during the "Loading hardware drivers" step during the kernel loading. I guess I'll see if I can find automatix. Thanks for your help.

---

### Post by po0f on 2007-01-22
pantsroptional,

Does [this guide](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) help you?

---

### Post by pantsroptional on 2007-01-22
Yes that guide helped! I'm now past the point where it typically froze and can fully boot ubuntu with the nvidia card! It must have been blacklisting apgpart and intel_agp in /etc/modprobe.d/blacklist

However... there is a massive purple overlay that I need to get rid of. I'll google this problem of course but if anyone has a solution or good link I'd really appreciate it. Thank you very much po0f and teaker1s

---

