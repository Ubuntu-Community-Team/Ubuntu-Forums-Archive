---
title: "Nvidia Drivers -- problems!"
date: 2008-09-15
forum: Multimedia Software
---

### Post by UgatorF on 2008-09-15
I am complete noob at linux, and this is my first foray into anything beyond mac and windows so I would appreciate that any responses to this thread are noob friendly ... thanks!

Anyways, I just installed Ubuntu 8.04 on a fresh install.  I've had to do this once before because I can't seem to get my graphics card to work.  I have a PCI-Express Geforce 6600gt.  The drivers that come with Ubuntu do not work as even after installing them, my system boots up in low graphics mode.  I have also trying to install envy but that doesn't seem to work either.

The closest thing I have found (but have not tried) to help is this:
[http://ubuntuforums.org/showthread.php?t=780777](http://ubuntuforums.org/showthread.php?t=780777)

I haven't tried this yet so I don't know if it will work but I was wondering if there were any other solutions out there for me to look at ...

Thanks in advance for all your help!

---

### Post by UgatorF on 2008-09-15
am complete noob at linux, and this is my first foray into anything beyond mac and windows so I would appreciate that any responses to this thread are noob friendly ... thanks!

Anyways, I just installed Ubuntu 8.04 on a fresh install. I've had to do this once before because I can't seem to get my graphics card to work. I have a PCI-Express Geforce 6600gt. The drivers that come with Ubuntu do not work as even after installing them, my system boots up in low graphics mode. I have also trying to install envy but that doesn't seem to work either.

The closest thing I have found (but have not tried) to help is this:
[http://ubuntuforums.org/showthread.php?t=780777](http://ubuntuforums.org/showthread.php?t=780777)

I haven't tried this yet so I don't know if it will work but I was wondering if there were any other solutions out there for me to look at ...

Thanks in advance for all your help!
UgatorF is online now Report Post   	Edit/Delete Message

---

### Post by overdrank on 2008-09-15
Hi and welcome, please do not make multiple threads on the same issue.
Threads merged.
After you install the graphics drivers you will need to also install nvidia-settings. Then you can use the command ```
gksu nvidia-settings
``` and hopefully adjust your resolution there.

---

### Post by UgatorF on 2008-09-15
sorry, i thought the first one hadn't posted since i have spotty internet here at school so i went ahead and made a second one.

as far as what you told me to do ... i have done that but for some reason, when i load up the nvidia settings, it won't give me a higher resolution than 800x600.

---

### Post by overdrank on 2008-09-15
> **UgatorF said:**
> sorry, i thought the first one hadn't posted since i have spotty internet here at school so i went ahead and made a second one.

as far as what you told me to do ... i have done that but for some reason, when i load up the nvidia settings, it won't give me a higher resolution than 800x600.

Ok you may try and use this command ```
gksu displayconfig-gtk
``` and set up your monitor there. Then you should be able to set the resolution in nvidia-settings

---

### Post by UgatorF on 2008-09-15
when you say set up your monitor, what do you mean?

i have a westinghouse lcd hd tv as my monitor.  i am using a vga input but will any of that make a difference?

---

