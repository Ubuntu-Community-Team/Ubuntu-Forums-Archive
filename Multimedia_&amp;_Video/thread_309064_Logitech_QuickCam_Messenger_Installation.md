---
title: "Logitech QuickCam Messenger Installation"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by TurningJpnz on 2006-11-29
I'm new to Ubuntu and have been trying to get a Logitech Quickcam Messenger Webcam up and running with no luck. I've tried Quickcam2 and later found it to be incompatible with my particular Logitech webcam. 

My webcam is listed on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) as being compatible with spca5xx/LE drivers. I therefore tried the following installation instructions from another post:

------------
Edgy Eft 6.10

1) System- Administration- Software Sources
check Community maintaned (universe)


2) sudo apt-get install module-assistant
sudo module-assistant
PREPARE
SELECT
select module spca5xx
and
GET
BUILD
INSTALL

-------------------

I still can't get it to work. Can anyone offer me some advice?

---

### Post by frodon on 2006-11-29
Here is what i did to get my logitech webcam working :
```
sudo apt-get install module-assistant camstream
sudo m-a update,prepare,a-i spca5xx
```Then reboot

camstream is just a tool to test your webcam.

---

### Post by Neo40 on 2006-11-30
I have too a Quickcam Messenger. The problem I have is camstream does not work:

```
eric@ubuntu:~$ camstream 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

I have a similar error if I try to run camorama:
```
Could not connect to video device (/dev/video0). Please check your connection.
```

Any idea?
Thanks

---

