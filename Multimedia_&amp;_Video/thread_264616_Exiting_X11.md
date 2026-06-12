---
title: "Exiting X11?"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by Echo35 on 2006-09-24
So I got the nVidia driver from their website and tried running it, but it tells me that I need to quit X11. So I hit Ctrl+Alt+F4 to quit to the terminal, but that didn't work. So then I tried booting into the terminal but that didn't seem to work either. Can anyone help me out here? I'm running on no graphics card and it's kind of annoying.

---

### Post by henriquemaia on 2006-09-24
To turn off the X server you have to type on a terminal:

```
sudo /etc/init.d/gdm stop
```

After that, you can install the Nvidia drivers. 
When you want to start X again, type:

```
sudo /etc/init.d/gdm start
```


But why don't you use the ones provided on the repositories? It's a bit easier to do it that way.

---

### Post by gunderwood on 2006-09-25
Ctrl-alt-backspace restarts the x-server.

Greg

---

### Post by henriquemaia on 2006-09-25
> **gunderwood said:**
> Ctrl-alt-backspace restarts the x-server.

Greg

Restarts, but it doesn't stop. To Install Nvidia drivers by hand you have to stop the X server.

---

### Post by Echo35 on 2006-09-25
I tried the one from the repository and it didn't work (I think those ones are 32-Bit anyway). I tried modifying something per suggestion from someone and that just totally broke my X Server and I had to re-format. So, I'm hoping compiling it myself will work a bit better.

---

### Post by Echo35 on 2006-09-25
](*,) Ok, now I feel like a noob. Apparantly, the nVidia install from EasyUbuntu worked just fine, I just needed to reboot first... Gah, ok, it works now. Is there any sort of control panel for it though? I really liked the nVidia crontrol panel I had in Windows and I would like one for Linux too, if there is such a program.

---

### Post by NT4usB on 2006-09-25
> **Echo35 said:**
> ](*,) Ok, now I feel like a noob. Apparantly, the nVidia install from EasyUbuntu worked just fine, I just needed to reboot first... Gah, ok, it works now. Is there any sort of control panel for it though?...

yes there is.
(not in front of my machine atm so I don't know for sure what it's called... Nvidia-Settings or something?)

---

