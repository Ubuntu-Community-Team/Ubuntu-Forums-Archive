---
title: "VLC does not stop"
date: 2009-01-31
forum: Multimedia Software
---

### Post by DeMus on 2009-01-31
I did a fresh install of Hardy Heron 8.0.4.2 and got it all working again. I also installed VLC and use it as my favorite media player, like before.

Now when I play a video and stop the program I notice it is still running as a process in the system monitor. I never saw that before, maybe I also wasn't looking for it.

When I stop the program without stopping the video first, the program stops and the window disappears, **BUT** the sound keeps going on.
Okay, your answer would be: then stop the video first. I know, I thought about that and when I do that it works, but is it normal that VLC stays in memory as a process?
As said before, I never saw that happening before.

---

### Post by gjoellee on 2009-01-31
The VLC logo will appea in the notification area (found in panels by default), Right click on it and hit "exit" to exit. That should to it.

---

### Post by jimmyhacker on 2009-01-31
I think something is really wrong in ubuntu`s kernel (the wrong memory handling and can`t kill some huge processes) and 8.10 is buggy for now i still use 7.10 and i downloaded all .deb`s to a 10 GB partition and when repository will be rwmoved i will have debs or i move file`s by puppy linux
if i want to move xmms to ubuntu by puppy i will copy:

/usr/local/bin/xmms
/usr/share/xmms
/usr/lib/libxmms.so

and other codec libraries.

Try amarok or Xmms.VLC in repos are really out-of-date and for compiling vlc
you will need WxWidgets and other Wx utils wich makes 400 MB :((.

---

### Post by DeMus on 2009-01-31
> **gjoellee said:**
> The VLC logo will appea in the notification area (found in panels by default), Right click on it and hit "exit" to exit. That should to it.

Thanks for your answer, however I don't get a logo in the notification area. I do get it from Rythmbox and other programs, but not VLC.
I looked in the settings but can't find where to switch it on.
Do you know?

---

### Post by linux_tech on 2009-01-31
> **jimmyhacker said:**
> I think something is really wrong in ubuntu`s kernel (the wrong memory handling and can`t kill some huge processes)

Give htop a try

---

### Post by redroad55 on 2009-01-31
Hi, Right click Applications.. select edit menus ..select sound and video on left box  .. right click on vlc in right box , choose properties in drop down menu .. In lower left corner choose help and read launcher properties .. Hope this helps you .. Best to you .. Post back your results and or questions ..

---

### Post by mc4man on 2009-01-31
> however I don't get a logo in the notification area.
The version offered in hardy, 0.8.6 does not have a notifications icon. It's also fairly common for 0.8.6 to continue on if you close out vlc without stopping playback.

There is a launchpad ppa (Korn) that offers the 0.9.8a version for hardy, though it (all 0.9x rev.'s) has issues/breakages, it would depend on your usage as to which would be more suitable for you.

---

