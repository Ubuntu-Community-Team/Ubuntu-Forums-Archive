---
title: "Nvidia drivers killed the system"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by Slavedriver on 2006-10-08
After installing NVidia drivers the way it was said in Wiki (running *sudo nvidia-glx-config enable*) I ended up with xorg.conf saying that my video card is ATI Radeon and being unable to start X at all. I managed to fix it by replacing the file with the one from LiveCD. After that I still wanted to get my 3D acceleartion or at least a decent screen resolution (c'mon, 1024x768 is just not what I can call decent) so I ran *sudo dpkg-reconfigure xserver-xorg*. After following all step there and restarting X I finally got NVidia logo but now, just after the login screen, before the time Window manager must start I just hang there with empty desktop and cursor for friends. And nothing happens. Changing session to default one doesn't help. Changing session to GNOME safe doesn't work because I'm missing some install files. Replacing xorg.conf with a backed up one still does not help.

---

### Post by tseliot on 2006-10-08
nvidia-glx-config enable is buggy but it couldn't cause the 2nd problem you had.

Try this:
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```


That should help you to enter GNOME again.

THEN, if and only if you can enter GNOME again, you can follow method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Slavedriver on 2006-10-08
Thing is that X does work. The system just stops loading after login screen. I don't see this 3D-like splash screen which list the components being loaded (like Window manager and so on). I just see a standart wallpaper and the cursor. That's all.

---

### Post by tseliot on 2006-10-08
> **Slavedriver said:**
> Thing is that X does work. The system just stops loading after login screen. I don't see this 3D-like splash screen which list the components being loaded (like Window manager and so on). I just see a standart wallpaper and the cursor. That's all.

Try what I said and see if it solves the problem (which resembles a know bug of the nvidia driver). If it does, I will tell you how to solve it.

---

### Post by Slavedriver on 2006-10-08
Nope, it did not work. Neither did any manual config of X. lspci output is kinda lengthy and I can't dump it to the file to copy-paste (well, I can but I can't access ext3 from Win). My video card (which is GeForce 6600GT BTW) is on PCI 1:0:0

---

### Post by tseliot on 2006-10-08
> **Slavedriver said:**
> Nope, it did not work. Neither did any manual config of X. lspci output is kinda lengthy and I can't dump it to the file to copy-paste (well, I can but I can't access ext3 from Win). My video card (which is GeForce 6600GT BTW) is on PCI 1:0:0

I can't help you. I've never had your problem and I don't know what might have caused the problem.

Anyway I suggest you to reinstal Ubuntu and then use Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Slavedriver on 2006-10-08
Just used Method 1 of your guide. Didn't help. Reinstalling Ubuntu will help (doh) but I really don't want to loose 200+Mb of updates. And ubiquity will fail if you don't reformat the root partition.

---

