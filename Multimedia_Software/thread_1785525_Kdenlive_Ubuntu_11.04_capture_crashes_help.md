---
title: "Kdenlive Ubuntu 11.04 capture crashes help"
date: 2011-06-18
forum: Multimedia Software
---

### Post by newguy0 on 2011-06-18
Hello all,
I have a Dell latitude D400 , with ubuntu 11.04 on it. Running quite nice. I have a jvc gr20 mini dv camcorder, and i'm trying to firewire my footage across. Now , it has trouble instailising, but can control my camcorder from Kdenlive i.e pause, play etc. When I try recording it plays the camcorder but does not record. Also does not show the camcorder feed on the laptop. 

I have to disconnect the camcorder in order to get anything to work, and it the tells me that Capture crashed. Check parameters. 

I have tried Kino, with no Joy. Can anyone help, this is getting really frustrating. 

Many thanks for any help.

---

### Post by newguy0 on 2011-06-19
Bump. Anyone got any idea's? This is driving me nuts.

---

### Post by newguy0 on 2011-06-19
Right, I found this (below), Tried it and it worked! for about 5 mins. Now has stopped working getting the same problem. I'm thinking about putting xp back on this laptop. 










From
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)  :

This method makes a new group called firewire   with control of the raw1394 device file, and your user a member of  that group. The camcoder must be plugged in and turned on at boot time  for this to work because udev will only create /dev/raw1394 if the  camcoder is present and /dev/raw1394 must be created before bootmisc.sh  is run.

   1.

      Open 'System > Administration > Users and Groups'. Add a new group and call it firewire
   2.

      Open the firewire group and add your user name to this group.
   3.

      Open a terminal and type

      sudo gedit /etc/init.d/bootmisc.sh

   4.

      At the end of the file type

      chgrp firewire /dev/raw1394

   5.

      Reboot, or to apply changes now type directly in a terminal

      sudo chgrp firewire /dev/raw1394

   6. Insure camcorder is connected and turned on before the system is booted.

---

### Post by newguy0 on 2011-07-01
Anyone got any thoughts on this? Like I said the firewire port is working. And I have it working, need help here.

---

### Post by newguy0 on 2011-07-02
Hello, anyone? :confused:

---

### Post by newguy0 on 2011-07-02
Is there no one with an answer? anyone know if older versions will work? 
I'm really ready to give up in ubuntu

---

### Post by newguy0 on 2011-07-03
Got it. Finally, took me a long time.

---

