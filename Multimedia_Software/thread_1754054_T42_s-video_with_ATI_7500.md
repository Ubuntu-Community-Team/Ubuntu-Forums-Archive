---
title: "T42 s-video with ATI 7500"
date: 2011-05-09
forum: Multimedia Software
---

### Post by TimGS on 2011-05-09
Hi,

I have a Thinkpad T42 and am trying to get S-video working.

I have read [https://wiki.ubuntu.com/X/Config/SVideo](https://wiki.ubuntu.com/X/Config/SVideo) and similar which suggest some xrandr commands to use to turn load detection back on and set the display to PAL.

A signal is definitely reaching the TV, but so far however I only have some faint horizontal bands moving slowly up the TV screen.

Output from xrandr is:

```
tim@dylan:~$ xrandr --props
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
	load_detection: 1 (0x00000001)	range:  (0,1)
DVI-0 disconnected (normal left inverted right x axis y axis)
	scaler: off
	tmds_pll: bios
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
	scaler: full
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video connected (normal left inverted right x axis y axis)
	tv_standard: pal
	tv_vertical_position: 0 (0x00000000)	range:  (-5,5)
	tv_horizontal_position: 0 (0x00000000)	range:  (-5,5)
	tv_horizontal_size: 0 (0x00000000)	range:  (-5,5)
	load_detection: 1 (0x00000001)	range:  (0,1)
   800x600        59.9 +   60.3  

```

Can anyone help?!

thanks,
Tim.
[I]
Edit: Changing the display resolution via System->Preferences->Monitors so that both Laptop and TV screen are set to 800x600 and ticking 'Same image in all monitors' makes little difference. However I have since noticed (this may be coincidental) that the TV screen is showing a distorted dark black and white version of the laptop screen e.g. when shutting down the 'ubuntu' graphic can be made out. Normal text such as in this browser window is too distorted to show anything that can be made out on the TV screen.[/I]

---

### Post by adhamj90 on 2011-05-09
I have the same problem 
it used to work just fine in 10.10

i think it's a reported bug
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/771458](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/771458)

i hope they find a fast solution for this.
i dont want to reinstall 10.10 again.it means backing everything up again :S

---

### Post by TimGS on 2011-05-09
> **adhamj90 said:**
> I have the same problem 
it used to work just fine in 10.10


I should have said - I am running 10.04, so probably a different issue.

thanks,
-- Tim.

---

