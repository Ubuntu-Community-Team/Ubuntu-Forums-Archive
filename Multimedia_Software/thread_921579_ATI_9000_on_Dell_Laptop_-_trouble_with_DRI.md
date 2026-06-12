---
title: "ATI 9000 on Dell Laptop - trouble with DRI"
date: 2008-09-16
forum: Multimedia Software
---

### Post by Fredvs79 on 2008-09-16
Hi I am completely new to Ubuntu, although I have some experience in the past with linux. I have a fresh install of Hardy on my Dell 600m laptop, and am having some trouble getting direct rendering to work. Out of the box the installer got my screen and video to work at the default 1400x1050 resolution, but I was unable to get screen effects to work. I realized that I didn't have the proper Radeon driver installed, so I set about trying to figure out how to install it. I followed the directions [here]("https://help.ubuntu.com/community/RadeonDriver"). I chose the open radeon driver over the closed source fglrx driver because I read under the prerequisites [here]("https://help.ubuntu.com/community/RadeonDriver") that the fglrx driver does not support cards below Radeon 9500. 

The laptop has an ATI Mobility Radeon 9000 in it. When I do
    $ lspci -nn | grep VGA
it reports
    01:00.0 VGA Compatible Controller: ATI Technologies INC Radeon RV250 [Mobility FireGL 9000] (rev2)
 
I made sure there were no fglrx drivers installed via synaptics (there weren't), and checked that the fglrx module wasn't loaded into the kernel via lsmod.

As I mentioned above, I followed directions to modify my /etc/X11/xorg.conf file. I restarted X and got to the part where I test my driver.

    $ glxinfo | grep vendor 
reports that the server and client vendor string are SGI.
    $ glxinfo | grep "direct rendering"
reports that NO direct rendering.

I checked my /var/log/Xorg.0.log file and saw the following lines:

in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1400x1050
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 2
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1400x1050

(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(**) RADEON(0): Option "XaaNoOffscreenPixmaps" "off"
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled

(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 370 x 277

(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1400x1050
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Total number of valid Screen mode(s) added: 2


When I go to "system" and then "preferences" and then "screen resolution" I get the following error message: "The X Server does not support XRandR extension. Runtime resolution changes to the display size are not available."

When I go to "preferences" and "Appearance" on the "visual effects" tab I can now select normal or extra. However, under all settings, dragging windows around is choppy.

I believe the problem lies in that I do not have DRI enabled. Please help

---

### Post by Fredvs79 on 2008-09-16
Since doing 
      $ glxinfo | grep "direct rendering"
reports that direct rendering is "NO", I believe DRI is disabled.

However, 
      $ grep -i "Direct rendering" /var/log/Xorg.0.log
shows that 
      (II) RADEON(0): Direct rendering enabled
... so it seems DRI is conflicted somewhere.

I then did
      $ export LIBGL_DEBUG=verbose
      $ glxinfo
but at the top it did not show any libGL trying to load any driver specific hardware. I would like it to show: 
     libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/radeon_dri.so.
But it does not. In fact, in my /usr/X11R6/lib folder there is no folder for modules at all. Do I not have the radeon_dri module?


The first part of the output from glxinfo is:
   name of display: :2.0
   display: :2  screen: 0
   direct rendering: No (If you want to find out why, try setting 
   LIBGL_DEBUG=verbose)


I read in the [DRI Wiki]("http://dri.freedesktop.org/wiki/DriTroubleshooting") that this could be because I replaced my "X.Org-provided libGL with some other libGL, or it's finding an old libGL from somewhere."

So I did 
    $ ldd /usr/X11R6/bin/glxinfo
and I got back
    libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ed6000)

At this point the WIKI just says "Make sure it's the one in /usr/X11R6/lib/libGL, or a link in /usr/lib to the one in /usr/X11R6/lib. You shouldn't have any libMesaGL* on your system."

I don't have any libMesaGL on my system... and I don't have any of the "errors" they suggest. The next step of the WIKI says 
 [I]If you are using a radeon and it complains about the module versions and maybe fails on an assertion, you need to update your DRM as in the instructions above.

If you've made it this far, glxinfo should be printing direct rendering: Yes and direct rendering for native GL programs should be working.[/I]

I am at a loss for how to proceed

---

### Post by Fredvs79 on 2008-09-16
I have checked synaptics to make sure I have libgl packages installed. The following are on my system already.


libgl1-mesa-glx       7.0.3~rc2-1ubuntu3
libgl1-mesa-dri       7.0.3~rc2-1ubuntu3

libglew1.5            1.5.0dfsg1-3ubuntu1
libglib2.0-0          2.16.4-0ubuntu3
libglib2.0-cil        2.12.0-2ubuntu3

---

### Post by Fredvs79 on 2008-09-16
It seems there was a conflict with the xserver-xgl.

Per this thread:
[http://ubuntuforums.org/showthread.php?p=3635640](http://ubuntuforums.org/showthread.php?p=3635640)

I removed xserver-xgl and restarted gdm

$ sudo /etc/init.d/gdm restart

Now when I check $ glxinfo
I see Direct Rendering is "Yes"
[I]name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/pc/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
[/I]
I notice that it is loading r200_dri.so instead of radeon_dri.so. Why is this? 

Dragging windows around the screen is no longer choppy. (=D>)

However, I can not enable "desktop effects" under "system" > "preferences" > "appearance" (](*,))

---

### Post by Fredvs79 on 2008-09-16
I found that Desktop Effect settings are enabled by replacing the default window manager of Gnome (Metacity) with another window manager (Compiz).

Most cards require xserver-xgl to run Compiz, but the ATI cards can actually run compiz with the open drivers. 

I tried typing *compiz* in a terminal, but I got an error that 

*GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.*

I found [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207") thread about this problem, and it is a documented bug. 

I followed Brad's suggestion and installed the compizconfig-settings-manager. I picked a corner in the 'scale' window, and was able to get compiz to run when I type it in a terminal. However, it seems that once I close the terminal, compiz quits.

---

### Post by Fredvs79 on 2008-09-16
UPDATE

I just found [this thread]("http://www.linuxquestions.org/questions/linux-software-2/how-to-start-compiz-fusion-576434/")

which states: press ALT+f2, to get a run command window.
type in "compiz --replace"

This will replace the default window manager with compiz. I just hope this is now enabled as default for whenever I log-in / start X in the future.

On another note, I haven't yet figured out how to increase the number of desktops I have in Compiz. It seems that there is no option available, though I thought I saw in metacity there was.

---

