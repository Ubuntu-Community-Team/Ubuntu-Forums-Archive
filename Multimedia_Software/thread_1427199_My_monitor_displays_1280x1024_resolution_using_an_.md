---
title: "My monitor displays 1280x1024 resolution using an ubuntu live cd but not in ubuntu"
date: 2010-03-11
forum: Multimedia Software
---

### Post by bilalsana on 2010-03-11
My monitor (philips 107E) displays a resolution of 1280x1024 in windows as well as when using an ubuntu live cd...but in my installed ubuntu this resolution is not shown, and if i apply it using xrandr...the monitor says ''frequency out of range'' i have tried 85hz, 60hz and 65hz!

---

### Post by themusicalduck on 2010-03-11
What graphics card do you have?

---

### Post by Bullwinkle_Moose on 2010-03-11
While this is intended for HTPC users it might solve your problem as well:

[http://forum.xbmc.org/showthread.php?t=54685](http://forum.xbmc.org/showthread.php?t=54685)

---

### Post by zeeshan_2011 on 2010-03-12
your graphic cart version.

---

### Post by VertexPusher on 2010-03-12
> **bilalsana said:**
> My monitor (philips 107E) displays a resolution of 1280x1024 in windows as well as when using an ubuntu live cd...but in my installed ubuntu this resolution is not shown, and if i apply it using xrandr...the monitor says ''frequency out of range'' i have tried 85hz, 60hz and 65hz!
If Xorg cannot automatically recognize your monitor's capabilities, you have to specify its horizontal and vertical refresh limits manually in the file /etc/X11/xorg.conf. Otherwise Xorg will use safe defaults which result in low resolutions. The xorg.conf file does not exist by default. Here is how you can create it:

Enter "sudo initctl stop gdm" to shut down the running instance of Xorg. You will drop to a text terminal screen.

Log in.

Run "sudo Xorg -configure". This will create a file "xorg.conf.new" in your home directory, containing default settings according to what Xorg was able to detect automatically.

Enter "sudo mv xorg.conf.new /etc/X11/xorg.conf". This will move the file to its designated location.

Enter "sudo nano /etc/X11/xorg.conf". This will open the file in a text editor.

Look for the section "Monitor" and add the following entries:
```
HorizSync 30-70
VertRefresh 50-160
```**These values are specific to the monitor model.** I've looked them up in Philips' user manual for the 107E which can be found online. **Do not use random values copied from other forum posts which refer to different monitor types! Remember to reset the limits before you attach a different monitor!**

Press Ctrl-O and Return to save the file, then press Ctrl-X to close the editor.

Enter "sudo shutdown -r now" to reboot.

---

### Post by bilalsana on 2010-03-14
i am using intel 865g....

---

### Post by bilalsana on 2010-03-15
Xrandr now gave the error 'mode not available' however adding the mode and then applying 1280x1024 resolution did the trick :)

Thk u every1 esp Vertex!

---

### Post by go4thaudio on 2010-03-19
Thank you "Vertex Pusher" for your helpful advice.  My screen now has more resolution settings than I know what to do with!  I am using an old HP ML350 G3 server with an onboard video chip Rage XL by ATI.  My resolution was stuck at 800x600 and I tried to modify xrandr and xorg.conf until I was blue in the face. At one point Ubuntu made revert my settings after restarting.  
     I did it a little differently: First of all "sudo initctl stop gdm" returned an error.
So I skipped that step.  Then "sudo Xorg-configure" returned an error.  Therefore "sudo mv ,etc"  would be pointless, why move something I did not create.  I do not use the Nano editor very proficiently, although I should learn since gedit is less terminal friendly, so here is what i did.  
    " $ gksudo gedit /etc/x11/xorg.conf"  I went to the monitor section and after the last line but before EndSection I put the cursor and hit enter.  So that means I saw a space before EndSection where my cursor was blinking.  I hit tab and typed HorizSnc 30-90 then I hit "enter" tab VertRefresh 50-150.  I saved the file and closed out and restarted my computer.  ABRACADABRA I was no longer stuck in 800x600 resolution.  CAUTION: YOU MUST KNOW YOUR MONITOR REFRESH RATES OR YOU COULD FRY YOUR MONITOR OR YOUR MOTHERBOARD/GRPHICS ADAPTER.  tHIS IS NOT A JOKE!!!Do your research.  The numbers I put in were for a Hitachi SuperScan Elite 20 monitor.  Your refresh rates will be different.  This worked for me in Ubuntu 9.04 with a HP ml350 G3 server with built in Rage XL graphics by ATI.  I have two Xeon processors by the way.  I hope I have helped someone.

---

### Post by go4thaudio on 2010-03-19
Here are some of my new display options: 1440x1050 (4:3), 1400x1050 (4:3), 1280x1024 (5:4), 1440x900 (16:10), 1280x960 (4:3), 1360x768 (16:9) etc, etc.  Some of these values looked somewhat distorted until I played with theconfiguration  option buttons on my monitor.  some people have a configuration menu on their monitor but i have like 12 buttons.  So if it comes up a little warped just adjust your monitor.

---

