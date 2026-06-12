---
title: "[SOLVED] webcam not working - compaq presario c700 laptop"
date: 2008-10-03
forum: Multimedia Software
---

### Post by hitesh_1717 on 2008-10-03
**[SIZE="4"]I have a compaq presario C700 laptop with inbuilt webcam:D......but i dont know how to use it in ubuntu 8.04:(.....pls guide...[/SIZE]**

---

### Post by linuxwizard on 2008-10-04
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga doesn't work post results of the command > lsusb

---

### Post by hitesh_1717 on 2008-10-04
Thanks Linuxwizard......by using your advice now i am able to take pictures using ekiga.....i am trying to gradually switch over to ubuntu from windows XP..... is there any other application also available to take pictures using webcam.....can i record my videos using ekiga....i can now take pictures bt still i m not sure of what other uses ekiga can have....pls guide...

---

### Post by hitesh_1717 on 2008-10-04
by the way this is the result which i got by using command lsusb

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000 



what does it actually means??/:confused:

---

### Post by linuxwizard on 2008-10-04
You can try using Cheese > [http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/) > or Camorama. They are both in the repo.

Here is more info on Ekiga > [http://wiki.ekiga.org/index.php/Main_Page](http://wiki.ekiga.org/index.php/Main_Page)


lsusb = it lists Product and Vendors ID # for USB devices.

---

### Post by hitesh_1717 on 2008-10-05
Thanks for your help....its really working for me...

but i am not able to install CHEESE.....its manual says to type the command "./configure; make; make install"...but whe i do this...this is what comes...
 


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/hitesh/cheese-2.24.0':
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

---

### Post by xc3RnbFO8P on 2008-10-05
You can install **Cheese** from:
Application> Add/Remove (all available application)

---

### Post by hitesh_1717 on 2008-10-06
thanks Ringi....cheese is really great...i like the special effects:guitar:....but i am not able to record a video using it....what should i do???

---

### Post by dadisunil on 2008-11-04
Hi, 

I have installed cheese and I am able to capture the pictures. I am trying to install the veriface application. However, it's not detecting the webcam. 

Can you help me with this?

Thanks in advance!

Sunil

> **linuxwizard said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga doesn't work post results of the command > lsusb

---

### Post by mzolisto01 on 2010-06-21
im new to Linux and mine still doesn't work below are the results of the command

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 174f:5212 Syntek USB 2.0 UVC PC Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Pls help im using Ubuntu 10.04 LTS   - the Lucid Lynx -

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG]

---

### Post by no2498 on 2010-06-21
mzolisto01

in/on 910 and up cheese webcam booth is/should be loaded
look in sound & video

try the cam in cheese first


this is the cam you have
174f:5212 Syntek USB 2.0 UVC PC Camera

it should just work

---

### Post by mzolisto01 on 2010-06-23
> **no2498 said:**
> mzolisto01

in/on 910 and up cheese webcam booth is/should be loaded
look in sound & video

try the cam in cheese first


this is the cam you have
174f:5212 Syntek USB 2.0 UVC PC Camera

it should just work


just installed cheese and it works thanks a mil guys

---

