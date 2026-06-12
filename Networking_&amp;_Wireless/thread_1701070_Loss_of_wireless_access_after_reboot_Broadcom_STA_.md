---
title: "Loss of wireless access after reboot: Broadcom STA driver &quot;active but not in use&quot;"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by alex_mallet on 2011-03-06
Hi - I'm running Ubuntu 10.10 on a Dell Inspiron XPS. I'm using the Broadcom STA driver for wireless access [I have a Broadcom BCM43224 card], and am running into the problem that after a reboot, the driver seems to no longer be in use: per System > Additional Drivers, the driver is activated, but not in use, with the net result being that I have no wireless access. The only way I've found of fixing this is to remove the driver and then re-activate it. 

How do I get the driver to actually be used after a reboot without having to go through removing & reactivating it ?

---

### Post by bkratz on 2011-03-06
> **alex_mallet said:**
> Hi - I'm running Ubuntu 10.10 on a Dell Inspiron XPS. I'm using the Broadcom STA driver for wireless access [I have a Broadcom BCM43224 card], and am running into the problem that after a reboot, the driver seems to no longer be in use: per System > Additional Drivers, the driver is activated, but not in use, with the net result being that I have no wireless access. The only way I've found of fixing this is to remove the driver and then re-activate it. 

How do I get the driver to actually be used after a reboot without having to go through removing & reactivating it ?



Not on my Ubuntu system right now, but if memory serves look at

gksudo gedit /etc/modules

and see if it says both wl and lp or just lp. If just lp we will probably have to add the wl here so it will load when booting.

---

### Post by taylorchase on 2011-03-06
try unloading the driver and re-loading it via the terminal:
```
sudo make wlunload b43
``````
sudo modprobe b43
```

That's if you use compat-wireless to compile and install the driver

---

### Post by bkratz on 2011-03-06
> **taylorchase said:**
> try unloading the driver and re-loading it via the terminal:
```
sudo make wlunload b43
``````
sudo modprobe b43
```

That's if you use compat-wireless to compile and install the driver



The OP is using the STA driver, not the b43. He/she should just need to add it to the location mentioned.

---

### Post by alex_mallet on 2011-03-07
Editing /etc/modules did the trick, thanks !

-Alex.

---

### Post by jemt on 2011-03-27
I'm expirencing the problem on my MacBook Pro (from 2010) too. Removing and activating again temporarily solves the problem - until next reboot. Hopefully fixed in upcomming release (April).

---

### Post by bkratz on 2011-03-27
> **jemt said:**
> I'm expirencing the problem on my MacBook Pro (from 2010) too. Removing and activating again temporarily solves the problem - until next reboot. Hopefully fixed in upcomming release (April).



have you checked the location mentioned in post 2?

---

### Post by pratikkhemka on 2011-04-17
Hello, I am using Dell XPS Studio 13. I have installed Ubuntu 10.10 on Virtual machine and I have the same problem. I do not think it is a problem of the virtual machine. The ifconfig command shows only 2 interfaces : eth0 and lo. Also I made the change to /etc/modules file as said in this forum and it showed only lp so I added wl as well but it does not detect any wireless interface.
I had faced a similar problem on ubuntu 9.10 too
Please help with this. Please let me know if you require any particular command outputs..

---

### Post by leokemps on 2011-07-03
I have used the command like was suggested 'gksudo gedit /etc/modules....'

Its just add a new line with 'wl' command? Like This?

"# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
"

thanks in advance!
:)

---

### Post by kblue on 2011-10-25
followed bkratz' method, works like a charm! thanks =D>

---

### Post by bkratz on 2011-10-25
> **kblue said:**
> followed bkratz' method, works like a charm! thanks =D>




Glad to be of help--enjoy!

---

### Post by Pepe_de_Bienvenida on 2011-11-05
adding wl to /etc/modules perfectly worked for me (on Peppermint). thanks kratz :mrgreen: :mrgreen: :mrgreen:

---

### Post by bkratz on 2011-11-05
> **Pepe_de_Bienvenida said:**
> adding wl to /etc/modules perfectly worked for me (on Peppermint). thanks kratz :mrgreen: :mrgreen: :mrgreen:


Certainly glad you got it too!

---

