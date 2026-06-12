---
title: "Trying to enable DVI-Port on Docking Station with Intel Chipset"
date: 2008-11-03
forum: Multimedia Software
---

### Post by jan. on 2008-11-03
I tried to enable the DVI-Port on my Lenovo [Advanced Mini Dock]("http://www.thinkwiki.org/wiki/ThinkPad_Advanced_Mini_Dock"), so that I could use it with my Thinkpad T400 docked into the station.

After a clean install of Ubuntu 8.10, xrandr doesn't show the DVI-Port (also referred to as TMDS-1) in its listing.

```
jan@thinkbig:/etc/hal/fdi/policy$ xrandr 
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1600 x 1600
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.2*+   59.9     50.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  

```

Since modifications of the xorg.conf are no longer the way to go, I tried to create a FDI policy, so that the "intel" driver is explicitly told to consider the DVI-Port. However the policy is not working, as the DVI-Port does not appear in the xrandr listing.

```
<deviceinfo version="0.2">
	<device>
		<match key="input.x11_driver" string="intel">
			<merge key="monitor-TMDS-1" type="string">dvi</merge>
		</match>
	</device>
</deviceinfo>
```

How do I enable the DVI-Port with Intrepid Ibex installed on my machine?

---

### Post by banshee.berlin on 2008-11-04
Same problem here with a T500. Suggestions, anyone?

---

### Post by gatman3 on 2008-11-14
I have a W500, and I'm pretty sure that the Intel integrated graphics can only drive VGA, not DVI.  Might be a different situation because the W500 has a switchable graphics with a discrete ATI chip as well, and the design allows the ATI graphics to drive both VGA and DVI.  But the integrated Intel graphics can only drive VGA.

---

### Post by jan. on 2008-12-03
From what I've read on some forums, I confirm what gatman3 stated.

---

### Post by swissz on 2011-03-25
I have the same problem with T400. On the site [http://www.thinkwiki.org/wiki/ThinkPad_Advanced_Mini_Dock](http://www.thinkwiki.org/wiki/ThinkPad_Advanced_Mini_Dock) it is explicitly written: "On laptops with Switchable Graphics only discrete GPU is attached to DVI output."

---

