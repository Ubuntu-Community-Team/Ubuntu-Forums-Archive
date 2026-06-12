---
title: "Can't save X configuration file?"
date: 2009-10-07
forum: Multimedia Software
---

### Post by mannyfresh8 on 2009-10-07
Trying to save to X configuration File but keep receiving error. I have a dual monitor setup and it doesn't allow me to setup the screens. I try to save the twin view setup. It works until I restart the system which it then goes back to the default settings.

Error: 
unable to create new X config backup 
file '/etc/x11/xorg.con.backup'.

Graphics Card - GE Force GTS 250
Driver version - 180.44
OS - Ubuntu 9.04

---

### Post by doas777 on 2009-10-07
did you lau7nch nvidia settings with gksu?
```
gksu nvidia-settings
```

---

### Post by mannyfresh8 on 2009-10-07
I should have mentioned I am a complete Noob when it comes to a Linux OS. So should I open a new Terminal and type that code in?

All I did was install the newest driver that Ubuntu recommended and proceeded to adjust the settings using the Nvidia Controls.

---

### Post by doas777 on 2009-10-07
> **mannyfresh8 said:**
> I should have mentioned I am a complete Noob when it comes to a Linux OS. So should I open a new Terminal and type that code in?

All I did was install the newest driver that Ubuntu recommended and proceeded to adjust the settings using the Nvidia Controls.

easiest way is to hit Alt+F2 to launch the "run Application" bar (but yes it would work in a terminal). then paste in that command and it will prompt you for your password before launching. if it does not ask, then you will not have the rights to save to xorg.conf. 

if you want, you can edit your menu launcher to use gksu when running nvidia-settings from System -> Administration

---

### Post by Bucky Ball on 2009-10-07
Problem is you need to STOP X to make any changes. Then when you either restart X or reboot your machine they will stick (persistent). To restart X:

```
startx
```

---

### Post by doas777 on 2009-10-07
> **Bucky Ball said:**
> Problem is you need to STOP X to make any changes. Then when you either restart X or reboot your machine they will stick (persistent). To restart X:

```
startx
```

it is true that when editing the file by hand, you need to restart x before you see your changes. with nvidia-settings however MOST settings are applied on demand, but they do not become persistent across reboots until the xorg.conf is updated. 

op, you will probably not need to stop x to perform your tweaks, unless you are editing the file by hand. alternatively, you can edit the file with x running, but will have to reboot or restart x before you will see changes.

---

### Post by mannyfresh8 on 2009-10-07
> **doas777 said:**
> easiest way is to hit Alt+F2 to launch the "run Application" bar (but yes it would work in a terminal). then paste in that command and it will prompt you for your password before launching. if it does not ask, then you will not have the rights to save to xorg.conf. 

if you want, you can edit your menu launcher to use gksu when running nvidia-settings from System -> Administration


Thanks a lot. This worked. Don't be surprised if you see me posting a lot of stupid stuff in the near future. 

Thanks again.

---

### Post by doas777 on 2009-10-07
np yo. welcome to the community

---

### Post by Bucky Ball on 2009-10-07
Welcome and good news. Please mark thread as 'solved' in the Thread Tools to help others. :)

---

### Post by mannyfresh8 on 2009-10-07
Thanks I saw that tool and did it. See you around

---

### Post by Bucky Ball on 2009-10-08
> **mannyfresh8 said:**
> Thanks I saw that tool and did it. See you around

A pleasure and welcome to the forums and Linux land!

---

### Post by jordanchap on 2009-10-31
How can you make the menu launch with gksu like you mention in this thread?  That would be very helpful!

---

### Post by Bucky Ball on 2009-11-01
Which menu exactly?

---

