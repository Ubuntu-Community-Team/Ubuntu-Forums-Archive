---
title: "X Server Error - Newbie help desperately needed!"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by dannythomas13 on 2006-06-29
hi, i was reading through my new ubuntu book and it said about installing drivers for nvidia cards so i followed what it said and downloaded the nvidia-glx stuff and ran "sudo nvidia-glx-config enable", when i did this it said some error but that i could get past it by typing some command, contained something like md or something but as i dont remember that isnt much use..sorry. anyway, i ran this command and then it let me run the glx-config enable but said i needed to restart. when i did this i get a blue screen of death saying:
Failed to start the X server (your graphical interface). It is likely that this is not set up correctly. Would you like to view the X Server output to diagnose the problem...but i have no idea what it all means even though it seems to contain nothing useful. I then get shown a screen saying:
The X Server is now disabled. Restart GDM when it is configured correctly.
and then i am able to login as command prompt but i dont understand this as i only started using ubuntu as the gui seemed impressive.
please can someone help me fix this or at least get it back to how it was
thanks
Daniel

ps i have tried the obvious in command prompt:
"sudo nvidia-glx-config disable" but it didnt fix the problem

---

### Post by crispingatiesa on 2006-06-29
Loggin, then

at the command pront type:

[HTML]sudo pico /etc/X11/xorg.conf[/HTML]

find the section when de driver is defined and change whatever NVIDIA reference by:

"vesa"

Reboot. You should be able to go gnome then.

---

### Post by dannythomas13 on 2006-06-29
ok, something weird has happened here, when i did the pico i searched through the file and there are no references to nvidia, but what is weirder is that there are loads of references to ATI Radeon, which i dont have (used to but sold a long time ago before installing ubuntu too), i have a nvidia geforce 6600gt
is there any way all this can get cleared up so gnome will work as well as all of the 3d graphics?
thanks in advance to anyone who can help
Daniel

---

### Post by crispingatiesa on 2006-06-29
Try

---

### Post by crispingatiesa on 2006-06-29
Try

[HTML]sudo dpkg -reconfigure xserver[/HTML]

---

### Post by tseliot on 2006-06-29
[QUOTE=crispingatiesa]Try

[HTML]sudo dpkg -reconfigure xserver[/HTML][/QUOTE]
The exact command is:
```
sudo dpkg-reconfigure xserver-xorg
```

Select "vesa" as graphic driver. Press ENTER when you don't know the answer to the questions it asks you.

Then:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by dannythomas13 on 2006-06-29
thanks for that, i'm back up and running! =)
i did however select nvidia rather than vesa as i do have an nvidia card.
does anyone know if i can now do "sudo nvidida-glx-enable" or will it then mess ti all up again?
thanks again

---

### Post by tseliot on 2006-06-30
[QUOTE=dannythomas13]thanks for that, i'm back up and running! =)
i did however select nvidia rather than vesa as i do have an nvidia card.
does anyone know if i can now do "sudo nvidida-glx-enable" or will it then mess ti all up again?
thanks again[/QUOTE]
Please don't use "sudo nvidia-glx-enable" (it's broken).

Selecting "nvidia" as you did is enough.

Enjoy your driver ;) 


P.S. the next time you install the driver you can use "sudo nvidia-xconfig" instead of "sudo nvidia-glx-enable". And here is my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

