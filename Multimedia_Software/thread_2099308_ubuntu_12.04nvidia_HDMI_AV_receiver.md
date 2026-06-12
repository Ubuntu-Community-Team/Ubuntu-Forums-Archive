---
title: "ubuntu 12.04/nvidia HDMI AV receiver"
date: 2012-12-29
forum: Multimedia Software
---

### Post by emistral on 2012-12-29
Hi all,

I posted this thread last week but it seems it ois not showing up anywhere in the forums.
The problem I have is related to my ubuntu/mythbuntu HTPC connected to my Denon AV receiver via HDMI.
Previously, I used to have another AV receiver to which my HTPC was connected via components and I could display 1080i without a problem. Because the video card in the HTPC blew, I changed it for a GT630 which has only HDMI and DVI outputs.
The AV receiver was also upgraded so that now the HTPC is to the AV receiver via HDMI then from the receiver to the video project via HDfury 3.
I can open the nvidia settings and set the resolution to 1080i 60hz and this will be displayed fine on the projector providing the fact that the AV receiver is on. The problem I have is when I switch the AV receiver off. If seems that the HTPC is losing the resolution. Next time I switch the AV receiver one, the resolution has reverted to something like 12xx X 720, not the 1080i 60hz that I set up previously.
This happens each time I switch the AV receiver off then on. Note that if I reboot the HTPC it will also lose the resolution set during the last session and revert to a default resolution (1024 x 768 I think).
This is really annoying. is there a way to tweak the xorg file - although it seems that it is not needed in 12.04 - so that I will always force to output 1080i 60hz?

for info I am running mythbuntu 12.04 + latest updates.
Thanks

---

### Post by TheFu on 2012-12-29
I see a similar issue, but not quite the same with the ATI GPU in my XBMC box. I think it is the binary drivers from ATI causing the problem that I'm seeing because is has gotten better over the last 4 months as ATI releases newer drivers.  

XBMC doesn't honor X11 resolution settings, so those do not have any impact.  If you want an easy way for force X11 resolutions, there is a tool ... let me think ...  **xrandr**

I also found this [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) , but you probably already tried those things.

---

### Post by wild_oscar on 2013-01-14
I seem to have the exact same problem. When I toggle the HDMI input I lose the image. I then need to re-run xrandr to set the correct resolution.

Have you managed to sort it out?

---

### Post by BicyclerBoy on 2013-01-14
A nice PnP method would be a udev rule..

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/660901/comments/3](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/660901/comments/3)

The nVidia X server driver prob work better with: 
nvidia-settings "srn res setting cmd"

Or could just generate an xorg.conf & force an output on & set resolution.
Can achieve the same with nvida-settings cmds line options.

---

