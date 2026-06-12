---
title: "Aspect ratio problems"
date: 2009-10-09
forum: Mythbuntu
---

### Post by igoddard on 2009-10-09
I've set up my Mythbuntu box (Biostar 945GC-330 M/B - Atom 330 & Intel 945 graphics, Hauppauge Nova-T) using a normal PC monitor which gives this result for xrandr:

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 4096 x 4096
VGA1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 408mm x 306mm
   1600x1200      60.0*+
   1280x1024      75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1

Mythtv makes some interesting but fairly reasonable guesses as to how to display video.

For production I need to connect it to a TV which has a native 1398 x 786 resolution.  On this the Mythtv front end GUI is fine but video is extremely compressed vertically.  I initially tried Jaunty but switched to Karmic hoping it might be a problem fixed in the later Intel drivers but with no success - if anything the display is worse.

However, I noticed the following response to xrandr:

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 32mm x 86mm
   1600x1024      60.2  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.7*    59.8  
   1152x864       70.0     60.0  
   1280x768       59.9  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1

As can be seen X sets itself to the nearest fit to the native resolution and the screen setup wizard confirms that this is how GUI is running.  I now suspect the screen distortion is a consequence of the nonsense screen dimensions which xrandr sees and which are presumably what EDID is reporting back.  Is there a way of patching the correct dimensions into Mythtv to correct this?  Or does anyone have an alternative idea as to what might be causing the problem?



Ian

---

### Post by igoddard on 2009-10-11
After a bit more reading the only solution I can see at present is to put a DisplaySize entry into the xorg.conf.

I've run Xorg -configure to get a bare-bones xorg.conf and patched into that a Monitor section obtained from read-edid using the normal PC monitor I use for setting things up on the bench and modified the Screen section to use that.  So far, so good.  I've also got a Monitor section from EDID using the TV.  I can edit that into the xorg.conf with a sensible DisplaySize entry.  The next job is to test this and make sure it does override the EDID info as advertised.

However - the ideal way of setting things up would be for Xorg to match the ID from the monitor with the appropriate model and/or manufacturer name in the Monitor section and select the appropriate one automatically.  At a pinch I could approximate this by having two xorg.confs having the start-up script run read-edid, grep for the model name in the output and use this to copy the correct file as the working xorg.conf.  Can I avoid this kludge?

---

