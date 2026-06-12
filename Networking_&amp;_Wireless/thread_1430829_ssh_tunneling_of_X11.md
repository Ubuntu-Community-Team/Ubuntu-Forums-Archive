---
title: "ssh tunneling of X11"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by jmsgz on 2010-03-15
hi folks
   have good command line ssh connection between (2) ubuntu computers. both machines running gui. have also good server connection and remote desktop viewer between same. 

   am trying to tunnell X11 between machines.

at command line using

    :~$ ssh -X remote_machine.local.
        "then following connection and passwd verification
         on remote machine"
    :~$ xload
        which produces a blank white window on local host.

i have uncommented ForwardX11 yes in client ssh_config file also
                   ForwardX11Trusted yes   in same

any ideas?
      as usual thanks in advance.
jmsgz :-)

---

### Post by dmizer on 2010-03-15
I get the same results with xload. Other GUI apps work fine.

---

### Post by n0dix on 2010-03-15
I have a similar problem when i try to see an image from a Arch Linux machine.

---

### Post by jmsgz on 2010-03-15
Other GUI apps work fine.

Can you explain that? Do you mean some other command besides "xload" should be used?
OR do you mean remote desktop viewing or ssh file transer etc??

---

### Post by jmsgz on 2010-03-15
I would like to get the ssh tunnelling working because it would be so much faster than using remote desktop connections.

any info pass along 
thanks

---

### Post by jmsgz on 2010-03-15
thanks for the reply,,,,,been here about a year so just moving from gui's to command line...i know you info is good and it will take me awhile to digest it. But for home use it is good info.....thanks

---

### Post by dmizer on 2010-03-15
> **jmsgz said:**
> Other GUI apps work fine.

Can you explain that? Do you mean some other command besides "xload" should be used?
OR do you mean remote desktop viewing or ssh file transer etc??

xload is a gui program for monitoring the load on the X11 server. It doesn't seem to work over ssh with X forwarding. Try something like firefox instead.

---

### Post by jmsgz on 2010-03-15
firefox what not the web browser explain!
Read your tutorial on FTP server howto .....interesting!

---

