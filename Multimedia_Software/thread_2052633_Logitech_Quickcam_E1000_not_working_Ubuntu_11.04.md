---
title: "Logitech Quickcam E1000 not working? Ubuntu 11.04"
date: 2012-09-03
forum: Multimedia Software
---

### Post by pmanley on 2012-09-03
I have just installed Ububtu Linux 11.04 om my new PC (Dell Inspiron 620 5.2GHZ). The camera does not seem to be working. I am new to this version of Linux and can't see where to look to see if the camera is visible to the system. Also I can not see where to get the drivers. There is some mention of drivers in other forums but no links to the files. Also I am a novice user, some of the suggested solutions seemed too technical for me. Is there and easy way to fix this or do I need to buy another camera? Is so what should I buy so that it will plug in and work without any hassle? Thanks for any help.

---

### Post by cortman on 2012-09-03
> **pmanley said:**
> I have just installed Ububtu Linux 11.04 om my new PC (Dell Inspiron 620 5.2GHZ). The camera does not seem to be working. I am new to this version of Linux and can't see where to look to see if the camera is visible to the system. Also I can not see where to get the drivers. There is some mention of drivers in other forums but no links to the files. Also I am a novice user, some of the suggested solutions seemed too technical for me. Is there and easy way to fix this or do I need to buy another camera? Is so what should I buy so that it will plug in and work without any hassle? Thanks for any help.

Although Cheese has its share of bugs, it usually works with most webcams- have you tried installing/using it?

```
sudo apt-get install cheese
```

---

### Post by pmanley on 2012-09-03
I installes Chese using the software centre. It did not seem to work.

---

### Post by cortman on 2012-09-03
> **pmanley said:**
> I installes Chese using the software centre. It did not seem to work.

Then I would suggest a look at [this page]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech").

---

### Post by pmanley on 2012-09-04
OK I looked at that page but could not see anything suitable. Perhaps I am missing the important thing on there, I don't know. I have installed Ubuntu Linux 12.04 and Cheese to test the camera. Still not seeing the camera. Any ideas?

---

### Post by pmanley on 2012-09-04
I have found a project called GSPCA and I have downloaded a file called 
**[gspcav1-20071224.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz")**

Now how do Install that? I am sorry if this seems a bit obvious to others out there.

---

### Post by pmanley on 2012-09-05
I also found these files on the web which claim to solve the problem:

qc-usb-0.6.6.tar.gz
qcamvc-1.0.11.tar.gz

However, I don't know what to do with these files to use them. I understand that they are file compressed files that I can extract, but where do I put them and what do I need to do to use them? I am a Linux novice, so please keep any instructions clear and simple. Assume I know very little about how to run stuff at the command prompt. Thanks.

---

### Post by pmanley on 2012-09-09
I have tried to extract and compile all these. But I get errors with each on. I'm not able to extract them in /usr/src as instructed as I don't have the permission to do that. How do I set the permission to allow me to extract them in the correct place?

---

### Post by pmanley on 2012-09-13
OK I give up. I ave now tried to install four different drivers that I'm told would solve my problem.  I am now convinced that the solution is to buy a webcam that will work easily with 12.04 Ubuntu. Which webcams are supported by this system? If you have a webcam that works on 12.04 without any setup please tell me about it. Thanks.

---

