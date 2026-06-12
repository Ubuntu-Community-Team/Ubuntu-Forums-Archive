---
title: "Mythtv backend closing when scanning for channels"
date: 2009-05-13
forum: Mythbuntu
---

### Post by adamjseed on 2009-05-13
Hello,

I think i have set up everything correctly in mythtv backend but when i go to scan for channels they app closes, doesnt crash but just closes and askes me if i want to update the database. 

It only happens when i scan for channels, when i change the input from composite0 to dvb. but im presuming i need to scan for channels on dvb.

The tv card I'm using is a hauppauge nova-HD-S2
This is what comes up in the log:

server kernel: [  954.730544] mythtv-setup.re[6101]: segfault at 128 ip 00007fa241feaf40 sp 00007fa2386d8878 error 4 in libqt-mt.so.3.3.8[7fa2419f7000+80d000]

anyone got any ideas?

---

### Post by adamjseed on 2009-05-13
im now thinking that my tv card may not be install correctly, 

I have looked on [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000) but it is a bit over my head. 

how can i check to see if it is installed? working?

---

### Post by Neon Dusk on 2009-05-16
What version of Mythbuntu are you using?

In Jaunty the firmware file for the HVR 4000 is corrupt - see [here](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/363682).

---

