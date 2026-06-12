---
title: "Problem with nvidia drivers"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by [knap] on 2005-12-19
Hi, i installed the nvidia drivers by synaptic packet manager (nvidia-glx and nvidia-settings packages) and now x don't work the error is something like kernel nvidia drivers are newer than x nvidia drivers.
How can i remove nvidia drivers or solve this?

Thanks

---

### Post by daschl on 2005-12-19
[QUOTE='[knap]']Hi, i installed the nvidia drivers by synaptic packet manager (nvidia-glx and nvidia-settings packages) and now x don't work the error is something like kernel nvidia drivers are newer than x nvidia drivers.
How can i remove nvidia drivers or solve this?

Thanks[/QUOTE]


at first, in the HOWTO sections there is a big big thread about that. post your logfiles and the exact problem there and youll get more help (i think).

and please post your logfiles there too.
(startx 2> logfile) and then upload it or post it maybe :)

kind regards,

---

### Post by frodon on 2005-12-19
Use the recovery mode  if needed and when you are in console mode type : ```
sudo nano /etc/X11/xorg.conf
```and replace "nvidia" by "nv" for the "Driver" parameter.

I give you the link to 2 useful threads which contain a lot of information about xorg configuration and nvidia drivers : 
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

