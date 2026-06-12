---
title: "Nvidia low-graphics"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Jookia on 2008-05-10
So basically, my xorg.conf file is in low-graphics, I can't get it back to normal, I'm used dpkg to configure it since when I enabled Nvidia's 3D support, it went into low-graphics and I'd spend 10 minutes getting to to go back to normal.

---

### Post by Jookia on 2008-05-10
After yelling at my computer, I have found out the problem is:

Nvidia GLX 'new' driver isn't doing anything
Enabling 3D acceleration is causing me to go into low-graphics.

---

### Post by Jookia on 2008-05-10
I found out my problem. I don't have a fix.

It won't let me enable nvidia glx-new driver. if I try, I restart, it goes in to low-graphics mode since it won't enable the driver. I look in the driver menu, there's no glx-new, only nv and nvidia, I tried nvidia, but it just error'ed me when using 'Test'. PLEASE help.

---

### Post by Jookia on 2008-05-10
I'm currently in BADLY need of help..

---

### Post by Robocoastie on 2008-05-10
aye join the club. I "thought" I had the nvidia driver working last night after following a thread here about how to install the driver fresh from the nvidia site and it did work - until I rebooted. At which point I'm right back to being forced into low graphics again.

If the problem is the driver I'll just go back to 7.10 until it's resolved but I think its actually the new xorg that's in Heron otherwise it wouldn't work at all like it did before a reboot.

Rob

---

### Post by Seks on 2008-05-10
Distro/GFX card/using wubi?

(glx-new is nvidia btw)


I found using wubi will not let me use the nvidia-glx-new driver but a native install fixed that. Also I recommend using EvnyNG to install.

---

### Post by Robocoastie on 2008-05-11
First I saw this thread: [http://ubuntuforums.org/showthread.php?t=763236](http://ubuntuforums.org/showthread.php?t=763236)

most of which had instructions I had already tried. What was NEW me was STEP 9.  That last step is very very important. Without step 9 xorg will default back to "nv".

I had to do one more step after that and that's something I have to do with every *nix install even 7.10 - my monitor just never gets detected right. So if you have that problem as well you will need to look in your monitor's book or website for its complete refresh rate list because you'll have to add its HorizSync and VertRefresh limits under the "Monitor" section and under Section "Screen" you'll have to enter the modes by hand. In my case I just set my modes for "1280x1024" "1024x768" "800x600"

Even though my card and monitor can handle higher and lower, I simply don't use anything other than those 3.

I suspect the nvidia issue with hardy is NOT the nvidia driver but is actually whatever got changed in xorg because the same driver works flawlessly in 7.10 (but I still have to do the monitor tweeks by hand).

Good luck. Feel free to PM me if you need further advice or want to refer me back to this because naturally with a new release the posts get buried rather quick to see.

Rob

---

### Post by Jookia on 2008-05-11
Alright, so it's going like this:

I configure it out of low-graphics mode.
I enable the NVIDIA accelerated graphics driver.
I restart and get low-graphics.
Repeat.

---

### Post by Jookia on 2008-05-11
Probably my last post for the day until it gets solved.

The nvidia driver isn't working.

[img]http://img230.imageshack.us/img230/8830/screenshotsk2.png[/img]

---

### Post by Jookia on 2008-05-11
PLEASE help me.

---

### Post by Jookia on 2008-05-12
Anybody?

---

### Post by jhetfield17 on 2008-05-12
Actually I had a clean install and after trying to get the 3D acceleration to work I got myself a perfectly low graphics prob.So after my father told me to I got into synaptic and removed anything that could relate to graphics(like envy linux restricted modules nvidia-glx-new and some more)then went and replaced my xorg with a backup from post-installation(the first backup) and then rebooted and upon login no error message.BUT when you login and install the nvidia driver from enabling it through the Hardware restricted modules thingy you reboot and get it again.So I'm just gonna do another clean install and hope I can fix it without getting low-graphics again.

---

### Post by Pap3r on 2008-05-12
Try ```
nvidia-xconfig
```

If that doesn't work, try Envy, install it from synaptics.

---

### Post by thedevnull on 2008-05-13
Same problem here.  :confused:  It just went to low graphics mode without any warning after like the 10th boot.  If I find out more I will post some info for you.  

You can always reboot and go to recovery mode.  Then select Fix X and it will get you working till the issue is resolved.

---

### Post by Jookia on 2008-05-13
It happened like this

I wanted to try other nvidia drivers

I uninstalled nvidia GLX new

(not sure if I rebooted or not)

I downloaded drivers from nvidia site

They didn't work

I tried to reinstall glx-new

enabled 3D

rebooted

low graphics

---

### Post by jhetfield17 on 2008-05-13
I think that uninstalling glx-new is that whick triggers the low-graphics prob cause I uninstalled it too and got the prob even if I uninstalled some other things.

---

### Post by Jookia on 2008-05-13
Somehow I fixed it, by removing all nvidia related stuff using package manager then using envy. [How the hell did I think that up?!]

---

### Post by jhetfield17 on 2008-05-14
I think half of it is tha same as i did.I just didn't use envy.:P

Anyways good for u.If btw you fix the 3D accel let us know.Cause I'm really pissed off at it and its the reason for getting that low graphics prob.

---

### Post by mattalexx on 2008-05-16
This is a driver conflict. Disable the other one:

[LIST=1]
[*]Install the correct driver from [nvidia.com]("http://nvidia.com"). You have to exit Gnome first.
[*]In /etc/default/linux-restricted-modules-common, add "nv" to DISABLED_MODULES.
[*]Restart.
[/LIST]

I wasted the whole day trying in vain to fix this problem, that that worked. Here's where I found it:

[http://quail.southernvaleslug.org/webblog/archives/48](http://quail.southernvaleslug.org/webblog/archives/48)

---

