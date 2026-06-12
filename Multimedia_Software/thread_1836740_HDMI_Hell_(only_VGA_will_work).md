---
title: "HDMI Hell (only VGA will work)"
date: 2011-08-31
forum: Multimedia Software
---

### Post by Dannny213 on 2011-08-31
Hi guys, sorry if this is in the wrong thread (I hope it's not)

I am having trouble utilizing the HDMI feature on my Samsung TV (LE19R86BD) in Ubuntu 10.04

Now, this TV has always been a pain in the *** when getting the HDMI or any other port to work (had loads of trouble with the 360 in the past etc) but I would like to try everything before I give up on the idea. 

Right now, I have both the VGA cable and HDMI cable plugged into my e-machines er1402. The VGA works fine, as it always has, but the HDMI either shows up as 'Mode Not Supported' or 'No Signal'. That was, until I manually downloaded and installed the latest NVIDIA graphics driver (280.13)

Now, when I click HDMI mode on my Samsung TV, I get an image of the PC screen - only it seems out of place. There is no mouse cursor nor can I do anything on screen. But at least it's somewhat working, right?

Now, when I open NVIDIA X Server Settings, I can see that there are 2 Display screens listed under the Configuration option. Screen 0 is my working screen (through VGA)  and Screen 1 is the HDMI screen (which doesn't work) 

Playing around with the HDMI resolution settings (screen 1 settings) forces Ubuntu to freeze and will simply force a 'Mode Not Supported' under the HDMI mode on my TV. If I revert back to PC mode (VGA) the screen will come back, but will be frozen completely and i'll be forced to shutdown and restart the computer.

So it seems there is some confusion in the HDMI detection and the correct resolution output. And the crazy thing is - with NO graphics driver installed - the HDMI works perfectly. 

If anyone has any ideas or suggestions, please fire away. I'd love to get it working right. I will try the simple solution of a new HDMI cable tomorrow when it arrives.

---

### Post by gennatolls on 2011-08-31
Hi,

I had a similar problem when connecting a sammy monitor to a dell in 10.04.
 In NVidia X Server, I disabled twin view" under configuration and set it to 
Separate X Screen.   Also had to make sure the default Ubuntu Monitors app 
agreed with the NVidia X server settings ( same resolutions etc.) It was a 
laptop, so may not apply here. Worth a shot though.

---

### Post by Dannny213 on 2011-09-01
Okay, so I reinstalled Ubuntu 10.04 and the HDMI works perfectly. There's only one problem - theres no NVIDIA graphics drivers currently installed.

It seems if I install one, the HDMI becomes extremely hard to handle. Any ideas?

---

### Post by Dannny213 on 2011-09-01
Okay, installed the first NVIDIA graphics driver on the Proprietary Drivers app. (version 173.14.22)

HDMI still works okay, but the movement is choppy, especially when browsing websites and windows in Ubuntu.

I'm about to install the latest version next (there are only 2 drivers I can download) My guess is HDMI is about to die as soon as I install and reboot.


EDIT - Yep, as expected, Proprietary Driver 195.36.24 no longer allows HDMI on my monitor. 'Mode Not Supported' is the message I receive. I had to plug my VGA back in.

---

