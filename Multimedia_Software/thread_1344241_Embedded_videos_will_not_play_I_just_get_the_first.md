---
title: "Embedded videos will not play I just get the first frame"
date: 2009-12-02
forum: Multimedia Software
---

### Post by zappadragon on 2009-12-02
Ok so I am running 9.10 and I have all the drivers to play video on youtube and other video sites, but when I try to play a video that is embedded on a forum I just get the starting frame with the play button. When I click the play button nothing happens. What can I do to fix this.

Thanks

---

### Post by lovinglinux on 2009-12-02
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by zappadragon on 2009-12-02
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

Thanks I tried that and its still not working. Any other options?

---

### Post by zappadragon on 2009-12-02
I figured out a work around. If I right click on the embedded video the menu options come up. The first time I clicked watch on youtube. Then I figured out if you just right click and bring up the menu options then click away, next if I click the embedded video it will play. Not the best option but it will work for now.

---

### Post by lovinglinux on 2009-12-02
> **zappadragon said:**
> Thanks I tried that and its still not working. Any other options?

Do you get a small play button or a big play button like [this](http://img371.imageshack.us/img371/4727/screenshotne8.png)?

---

### Post by zappadragon on 2009-12-07
> **lovinglinux said:**
> Do you get a small play button or a big play button like [this](http://img371.imageshack.us/img371/4727/screenshotne8.png)?

I just get the smaller one.

---

### Post by lovinglinux on 2009-12-07
> **zappadragon said:**
> I just get the smaller one.

In this case, my solution does not apply. I don't know why you can't click the small play button. Perhaps you could create a clean firefox profile to check if the problem is system wide or related to Firefox settings. See the tutorial in my sig for additional info on Firefox profiles.

---

### Post by zappadragon on 2009-12-07
> **lovinglinux said:**
> In this case, my solution does not apply. I don't know why you can't click the small play button. Perhaps you could create a clean firefox profile to check if the problem is system wide or related to Firefox settings. See the tutorial in my sig for additional info on Firefox profiles.

This is what I got:

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/danny/.mozilla/plugins/libflashplayer.so [/home/danny/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

---

### Post by lovinglinux on 2009-12-07
> **zappadragon said:**
> This is what I got:

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /home/danny/.mozilla/plugins/libflashplayer.so [/home/danny/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

If you are not using 64bit version of flashplayer downloaded manually and placed under ~/.mozilla/plugins then I would recommend deleting /home/danny/.mozilla/plugins/libflashplayer.so and installing it from Synaptic.

```
sudo apt-get install flashplayer-nonfree
```

---

### Post by lovinglinux on 2009-12-07
Take a look at [this](http://ubuntuforums.org/showthread.php?t=989448) thread.

---

