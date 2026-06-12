---
title: "hi iam new on linux (silvercrest wc2130 webcam)"
date: 2009-01-06
forum: Multimedia Software
---

### Post by pangoul on 2009-01-06
hi to all and thank for all the forum information.
i have the ubuntu 8.10 and i cant work my web camera silvercrest wc2130.
can anyone help me??
thanks

---

### Post by xc3RnbFO8P on 2009-01-06
First do **lsusb** in Terminal and show the output.

---

### Post by pangoul on 2009-01-06
> **Ringi said:**
> First do **lsusb** in Terminal and show the output.





panos@ubuntu:~$ lsusb
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62b3 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


thanks

---

### Post by xc3RnbFO8P on 2009-01-06
Read this:
[http://ubuntuforums.org/archive/index.php/t-921153.html]("http://ubuntuforums.org/archive/index.php/t-921153.html")

---

### Post by xc3RnbFO8P on 2009-01-06
>  Originally Posted by Ringi  View Post
Delete
(sorry this was a double post #4)

---

### Post by pangoul on 2009-01-06
> **Ringi said:**
> Delete

thanks but dont help me

---

### Post by Ghost_face on 2010-12-26
Hello all. I have this problem too. Who can help me? This my lsusb:

===============================================
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0c45:62b3 Microdia PC Camera with Microphone (SN9C202 + OV9655)
Bus 001 Device 006: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 001 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

===============================================

---

### Post by no2498 on 2010-12-27
Ghost_face

click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1


i hope it comes on for you if it does
you need a program like cheese to use it in

---

### Post by Ghost_face on 2010-12-30
i can't search this:
go down the list to multimedia systems selector, start it click video

i use ubuntu 10.04 lts

---

### Post by no2498 on 2010-12-30
top of your screen
you can do it now
applications, places, system click system

---

### Post by Ghost_face on 2011-01-18
> **no2498 said:**
> top of your screen
you can do it now
applications, places, system click system

i don't have this menu

---

