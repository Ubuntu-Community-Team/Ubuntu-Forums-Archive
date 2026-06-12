---
title: "Graphics Unusable with ATI Drivers on 12.10"
date: 2012-12-08
forum: Multimedia Software
---

### Post by southpointingchariot on 2012-12-08
I'm having graphics problems with a 1 day old install of 12.10 on a Sony Vaio VGN-FW139E with a ATI Mobility Radeon HD 3400.

I could not get my HDMI display to be recognized, so I tried installing the proprietary drivers through the Software Center.

When I rebooted however, the resolution had been send to 1024x768, the launcher cannot be seen or accessed, and terminals will not appear.

I can get to the system settings menu by right clicking the desktop, but cannot launch any other applications.

What can I do to resolve this?

---

### Post by yanes on 2012-12-08
By pressing : Alt + Ctrl + T ,   a terminal window will appears , 
then you type : 
[COLOR=Blue]xrandr[/COLOR]

 your screen details (including current resolution )wil appears with a  list of available resolutions
you can then type : 
 xrandr -s 0       
(for the first resolution in list , the index begins with zero )
e.g. : to choose the second resolution  in list you type :
[COLOR=Blue] xrandr -s 1 [/COLOR]

Good luck

---

### Post by southpointingchariot on 2012-12-08
> **yanes said:**
> By pressing : Alt + Ctrl + T ,   a terminal window will appears , 
then you type : 
[COLOR=Blue]xrandr[/COLOR]

 your screen details (including current resolution )wil appears with a  list of available resolutions
you can then type : 
 xrandr -s 0       
(for the first resolution in list , the index begins with zero )
e.g. : to choose the second resolution  in list you type :
[COLOR=Blue] xrandr -s 1 [/COLOR]

Good luck

I will try that out, thank you. A dollar says the terminal won't appear, but we'll see ;) .

---

