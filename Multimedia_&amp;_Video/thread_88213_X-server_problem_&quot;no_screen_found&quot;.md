---
title: "X-server problem &quot;no screen found&quot;"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by janbanan on 2005-11-09
Have a problem during startup. When it comes to x-server i get an fatal error "no screen found". After there is a black screen with username@computername;
and i can enter some commands.
I have a Samsung syncmaster flat-screen with DVI and an ATI x700 graphics.
I googled and found sudo dkpg-reconfigure xserver-xorg
but the i get command unknown.
Can someone guide me. I prefer basic guidence because i'm new in the game

---

### Post by Remmelas on 2005-11-09
Easiest starting point is to view the xserver logs and look for 'EE' errors, to see what broke the start up.

---

### Post by Teroedni on 2005-11-10
in console(wherebn you are now) write
sudo nano /etc/X11/xorg.conf


change driver in device from ati to Vesa


demo taken from my xorg
Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"<-----change to vesa
	BusID		"PCI:3:0:0"
        Option          "backingstore"
EndSection


Then save the xorg file press ctrl+o
Then you must exit  Press ctrl+x
Then your back at console(black screen)
Write sudo startx
Then you should be loading:)

---

### Post by janbanan on 2005-11-10
Thanks for the help, really appreciate it.
I've done the things you wrote but then I experience the next problem.
Changing it to vesa made it even worse. Now the screen freezes and it's just black

---

### Post by Teroedni on 2005-11-10
So vesa destroy it?

It may be that the instalation have gone very bad
Install anew and use only defaults 
Let ubuntu decide everything:

---

### Post by tseliot on 2005-11-10
[QUOTE=janbanan]Have a problem during startup. When it comes to x-server i get an fatal error "no screen found". After there is a black screen with username@computername;
and i can enter some commands.
I have a Samsung syncmaster flat-screen with DVI and an ATI x700 graphics.
I googled and found sudo dkpg-reconfigure xserver-xorg
but the i get command unknown.
Can someone guide me. I prefer basic guidence because i'm new in the game[/QUOTE]

The correct command is "sudo [COLOR="Red"]dpkg[/COLOR]-reconfigure xserver-xorg"

(it's "dpkg" and not "dkpg")

Try it now

---

### Post by janbanan on 2005-11-11
I've fixed the "no screen found" problem and I'm now able to run ubuntu. That opens  up for the next question. Should i now download and install the ati drivers from ati.com? To fix the first problem I followed a How-to guide and ran apt-get install xorg-driver-fglrx and chosed the fglrx driver instead of ati + made some changes in xorg.conf. So is it a good idea to download the drivers?

Ati x700 graphics

---

### Post by Teroedni on 2005-11-11
no I think you should be happy now;)
fglrx is the driver from ati. 



Run some opengl screensaver or 3dgames to check that your card work alright:D

---

### Post by janbanan on 2005-11-11
Thanks for taking time. I really appreciate it.
I wan't to test if the video-card is working properly. Ran the glxgears -printfps and got 4620FPS. Is that satisfying? Is there anything else i can check?
I kind of liked the catalyst control-center from ati when i used windows. Isn't it possible to have that control-center in ubuntu? I'm scared of screw things up if i install the 51Mb package.

My TV-out is always turned on. Also it's a clone of my desktop. I don't want a clone, like an expanded desktop better. I wan't to calibrate the screen-size so that it fit my TV. Usually I did that with catalyst. How am I supposed to do this now if i can't use the control-panel?

---

### Post by Teroedni on 2005-11-13
i would say thats very good i got 3000 ca with my geforce 4 ti 4200
Ati drivers are very bad and therefore score lower then their equilvent cards from Nvidia.

---

