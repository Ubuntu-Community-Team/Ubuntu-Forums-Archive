---
title: "Console Command to Test Camera?"
date: 2011-05-06
forum: Multimedia Software
---

### Post by ProNux on 2011-05-06
Hi Guys,

I remember there is a command in the console to test the camera, without having to install any chat clients.  Can someone please post it here, I forgot the command.  I can't find after searching the forums.  Thanks in advance.

---

### Post by no2498 on 2011-05-06
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by ProNux on 2011-05-06
> **no2498 said:**
> open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

Thanks bro!  Exactly the command that I was looking for.  This is one reason why I like the Ubuntu community.

My device is STILL NOT supported.  My device ID is 0545:810a.  I have searched berlios uvc still no news about my device.

---

### Post by no2498 on 2011-05-06
in a terminal type dmesg click enter
after it stops type lsusb click enter
that should give you a number and name of your cam

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

[http://www.danielogawa.com/webcam.html](http://www.danielogawa.com/webcam.html)


most web cam drivers are in the kernel now days

---

### Post by merryreed on 2011-05-07
To access the console, use the backtick key (`), while in the game (Unpaused). The backquote key changes tilde (~) on U.S. keyboards, and the symbol does not (¬) on keyboards in the UK. Other keyboards are different, but the key is usually on the left of 1 and just below the Escape key (Esc). The key is in the top left button under escape on non-US keyboards. (Example: §, ½ o | in Scandinavia (Sweden, etc., Danish, Norwegian), circumflex (^) in German keyboards, ² of the French, \ o | Keyboards in Italian, "in Brazilian Keyboards" in Turkish keyboards ). The HUD will disappear and you receive a message (|) in the lower left corner of the screen where you can type in the code (s).
Go to your installation directory Fallout New Vegas, find Fallout_default.ini (make sure it is not read-only) and open it in notepad. Then use Ctrl + F to find iConsoleTextXPos line and change 30 to a larger number, 200 for example. This will make the console appears in the right place.

---

