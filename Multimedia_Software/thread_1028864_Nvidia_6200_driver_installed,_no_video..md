---
title: "Nvidia 6200 driver installed, no video."
date: 2009-01-02
forum: Multimedia Software
---

### Post by gasto on 2009-01-02
I tried to install with the driver help utility(Restricted Drivers Manager ) in Ubuntu 8.10, but did not work.

So I tried to do it with the NVIDIA-Linux-x86-177.82.pkg1.run supplied at the Nvidia web page.

Of course it gave me an error: close X server.
So searching on Google I got a webpage explaining that, to stop the X server, type on the command line:

/etc/init.d/gdm stop

I then typed (at the virtual terminal):

sudo sh NVIDIA-Linux-x86-177.82.pkg1.run

and it ran seemingly well, it asked for visiting the FTP Nvidia site for downloading the precompiled kernel interface, none was found, so it compiled it automatically, gave 0 errors, and then sent me back to the command line, I just typed:

sudo /etc/init.d/gdm start

And the GNOME Display Manager was started, so the Ubuntu start page asked me my user name, password(displayed in the default enlarged resolution), and after that no video was seen (black screen).

Any help , really appreciated. 

Thanks in advance.

---

### Post by gasto on 2009-01-03
I am reluctant to think that nobody else had this problem, considering Nvidia sells for mainstream customers.

By the way 177 from the driver assistant did not work.

---

### Post by gasto on 2009-01-03
Uhhhm, what can I say, I am not that fluent in Linux, so I don´t know what try out.

---

### Post by gasto on 2009-01-06
Update I tried envy.

started with:

sudo apt-get update && sudo apt-get install envyng-gtk envyng-core

from the virtual terminal,and then:

sudo envyng -t

I ran the installation (because apparently it didn´t detect the previous faulty Nvidia driver).

Same issue as before, after the output of the console where successfully installed appeared somewhere, the system tried to restart but failed. So I restarted the computer manually, by pressing the restart button on the case. Then same issue, no video after the account selection. (same wide screen at the account selection)

---

### Post by gasto on 2009-01-06
¿ehm, anybody here?

---

### Post by gasto on 2009-01-07
I guess Nvidia drivers are a pain to install that's why I receive 0 replies, nobody wants to mess with this nightmare. Sigh, if only Ubuntu was what it claimed to be, I wouldn't be disappointed.

---

