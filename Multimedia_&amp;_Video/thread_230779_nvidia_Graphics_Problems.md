---
title: "nvidia Graphics Problems"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by achafe on 2006-08-06
I have a new computer, on which I run Ubuntu Drapper.  The computer has an Integrated NVIDIA GeForce 6150 LE.  

When I first started running Ubuntu, I was stuck in 1024x768.   So I followed the guide here: [http://ubuntuguide.org/wiki/Ubuntu#Hardware]("http://ubuntuguide.org/wiki/Ubuntu#Hardware")
in order to try and get the full potential of my graphics and some higher resolutions.

Now when I boot the computer I get an error saying:
NVIDIA: No matching Device section instance (BusID PCI 0:5:0) found

So far my google and forum searching have not turned up a solution, though I belive it may be a problem with the xorg.conf file. :confused:   

Any help you guys could give would be excellent!

Thanks!

---

### Post by tseliot on 2006-08-06
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then type:

```
nano -w /etc/X11/xorg.conf
```

get to the Section Device and comment out (i.e. put a "#" before) "Busid" like in the following example:
```
#BusID		"PCI:1:0:0"
```

Press CTRL+X to exit (save the file)

then reboot:
```
sudo reboot
```


EDIT: next time please, use my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by achafe on 2006-08-06
Thanks!  Worked like a charm, except I'm still stuck in 1024x768.  I will search the forums on this remaining issue!

Thanks again!

---

