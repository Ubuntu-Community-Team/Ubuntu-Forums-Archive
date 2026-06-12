---
title: "fglrx won't wake up without switching consoles"
date: 2008-07-16
forum: Multimedia Software
---

### Post by padukes on 2008-07-16
Hi All,

I recently switched from the radeon xorg driver to fglrx.  Everything seems to be working, however, after the machine is left off for a few hours the monitor (a TV) goes blank and won't come back on without switching the virtual console.  Hitting a button on the keyboard or moving the mouse doesn't do anything but switching to vt1 and then back to vt7 seems to do the trick.  Really all I want to do is disable this sleeping so that the monitor (TV) never goes blank without me explicitly turning it off.

Any ideas?
Thanks!
P

---

### Post by markbuntu on 2008-07-16
Just set your screensaver and power management settings to never.

btw, which ati driver are you using?

---

### Post by padukes on 2008-07-16
Hi,

Thanks for the quick reply.  I already unchecked the screen saver in the screen saver settings but I don't see anything for power management (this is mythbuntu).  Is this the right way to get the driver version info:

padukes@mymachine:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7412 Release

edit: Also, everything worked fine when I used the radeon driver

Thanks!
P

---

### Post by markbuntu on 2008-07-16
Yes, it is, sort of. It tells us that you are using the ATI driver but not which version.

If everything worked fine, why did you change?

btw, what ati video do you have?
Some work better with the Radeon driver.

---

### Post by padukes on 2008-07-16
I switched because I couldn't get direct rendering to work and I wanted to watch HD video. The new driver lets me do that (and works pretty well on my old machine).  Here's my video card:

02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
02:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


Thanks again for the quick response. Any ideas on the screen blanking stuff?

Thanks!
P

---

### Post by markbuntu on 2008-07-17
Ok, where did you get this driver?
Are you running compiz/desktop effects?

---

### Post by padukes on 2008-07-17
I got the driver by clicking the restricted drivers window and selecting the ati driver (then I messed with the xorg.conf manually).  I'm not running compiz/desktop effects because this is a mythbuntu box and I just want to use it to watch/record tv.  Should there be power management settings somewhere? Can I do them from the command line?

Thanks again,
P

---

### Post by markbuntu on 2008-07-17
Ok, just to be sure, in the OP you stated that the sceen went dark after leaving the machine off for a few hours and then it would not wake up. I am assuming you meant on.

This is a suspend/resume problem with ACPI and it not recognizing the timer it needs to wake up or to load system info to swap. There is also an unrelated problem with the 8.4 ati driver that is fixed in the 8.6 driver. If you want to get this driver you can follow the directions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use Method 2.

Also, there are some tweaks you can use to increase the performance with mythbuntu. Those are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Be sure and read it all the way through and take note of the parts about mythbuntu before making any changes.

If this does not work then you probably have the first problem. I am not familiar with mythbuntu but there should be some way to keep the system from going to sleep which will fix this problem in any case. Try that first.

---

### Post by padukes on 2008-07-18
Thanks again Mark!

I'm a little scared to try your suggestion because installing new video drivers seems to be non-trivial, so I'm hoping to avoid it.  I did a little more testing and this is what I found:

I disabled ACPI by putting "acpi=off lspci=noacpi" in the kernel startup options and that didn't seem to have any effect which made me think it was not an ACPI problem.

Then I tried turning off the TV and then immediately turning it back on and I was able to reproduce the problem!  Is it possible that the video card freaks out when the TV signal goes away and then doesn't know when to come back on?  Is there any way to fix this? Maybe something with EDID?

Thanks so much!
P

---

### Post by padukes on 2008-07-19
Hi All,

I installed the new driver according to method 2 above and I still get the same problem: The signal disappears when the TV goes off and doesn't come back unless I switch virtual consoles or restart gdm.

Any ideas?

Thanks!
P

---

### Post by markbuntu on 2008-07-19
Well yes, the driver could be freaking out when one of the displays it is driving suddenly dissapears. You can use Catalyst Control Center to tell the driver to stop using the tv before you turn it off. In fact, this is probably the way you should do it.

---

### Post by padukes on 2008-07-31
Hi Mark,

I ran amdcccle but didn't see any options for this. Are there any programatic ways to handle this? I'd rather not have to run a program and click a few buttons every time I want to turn off my tv.

Thanks!
P

---

### Post by markbuntu on 2008-07-31
I don't know, I don't even own a tv but I do use dual  monitor and there is the little box in the Catalyst Control Center/Display Manager/Display Modes labelled "Enable Display" which you can use to turn on and off whatever display is selected in red.

---

