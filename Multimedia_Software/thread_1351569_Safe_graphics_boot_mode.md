---
title: "Safe graphics boot mode?"
date: 2009-12-10
forum: Multimedia Software
---

### Post by nategerr on 2009-12-10
Is there any way to boot up a linux box with default low screen resolution? I'm really stuck on an uncompatible setting and can't see anything past the splash screen to change it back. How bout a command in the terminal?

---

### Post by markbuntu on 2009-12-11
From grub there is a recovery kernel boot option just below the normal boot line. Boot into that and use the fix x option and then resume or choose the command line option and do stuff from there.

---

### Post by nategerr on 2009-12-11
I got into the grub menu but I only have 3 options.
Ubuntu 9.10 2.6.31-15-generic
"-16-generic
"-14-generic
memory test
 
Is there a rescue disk linux offers so I can just boot with that?

---

### Post by RedSingularity on 2009-12-11
So you cant get to the terminal at all?

---

### Post by nategerr on 2009-12-11
yes,if i hit ctrl alt f1-f6. but becuase i'm super new with linux and don't know many commands yet i'm not sure what totype once there to change my screen res. how do i reload menu.lst from the terminal?

---

### Post by RedSingularity on 2009-12-11
Go to a terminal and try this command,,

xorgconfig

Then reboot.

---

### Post by nategerr on 2009-12-11
xorgconfig - command not found. is there anything else I can try?

---

### Post by RedSingularity on 2009-12-11
Here try this.....

sudo dpkg-reconfigure xserver-xorg

---

### Post by nategerr on 2009-12-11
That didn't seem to work 
usr/sbin/dpkg-reconfigure: xserver-org is not installed
how do i instal this program?

---

### Post by RedSingularity on 2009-12-11
In the command line do 

sudo apt-get install ubuntu-desktop

---

### Post by nategerr on 2009-12-23
That's not working. It saya my desktop is already updated. is there command in the terminal that allows me to manually select screen resolution from a list?

---

### Post by RedSingularity on 2009-12-23
You can set your screen resolution inside the xorg.conf file.

Post the output of 

cat /etc/X11/xorg.conf

---

