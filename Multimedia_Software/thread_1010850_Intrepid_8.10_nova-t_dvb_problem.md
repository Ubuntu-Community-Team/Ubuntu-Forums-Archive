---
title: "Intrepid 8.10 nova-t dvb problem"
date: 2008-12-14
forum: Multimedia Software
---

### Post by AndrewWalker on 2008-12-14
I've been using a Hauppauge WinTV Nova-T DVB terrestrial card for ages on Hardy with MythTV but due to a hard drive problem I need to reinstall. I wanted to use Mythbuntu but for some reason it no longer works correctly with Intrepid. It did work previously with Intrepid after an upgrade from Hardy but not on a clean install. Also, Nova-T no longer exists as an option in the lirc package, it seems to have been replaced with Nova-T 500 which is a different card.
Is anyone else experiencing problems with this card? It used to run out of the box, and does anyone know which lirc driver I need to select now it's specific one has vanished?

---

### Post by watkin5 on 2008-12-15
What's do you get in a terminal from
dmesg | grep dvb

?

---

### Post by AndrewWalker on 2008-12-16
I ran an update and there was an updated kernel and that seems to have fixed the tv side of things. Now it's just lirc that is screwed.
Here's the dmesg info

mythtvuser@mythtvbox:~$ dmesg | grep dvb
[   13.325115] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   13.325119] cx88/2: registering cx8802 driver, type: dvb access: shared
mythtvuser@mythtvbox:~$

Here's the lirc info

mythtvuser@mythtvbox:~$ dmesg | grep lirc
[   49.541954] lirc_dev: IR Remote Control driver registered, major 61
mythtvuser@mythtvbox:~$

but no lirc0 device exists in /dev and I still don't know which is the correct lirc driver for this card. I tried irw and get no response, just a carriage return in the console.

---

### Post by watkin5 on 2008-12-17
Not all tv cards use lirc device driver.
See [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI#LIRC]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI#LIRC").

P.S. I've a different device, so I'm not alot of help.

---

