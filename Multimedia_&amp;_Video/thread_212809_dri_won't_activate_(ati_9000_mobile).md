---
title: "dri won't activate (ati 9000 mobile)"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by kr0m3 on 2006-07-10
after installing the ati drivers for my radeon 9000 series Mobile, everything SAYS dri is working, but it isn't.

for instance:
-------------
> 
kr0m3@zulu:~$ glxinfo|grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


and glxheads states:
--------------------
> 
kr0m3@zulu:~$ glxheads
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x805e008
  Window:      0x2c00002
  Context:     0x8065650
  GL_VERSION:  1.2 (1.5 Mesa 6.4.1)
  GL_VENDOR:   Mesa project: [www.mesa3d.org](www.mesa3d.org)
  GL_RENDERER: Mesa GLX Indirect


but.../var/log/Xorg.0.log says:
-------------
> 
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!


and my /etc/X11/xorg.conf says:
-------------------------------
> 
Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


the reason that I even care is because i have just installed the drivers (as per [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) ) and yes, i replaced the /usr/lib/libGL.so.1.2 and created the sym-link from /usr/lib/dri to /usr/lib/xorg/modules/dri as it states.)  i used method 1 and dont have an amd_64... but this is my first step in trying for the elusive xgl/compiz and i don't want to proceed until i get my frame-rate back up.

glxgears -printfps used to give me an average of 850 +/- and now it sits at a dismal 175 +/- ....

further, fgl_glxgears won't even run, flashing for a sec and giving this:
--------------------------------------------------------------------------
> 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33




i have perused the forums and google'd the www, but to be honest there are simply soOOooo many different he-said/she-said's going on that i just needed to come right out and ask it.

so:  is this an issue or am i just wiggin' out over here?

thanx in advance!!
~k

---

### Post by Paerez on 2006-07-10
Try searching in /usr/lib/xorg/modules/dri for anything named mesa:
```
# find /usr/lib/xorg/modules/dri -iname '*mesa*'
```
and delete it.

I also have a 9000 mobility, and this helped me a bit, since xorg will pick mesa over fglrx, you have to remove all the mesa stuff.

Hey if you ever get xgl working with fglrx let me know. The best I could do was the way crappy performance using the "radeon" driver back before xorg 7.

---

### Post by kr0m3 on 2006-07-10
the issue actually was caused by leftover Mesa libGL crap in /usr/lib that i had missed the first time around.
i cleared them out and streamlined the display/device/monitor settings in xorg.conf so that all the settings fell under the ati driver device settings and i got xgl to load.
--
IMHO, not EVEN worth the effort.  the performance of the pc takes a dive across the board.  completely unusable.  metacity crashes, dvd is unwatchable, etc etc ... basically al the horror stories from the other threads.  a complete waste of time at this stage.


im certain that Novell will eventually get xgl stable.  im sure that it will easily be the most wonderful eye-candy that the world has ever seen.  but not yet and not soon.


maybe a christmas present from suSE Claus?  :)

~k

---

### Post by Paerez on 2006-07-10
I am mostly hoping for new Xorg and new FGLRX to play nice, once that works out I will try XGL/Compiz.

---

