---
title: "X Freezes after login; fglrx related?"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by Dakana on 2007-03-05
Well, I decided to take the plunge yesterday: I'm a lifelong Windows user, and finally resolved to learn Linux. I figure it's a skill I should have; on my home network I'm running a fileserver with Linux installed, and have very minimal experience with it.

Anyway, I installed Ubuntu 6.10 without any issues. I rebooted after the initial install and immediately went to the update manager. I believe Synaptic had around 135 updates for me - I know there was a kernel update as well as some X related updates. With everything selected, I ran the updates and restarted. This is where my problems began.

After the reboot, I got a blank screen where the GUI login screen should have been. I hard restarted the computer and entered recovery mode. I used Vi and edited my xorg.conf file, changing the driver from 'ati' to 'vesa'. I rebooted from the console, and X started up just fine this time. 

Wanting full 3d support, I installed the fglrx package from Synaptic. After reading that 'sudo aticonfig --initial' could overwrite my monitor settings, I decided to forgo that and instead simply change 'vesa' in xorg.conf to 'fglrx.' The guide I was using said that was an appropriate substitution. After that, I did 'sudo aticonfig --overlay-type=Xv' and rebooted. The login screen loaded, and I was able to enter the desktop environment.

However, after being in the environment for around 2 minutes, the system became unresponsive. My mouse pointer was moving appropriately, but nothing else would respond to clicks, keyboard input, etc. I tried CTRL+ALT+Backspace, and it didn't work, so I tried CTRL+ALT+F1 - that didn't work either. I hard restarted and re-logged in. This time, when Panels was supposed to load, I got an orange single-color desktop background and blank, white Panels at the top and bottom, and the unresponsiveness set in again. I hard restarted and re-logged in, and the situation repeated itself.

It was then 2am and I had to be up at 6am the next morning, so I gave up and went to bed. I'm now at school posting this, hoping someone has some knowledge about this issue! When I get home I guess I'll reenable the vesa drivers and see what happens.

I'm using a Radeon 8500DV and fglrx driver version 8.28.8.


Does anyone know what's going on?

---

### Post by Dakana on 2007-03-05
An update - I got home and searched around some more about this issue.

I came across this wiki entry ([http://wiki.cchtml.com/index.php/Frequently_Asked_Questions](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions)) and it mentioned UMA/SIDEPORT options in BIOS. It said that X can become unresponsive if it isn't configured correctly in some ATI card, so I decided to try it.

I changed 'vesa' to 'fglrx' and rebooted into BIOS. I reduced my AGP aperture size to 64mb from 128mb. This time, Panels loaded fine, and I was able to enter the desktop environment. However, after a minute or two, X became completely unresponsive once again.

I rebooted into BIOS and reduced it further, from 64mb to 32mb. This time, Panels didn't even load before it froze. To double-check, I increased the size to 64mb once again, and the previous problem (freezing after 1-2 minutes) occurred again.

I then rebooted into recovery console and changed fglrx back to vesa, and here I am typing this update, hoping someone knows what's going on here :(.

---

### Post by StarscreamD on 2007-03-05
Timed freeze-outs sounds like either a memory problem or the graphics problem. Memory doesn't seem to be your issue, but I don't have experiece with ATi cards as my own is NViDiA. I had a similar issue, and it had to due with the option "RenderAccel" in my xorg.conf file.

What would happen is that I would open Firefox or Add/Remove Programs or something, and everything besides the movement of the mouse froze. I had to manually change this setting from - "Render Accel" "true" to "RenderAccel" "0" before I could normally use Ubuntu.

I don't think this will help, but it's worth a shot. :) Hopefully this bump will find somebody more knowledgeable in this subject. Good luck!

---

### Post by Dakana on 2007-03-06
I'm pretty sure I've isolated it to a kernel issue, as when I install a clean 6.10, 3d acceleration works fine using the 'ati' driver, without freezing. When I upgraded to the 6.11 kernel, it broke...

It may also have something to do with the X version, as xorg core and other stuff relating to it was included in the update. I can't find any previous reports of ati drivers freezing or blanking on the newest kernel upgrade... I don't really know what to do anymore.

---

