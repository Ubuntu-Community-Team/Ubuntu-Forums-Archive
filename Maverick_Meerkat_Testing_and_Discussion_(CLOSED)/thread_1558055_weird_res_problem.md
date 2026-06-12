---
title: "weird res problem"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-08-21
I have a strange video problem on one box , with a fesh @ A3 and updated install I cannot get any decent resolution only 600x480 or some such whe using either nouveau or the nvidia 256.44  either installed from Nvidia or through hardware drivers , I have added a server flags section and ignore abi no help . Using nv allows me to use the full resolution ( 1440x900) of the monitor , on a side note when using nv hardware drivers tells me I am using a propriatary driver ? Previous releases of ubuntu on this box have not had this . I know the edid on the monitor is bad but have always been able to set the res previously via system>preferences>display ( now monitors) or else by adjusting xorg.confg

---

### Post by VinDSL on 2010-08-23
> **ronacc said:**
> [W]ith a fresh @ A3 and updated install I cannot get any decent resolution only 600x480 or some such when using either nouveau or the nvidia 256.44 either installed from Nvidia or through hardware drivers[...]Here's a little anecdotal info for you.  Maybe it will help...

I did a fresh install of A3, every day for 5 days.

After setting up the proprietary jockey/nvidia-common drivers, and doing an update, I could NOT get past Plymouth.

I finally hit the right combo:[LIST]
[*]Do a fresh install.
[*]Forget the res (for now). Don't invoke jockey. Just use standard Nouveau drivers. 
[*]Perform a full-upgrade.
[*]After all updates are complete, THEN run jockey and tweak the nvidia-settings.
[/LIST]  

That's how I got 10.10 up n' running in high-res (GeForce 7600 GT)...  ;)

---

### Post by ronacc on 2010-08-23
Thanks for the reply , the combo you gave is essentially what I did . I never had a problem getting to desktop ,just setting the res . with either nouveau or the nvidia drivers I can't even get 800x600 only nv will allow full res . I have 2 other maverick installs on another box that do not have this problem .

---

### Post by cjcj on 2010-08-23
I have exactly the same problem with my nvidia gforce 8600 card. It started when the warning appeared in the sticky posts a litle over a week ago. I assume therefore it is part of what we have been warned about while the wise ones sort out the new verion of Xorg and its relationship with the graphics drivers that have to be compiled against it. I am making do with the nv driver for now. I suggest patience until it is sorted out. (Or a return to version 10.4 - the one we are allowed to expect to be working at the moment.)

---

### Post by dabl on 2010-08-24
I'm having what looks like the same issue, with Kubuntu 10.10 on a VMware Player VM.  I installed VMware Tools first thing after I installed from the daily build ISO (a week ago), and have been fiddling with it ever since, trying to change the default screen resolution.

- KDE System Settings lets me change to any of a number of choices, including a nice 1400x1100 that fits well on my 1600x1200 desktop. The panel has to be manually resized as well.

- VMware lets me select screen sizes, and also switches cleanly between full screen and the windowed mode

and none of it survives a reboot.


- today I made a /etc/X11/xorg.conf file, inserting a modeline for the 1400x1100 mode -- no help there

Upon reboot, it's always the same 800x600.  Very sharp and usable (in a small way), but geeeeeeeeeeez ......

---

