---
title: "Mutliple Monitors with an Nvidia Card"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by kingkilr on 2007-12-17
I've been trying to get 2 monitors set up on my new Ubuntu install(through Wubi if it matters).  I've been trying to get it running through the screen and graphics thing, but every time I log out after it tells me to I get an error about low graphics mode, and then when I log back in my settings are reset(and the available resolutions altered).  I have been told to use sudo nvidia-settings however that just gives me an error saying that nvidia x isn't running, to run sudo nvidia-xconfig and then restart x server, I have tried this(assuming cntrl-alt-backspace restarts x), however it just gives me the same error.  I have installed the restricted driver and the system should be fully up to date.

My hardware:
Nvidia 7900GS
1st monitor: Samsung Syncmaster 1680*1050
2nd monitor: Dell M782p

Thanks in advance!

---

### Post by MCMcButtah on 2007-12-17
I am pretty sure nvidia-settings is a GUI that you use once your X is up and running and you are at your desktop. If your config is too broken to allow you to startx that should be addressed first. Maybe you should post the contents of your /etc/X11/xorg.conf file here.

I had allot of problems myself with bad xorg.conf files being generated when I was using nvidia-settings to setup my dual monitors.

---

### Post by kingkilr on 2007-12-17
Well I'm in Ubuntu, using firefox so I think x is working, but I'm not 100% sure.  Here is a link to the xorg.conf : [http://dpaste.com/28308/](http://dpaste.com/28308/) there are also a few xorg.conf.1 and failsafe and backup can they be deleted safely?

---

### Post by MCMcButtah on 2007-12-27
I have never had a problem deleting them. I have always assumed they were backup copies made when nvidia-settings writes a new xorg.conf file.

---

