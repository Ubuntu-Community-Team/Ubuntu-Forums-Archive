---
title: "Second monitor not working"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by taojian on 2011-04-02
Upgrading to Natty seems to have made it impossible to use my second monitor. I have an odd setup, with a Radeon video card, and the newest open-source fglrx drivers. I have the Unity daily PPA enabled to make all this work. fglrx version: 2:8.840-0ubuntu1.

When I plug in the second monitor and open the monitors system setting pane, the second monitor is "off" by default. When I click "on" and then "apply", there's a bunch of flashing, then I get an error notification:

```
Required virtual size does not fit available size: requested=(2880,900),minimum=(320,220),maximum=(1440,1440)
```

Both monitors are 1440x900.

That's really all that happens -- the second monitor stays blank.

Any hints?

lspci output:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0342
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at dc00 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon 
```

---

### Post by osarusan on 2011-04-02
I have this same issue when I try to use the xrandr applet. (I am also using an ATI card with the fglrx drivers).

I got my dual monitor setup working by using amdccle -- the Catalyst control center. That was the only way I could get things to work, both before Natty and after upgrading to Natty. fglrx is really fudgy like that...

Incidentally, if you use the built-in open source ati drivers, you can use the xrandr just fine, and the display is generally much faster and more responsive. 3d is a bit slower, unfortunately.

---

### Post by taojian on 2011-04-02
Hey no kidding! That worked, thanks very much. I've never used the Catalyst control center before -- in my wrestling with fglrx I've only ever used aticonfig --intial=dual-head, which I guess is still a xorg.conf thing.

So now I've got one enormous desktop, and the monitors control panel doesn't even know there are two monitors plugged in. I'm not able to drag windows across the border, however, so the second monitor isn't much use. When I try, the window disappears off the edge until the mouse pointer itself hits the edge. The window doesn't appear on the other monitor. When the mouse hits the edge it acts like it does when you press a window against the top menu bar and you get a blue shade indicating that it's going to be maximized. In this case, though, the blue shade only appears on half of the monitor, and if you release the window it's maximized vertically, but only takes up half the screen, horizontally. Looks like the screen/monitor dimensions are getting confused somewhere along the line…

Thanks again

---

### Post by osarusan on 2011-04-02
Yeah, you'll have to play around with the various settings in Catalyst to get a setup you like, but you can get a very nice, beautiful setup where you can drag windows across the monitors. Just keep trying the various options. The sad thing is you have to restart each time, but you can get it to work.

---

### Post by taojian on 2011-04-02
Awesome! Thanks for the tips. For anyone else: I ended up going into the "Display Manager" tab of the Catalyst control center, and for both monitors switching the "Multi-Display" choice to "Multi-display desktop with display(s) 1/2". Xinerama is off. It's still not working correctly, though -- anything to do with switching workspaces causes the displays to choke and flicker and redisplay. Gah.

Out of curiosity, are you also having the issues cited in [this thread]("http://ubuntuforums.org/showthread.php?t=1718206")? I am -- gnome-panel will not die, though I've hidden it, and I have to put Unity in a startup application.

---

### Post by osarusan on 2011-04-03
Ah, are you using Unity?
I was having awful glitches with fglrx and Unity, so right now I switched back to the open source drivers.

If you load into the "Ubuntu Classic (no effects)" desktop, you will probably have better results with the graphics for now. Apparently the fglrx driver in the repos isn't working right just yet.

When I was using the no-effects session, everything worked beautifully and I had no graphical errors. It's only when Compiz/Unity are loaded that I had trouble.

You can also use the Unity2d session with no troubles.

I'm hoping that the fglrx drivers will be updated soon... I'd like to be able to use Unity with compiz again.

---

### Post by taojian on 2011-04-03
I'm using the Unity daily builds (a separate PPA), and that allows the whole compiz/Unity/open sources fglrx wedding cake to work. Not perfectly, mind you, but it is 3D Unity on open source drivers&#8230;

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta)

---

