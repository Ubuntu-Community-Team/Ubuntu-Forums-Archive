---
title: "Latest nvidia drivers"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by loserboy on 2006-06-20
im so new at this its not evern funny so if this is silly let me know.

i see the thread about getting the latest nvidia drivers, but can't I just use synaptic and get nvidia-glx? or am i missing something

thanks

---

### Post by meng on 2006-06-20
I used the nvidia-glx through synaptic strategy. (If you have nvidia-settings installed from a previous breezy, it is okay to uninstall it as nvidia-glx includes nvidia-settings.)

---

### Post by loserboy on 2006-06-20
ok cool so we have the latest drivers right?

---

### Post by meng on 2006-06-20
alt-f2, type nvidia-settings and you can see for yourself. My driver version is 1.0-8762.

---

### Post by loserboy on 2006-06-20
I dont see the version anywhere, and the only things i can do is check some boxes

---

### Post by meng on 2006-06-20
That's funny. When I run nvidia-settings, the first/default screen/tab shows NVIDIA Driver Version at the bottom. Does yours not show that?

---

### Post by thepizzaking on 2006-06-20
Open the terminal and type: cat /proc/driver/nvidia/version

---

### Post by loserboy on 2006-06-20
nah mine didnt show that, but the command works and i have 1.0-8762

maybe i dont have that nvidia settings thing installed

thanks guys

---

### Post by loserboy on 2006-06-20
now if i could just get 3d stuff to work

---

### Post by tseliot on 2006-06-21
[QUOTE=loserboy]ok cool so we have the latest drivers right?[/QUOTE]
Yes, at least for now. When a new driver is released you won't find it in Ubuntu's repos and then you will have to use either my Method 2 or my script.

---

