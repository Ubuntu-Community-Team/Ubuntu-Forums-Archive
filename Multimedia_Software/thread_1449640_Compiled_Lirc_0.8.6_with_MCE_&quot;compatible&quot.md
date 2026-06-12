---
title: "Compiled Lirc 0.8.6 with MCE &quot;compatible&quot; remote"
date: 2010-04-08
forum: Multimedia Software
---

### Post by Zemy on 2010-04-08
Hi all,
 
I have faced a problem with using lirc 0.8.6 on Ubuntu910.
/dev/lirc0 will not be created on reboot. Somehow it is related
module lirc_mceusb loading.
What I have done is basic Ubuntu910 desktop installation and after that
compiled Lirc 0.8.6 from source. I had to compile it to get my USB IR-receiver
to work. The device Realtek eHome IR receiver (0bda:0161) was not listed in lirc
source. Added the vendor information and the usb device information to lirc_mceusb.c
source file. After that compiled the lirc and installed. Everything good so far.
Then commands;
sudo modprobe lirc_mceusb
sudo /etc/lirc restart
 
lirc0 is created to /dev/ and everything works ok, response is right to irw.
 
After a reboot no lirc0 created and no response to irw....
 
Have to do;
sudo rmmod lirc_mceusb
sudo modprobe lirc_mceusb (after this lirc0 is created)
sudo /etc/lirc restart
 
Then everything works again.
 
If someone has knowlegde or a hint to help with this problem, everything is greatly
appreciated.
 
Br, Zemy

---

### Post by Zemy on 2010-04-10
Anyone knowing about this problem?

Br, Zemy


> **Zemy said:**
> Hi all,
 
I have faced a problem with using lirc 0.8.6 on Ubuntu910.
/dev/lirc0 will not be created on reboot. Somehow it is related
module lirc_mceusb loading.
What I have done is basic Ubuntu910 desktop installation and after that
compiled Lirc 0.8.6 from source. I had to compile it to get my USB IR-receiver
to work. The device Realtek eHome IR receiver (0bda:0161) was not listed in lirc
source. Added the vendor information and the usb device information to lirc_mceusb.c
source file. After that compiled the lirc and installed. Everything good so far.
Then commands;
sudo modprobe lirc_mceusb
sudo /etc/lirc restart
 
lirc0 is created to /dev/ and everything works ok, response is right to irw.
 
After a reboot no lirc0 created and no response to irw....
 
Have to do;
sudo rmmod lirc_mceusb
sudo modprobe lirc_mceusb (after this lirc0 is created)
sudo /etc/lirc restart
 
Then everything works again.
 
If someone has knowlegde or a hint to help with this problem, everything is greatly
appreciated.
 
Br, Zemy

---

