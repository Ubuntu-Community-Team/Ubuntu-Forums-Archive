---
title: "Lirc - Why is Compile needed"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by jbencic on 2007-03-08
I finally got my mce/Phillips  Remote Control up and running with Feisty having to build the lirc_mceusb2 module 

i just have one question with regards to needing to compile the lirc module 


is it possible to configure any remote control using say the IR port of a laptop and just configure the /etc/lircd/lircd.conf with the correct control mappings?


i tried to do a cat on the /dev/input/eventX  using the MCE remote on a different IR port and the responses i got for every key was 'TAB'

it would be nice not to lug this bulky IR receiver around and just use a onboard laptop IR or a IR port that comes with the Capture card.

---

### Post by pelago on 2007-03-13
I believe IR ports on laptops use a different protocol (called IRDA) which is not the same as remote control-style IR, which is sometimes called CIR (Consumer IR). So I don't think you can use the laptop IR port as a receiver for a remote control.

---

### Post by Rever75 on 2007-03-14
How did you get the lirc_mceusb2 module to compile? I keep getting this error in feisty....

make[6]: *** [/home/rever/temp/Mythtv/lirc-0.8.1/drivers/lirc_mceusb2/lirc_mceusb2.o] Error 1
make[5]: *** [_module_/home/rever/temp/Mythtv/lirc-0.8.1/drivers/lirc_mceusb2] Error 2
make[5]: Leaving directory `/usr/src/linux-headers-2.6.20-10-generic'
make[4]: *** [lirc_mceusb2.o] Error 2
make[4]: Leaving directory `/home/rever/temp/Mythtv/lirc-0.8.1/drivers/lirc_mceusb2'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/rever/temp/Mythtv/lirc-0.8.1/drivers/lirc_mceusb2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rever/temp/Mythtv/lirc-0.8.1/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rever/temp/Mythtv/lirc-0.8.1'
make: *** [all] Error 2

---

### Post by jbencic on 2007-05-25
> How did you get the lirc_mceusb2 module to compile? I keep getting this error in feisty....

i had to download it and build it from source, i think it was because getting the same problem as you

[www.lirc.org](www.lirc.org)

Get the sources:

    > cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
		

Compile:
> 
    cd lirc
    ./autogen.sh
    ./setup.sh
    make
		

---

