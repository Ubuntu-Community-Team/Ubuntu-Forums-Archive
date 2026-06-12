---
title: "Gimp removal - gimp is not installed!"
date: 2020-01-05
forum: Multimedia Software
---

### Post by 3billy3 on 2020-01-05
Hi, I'm a new Lubuntu user. I have successfully installed Lubuntu 19.04 on my Asus laptop - all is/was working well.

I thought I would install Gimp and ended up with a bad install of the program, I used a snap command - Gimp runs but no tool icons show.

I then installed Gimp from the software center, the program worked perfectly but i was left with 2 versions of Gimp - one that works fine and one that doesn't. 

I then thought that i would remove both of the installations and start again, the Gimp version that works OK has been removed without any problems, 
I can't get rid of the version that doesn't work properly. When I run the $ sudo apt-get remove gimp it says that Gimp isn't installed

I have run snap list and it shows Gimp 2.10.14 in the list

Can anyone suggest how I might remove it so I can install the version that does work?

Thanks in advance

---

### Post by howefield on 2020-01-05
Try..

```
sudo snap remove gimp
```

to remove the snap version.

Also, 19.04 goes End of Life this month so not a great choice if you have only recently installed it, you'll probably want to upgrade to 19.10

---

### Post by ajgreeny on 2020-01-05
Try command ```
sudo snap remove gimp
``` and if that gets rid of the snap version of gimp you can reinstall the deb version with ```
sudo apt install gimp
```
Snap packages are handled, installed, removed etc etc using the snap commands shown in ```
man snap
``` and not using apt.

---

### Post by 3billy3 on 2020-01-05
Thank you, that's sorted it!

---

