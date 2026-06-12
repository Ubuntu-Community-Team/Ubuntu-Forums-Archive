---
title: "Sound not working in Ubuntu 8.04 (Sony VGN-C 140G)"
date: 2009-07-24
forum: Multimedia Software
---

### Post by strawberrytd on 2009-07-24
I am a new bee to Ubuntu.
I installed Ubuntu one week back.Couple of times, Sound was not working while watching videos on internet.But once I rebooted-everything would come to normal.

But now even after reboots, sound has completely stopped working either from internet or from computer.Please someone let me know or send me the link to correct thread.

Thanks,

PS:I have skimmed through some threads but could not find a working solution.

---

### Post by igorzwx on 2009-07-24
You may better start here:

Ubuntu Linux for Dummies.chm

read some 20 pages
install another Ubuntu (better 9.04)
in duall boot (or multiple boot)

---

### Post by jerrrys on 2009-07-24
have you installed Ubuntu Restricted Extras, located in Synaptic Package Manager?

---

### Post by martinbaselier on 2009-07-24
First thing that pops my mind is alsamixer. When you open a terminal and start alsamixer, do you see any channels muted?

what kind of audio card do you have ?

**lspci | grep Audio -i**

will show you. 

to get more details use:

**sudo lspci -v -s cardnumber**
replace cardnumber with the number you got from the first command.

---

