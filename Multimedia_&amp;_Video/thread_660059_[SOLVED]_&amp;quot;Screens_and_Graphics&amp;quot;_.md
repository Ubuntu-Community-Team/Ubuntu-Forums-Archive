---
title: "[SOLVED] &amp;quot;Screens and Graphics&amp;quot; woes"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by adrift on 2008-01-06
Ahhh, I'm losing my mind here. I hope I'm posting this in the right location as well. 
Here's my story. 
I had a perfectly well running copy of 7.10. Was able to mess around with Compiz, play games in Wine, you know the usual. Then I just had to go and mess up my personal Ubuntu nirvana by going into the Screens and Graphics settings under System/Administration because I wanted to extend my display through an S-video cable to my TV. I was finally successfully able to get the video extended, but when I wanted to go back to my initial settings I found that I just couldn't get back to normal.  Graphics are running on a 7600GT with no on board video. At this point, I can't get the nvidia drivers working correctly under Screens and Graphics and so am using the default generic Vesa drivers. Oddly enough, even though the second display is set to disabled in Screens and Graphics... its not. it still remains enabled in the real. When I try to run Nvidia-Settings I get an error message informing me that I "do not appear to be using the NVIDIA X driver." Under "Restricted Drivers" Nvidia Accelerated Graphic Drivers is checked. 

any advice out there?

Thank you much

---

### Post by overdrank on 2008-01-06
> **adrift said:**
> Ahhh, I'm losing my mind here. I hope I'm posting this in the right location as well. 
Here's my story. 
I had a perfectly well running copy of 7.10. Was able to mess around with Compiz, play games in Wine, you know the usual. Then I just had to go and mess up my personal Ubuntu nirvana by going into the Screens and Graphics settings under System/Administration because I wanted to extend my display through an S-video cable to my TV. I was finally successfully able to get the video extended, but when I wanted to go back to my initial settings I found that I just couldn't get back to normal.  Graphics are running on a 7600GT with no on board video. At this point, I can't get the nvidia drivers working correctly under Screens and Graphics and so am using the default generic Vesa drivers. Oddly enough, even though the second display is set to disabled in Screens and Graphics... its not. it still remains enabled in the real. When I try to run Nvidia-Settings I get an error message informing me that I "do not appear to be using the NVIDIA X driver." Under "Restricted Drivers" Nvidia Accelerated Graphic Drivers is checked. 

any advice out there?

Thank you much
HI and I had a similar issues with one sytem. Remove the restricted driver then reinstall it and you may have to reconfigure your xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use nvidia settings to enable your tv. ```
gksudo nvidia-settings
``` Good luck!

---

### Post by adrift on 2008-01-06
> **overdrank said:**
> HI and I had a similar issues with one sytem. Remove the restricted driver then reinstall it and you may have to reconfigure your xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use nvidia settings to enable your tv. ```
gksudo nvidia-settings
``` Good luck!

Excellent! you're a genius overdrank! Had to tweak one thing outside of your directions. Had to go back into "Screens and Graphics" and change my driver from (i'm guessing) the default nvidia driver to the (I'm assuming) restricted one.
Works perfectly now.
Thanks again!

---

### Post by overdrank on 2008-01-06
> **adrift said:**
> Excellent! you're a genius overdrank! Had to tweak one thing outside of your directions. Had to go back into "Screens and Graphics" and change my driver from (i'm guessing) the default nvidia driver to the (I'm assuming) restricted one.
Works perfectly now.
Thanks again!

HI and no genius here just hanging around the forums for awhile. Please mark the thread as solved so that other may benefit. Good luck! :KS

---

