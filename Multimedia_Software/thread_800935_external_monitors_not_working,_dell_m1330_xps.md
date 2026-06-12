---
title: "external monitors not working, dell m1330 xps"
date: 2008-05-20
forum: Multimedia Software
---

### Post by xkaliburx on 2008-05-20
Morning all, made the change over the weekend from fedora 8 to Ubuntu, all seemed good (wireless still not working, but that's another story).  

But at work I have a Matrox triple head to go ([http://www.matrox.com/graphics/en/cadgis/products/th2go/th2go.php]("http://www.matrox.com/graphics/en/cadgis/products/th2go/th2go.php"))  connected to 3 Dell 22' widescren monitors.

Last week I would connect the video before the latpop started, start the laptop and the display would soon change over to the monitors giving me a nice 3850x1600 resolution.  I can't get anything at all and not sure where to look.  I tried connecting before, after, even trying the Fn+F8 but all the monitors sit in offline mode.

I am not 2 Ubuntu saavy yet, do have the correct nvidia drivers loaded and working fine, System->Pref->Screen resolution shows one monitor [ Unknonwn ], not sure if that is it but nothing is displayed.

Is this something I must dig into the xorg.conf file or is there an easier way?  Thanks for all replies.

Lr

###########################
# update:
###########################

After restarting again, the center of the 3 monitors is now working (cloned with the laptop), but resolution is terrible (I guess it's using the laptop's) and the nvidia functions (enhanced desktop) don't seem to be working now.   Not sure if that helps, or not, but basically it looks like I just need to "add" this one large item as a monitor as I remember in Fedora when I looked at the screen resolution part there was the laptop and the other monitor shown where here it only shows [laptop] now, and there is no "click to add a monitor" which is why I am thinking xorg (but no idea what/how).

---

