---
title: "pinnacle 800i"
date: 2012-06-15
forum: Multimedia Software
---

### Post by jmore9 on 2012-06-15
Now this one has me puzzled .  I tried to run metv from the list of installed apps and nothing happend.  So i tried it from the command line.
This is what i got

(me-tv:4668): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
jeffm@jeffm-MS-7108:~$ 


Tried again after upgrading to 1.4 , this is what i got :

jeffm@jeffm-MS-7108:~$ me-tv
The program 'me-tv' is currently not installed.  You can install it by typing:
sudo apt-get install me-tv
jeffm@jeffm-MS-7108:~$ sudo apt-get install me-tv
[sudo] password for jeffm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
me-tv is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeffm@jeffm-MS-7108:~$ 

lspci :

02:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:02.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

It worked just fine under 11.10 and 11.04

Any ideas anyone ?

---

### Post by jmore9 on 2012-06-15
Now this is different on 11.04 and 11.10 kaffeine would not scan any channels no matter what i did.  I just got done with it and it scanned the channels and plays all of them with no pixelation at all.

But now in 12.04 me-tv decides it does not want ot work.

---

### Post by jmore9 on 2012-06-16
Well after messing around wqith metv all night it finally starts a little but gives this exit error :

Me TV 1.3.6
06/16/2012 15:20:59: Exception: Failed to initialise database

Now all i have to do is figure out what that means.  Maybe just manually deleting the database ?

---

