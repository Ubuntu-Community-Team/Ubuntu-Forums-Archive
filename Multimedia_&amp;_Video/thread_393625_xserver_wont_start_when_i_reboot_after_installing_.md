---
title: "xserver wont start when i reboot after installing nvidia drivers"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by Kenjamin80 on 2007-03-25
i tried doing a search for info, but just couldnt find one.

i recently installed ubuntu and beryl on my pc on a spare drive.

i needed to install the nvidia drivers to make beryl work. i install the drivers from the tty1 interface and all goes well. it works perfectly. i restart gdm and i see the nvidia logo. i log in. everything is beautiful. if i reboot the machine though, i get the 'xserver cannot start' error saying it cant find any displays and such. i dont have the log, because im trying to not restart until i get this under control. if i reinstall the nvidia drivers again, everything is fine. whats going on?

any ideas would be great. anything you need, info wise, ask. im really new to the linux environment but im learning quickly.

---

### Post by simonn on 2007-03-26
[http://ubuntuforums.org/showpost.php?p=2294966&postcount=9](http://ubuntuforums.org/showpost.php?p=2294966&postcount=9)

---

### Post by tseliot on 2007-03-26
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine

then install Envy and follow the instructions on this page:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Read the part where it says "B) Can I use Envy 0.9.x if I had installed the Nvidia driver via Envy version 0.8.2 (or lower) or via the Nvidia installer?"

---

