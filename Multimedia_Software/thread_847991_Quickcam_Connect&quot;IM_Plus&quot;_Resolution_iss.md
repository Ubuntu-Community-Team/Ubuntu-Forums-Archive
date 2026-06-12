---
title: "Quickcam Connect/&quot;IM Plus&quot; Resolution issue"
date: 2008-07-03
forum: Multimedia Software
---

### Post by mlitty on 2008-07-03
I recently installed skype so that distant family could talk back and forth.  I knew that hardware compatibility is an issue, so I looked for recommended web cams and found the Logitech Quickcams to be widely supported, so I bought the Quickcam IM Plus package.  One of the reasons bought it was for the 640x480 resolution.  Another was the several references to open source driver support.

After having the camera and using it for a week with my wife, her regular complaints about the blurry and pixelated images she is seeing from the camera got me digging deeper.  It seems that the camera is only supported at 320x240 and I'm only getting about 12fps, not the advertised 30fps.! 

Since I'm runnin it on a AMD Turion64 X2 with 3GB RAM, I'm pretty sure it's not an issue with the PC.  Looking into the drivers, it seems to be a driver issue.

This has me angry for several reasons.  I did the research and believed the sources that said this camera was supported.  There were no qualifications stating anything about limited resolution or frame rates.  As a long time linux user, I'm upset that I can't even trust the community hardware resources.  Why is it that "supported" always means "supported with unspecified limitations"!?

After four hours of wrestling with this tonight alone, I'm very frustrated.  I feel like I've wasted $35 and a LOT of pre-purchase research time.

Does anyone know of a way to get full 640x480 resolution support at 30fps on a Logitech Quickcam IM Plus!?

lsusb reports it to be 
> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam Connect


I'm running Ubuntu Hardy.

If not, does anyone know of a camera that is truly and fully supported under Ubuntu at 640x480 @ 30fps, and works with skype?  Skype seems to think that only the Logitech Quick cams will work at that resolution.  [See this note from Skype]("http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=1416&nav=+%26gt%3B+%3Ca+href%3D%27index.php%3F_a%3Dknowledgebase%26_j%3Dsubcat%26_i%3D41%27%3EVideo%3C%2Fa%3E").  This one also talks about [why Logitech Cams are only supported]("http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=1426&nav=+%26gt%3B+%3Ca+href%3D%27index.php%3F_a%3Dknowledgebase%26_j%3Dsubcat%26_i%3D41%27%3EVideo%3C%2Fa%3E").

Is anyone getting 640x480 on linux with skype?  What webcam are you using and what drivers?

Thank you to anyone with the patience to get through my rant to the question above.

~mlitty

---

### Post by mlitty on 2008-07-11
An update.  I've recently learned that USB does not support 640x480 @30fps.  Apparently there's [not enough bandwidth]("http://www.lavrsen.dk/twiki/bin/view/PWC/FrequentlyAskedQuestionsPWC#The_box_says_I_can_take_images_a"). 

Setpwc is great for getting it up to 640x480.  Does anyone know if there's a way to make the changes I do with setpwc permanent? or at least persistent after a reboot?

I tried ```
setpwc -b
``` but I got > setpwc v1.2, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]
Error while doing ioctl VIDIOCPWCSUSER: Invalid argument


I suspect that this is because I'm using a logitech camera that does not support the Phillips store feature.

Any other ideas?

---

