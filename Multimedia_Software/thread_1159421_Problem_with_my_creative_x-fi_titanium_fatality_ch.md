---
title: "Problem with my creative x-fi titanium fatality champion"
date: 2009-05-14
forum: Multimedia Software
---

### Post by jasone on 2009-05-14
Hello everyone,
I just installed ubuntu 9.04.
The system does not recognize my soundcard so i downloaded the XFiDrv_Linux_Public_US_1.00 driver from the site of creative.
I followed many instruction i found on many topics. I downloaded build - essentials and i tried make, make install etc. The messages i get at my terminal is the following:


iasonas@iasonas-pc:~/Desktop/XFiDrv_Linux_Public_US_1.00$ **sudo make**
[sudo] password for iasonas: 
make -C /lib/modules/2.6.28-11-generic/build M=/home/iasonas/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
iasonas@iasonas-pc:~/Desktop/XFiDrv_Linux_Public_US_1.00$ **sudo make install**
Copy module files...
Update module dependency relationships...
iasonas@iasonas-pc:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 

The strange thing is that in system>administration>hardware drivers the system recognizes a driver x-fi driver version 1.00 but i still have no sound.
The soundcard works fine in windows xp so i don't think there is a hardware issue.

I know there have been many topics on this subject but i 've been searching for 2 days and i couldn't find anything.

P.S Please note that i am a complete newbee so please give me specific instructions.

Thank you veryvery much

---

### Post by jasone on 2009-05-14
Ok i made it work
As i said i followed the instructions in [http://ubuntuforums.org/showthread.php?t=870001 ]("http://ubuntuforums.org/showthread.php?t=870001")
and i changed the file from 41 to 42 but it did not work.
After i posted the topic i changed to 43 and fortunately that did the trick!!!;)

Now should i select the ALSA or OSS in sound settings?
What's the difference?
Do you know any good program to manage my surround speaker settings?

---

