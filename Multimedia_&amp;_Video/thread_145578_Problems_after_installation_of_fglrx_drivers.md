---
title: "Problems after installation of fglrx drivers"
date: 2006-03-16
forum: Multimedia &amp; Video
---

### Post by UeB on 2006-03-16
i used [this]("http://doc.gwos.org/index.php/Install_ATI_driver")
guide to install the ati dirvers but part of this was (what i didnt know)
there strage x.org reconfiger think which asked my a lot of shit i dont know.
now i have no daed keys anymore
(yes there was this screen that ask me something about the keyboard and the default anser was "nodeadkeys" but what the hell should i have answered here instead? i feard to loos any keyboard functuality when i try to change the default values)
and i want them back becaus now it wirites ´e instead placing the ´ direktly over the e  (same with ^ ´ ` and ~ )  
everything with the keyboard was fine and i dont understand why a tool which thorght is there to change the display driver wants to konw anything about the keyboard!!!!! 
changing the " german eleminate deadkeys" to "german daed grave acute" didnt help anything.

ok the other thing is that my screen resolution is now 1280x764 although my laptops flat sceens once is 1280x800 and i cant change it the right one in gnome
(only to the smaller one 1024x768) and now i have to look at this ugly interpolated grafics.

Is the reason for this the "widesceen" bug mentions in the guide 
[here]("http://doc.gwos.org/index.php/Install_ATI_fglrx_driver_for_widescreen").
?
because in my xconifg.conf file there is only the right resolution (1280x764) in section monitor and screen.

thanks for any help

---

### Post by UeB on 2006-03-16
ok the keyboard is fine now just deleting the line with "nodeadkeys" in xorg.conf was enough
only the problem with the resolution left!

---

