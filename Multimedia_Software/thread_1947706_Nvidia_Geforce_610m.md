---
title: "Nvidia Geforce 610m"
date: 2012-03-27
forum: Multimedia Software
---

### Post by yashie on 2012-03-27
Hi all,
 
I have got a new Asus K53sd laptop. It has Nvidia Geforce610m Graphic card.
I have installed the ubuntu 11.04 and tried to install the additional drivers for the same.
I got some error while configuring. It says that Nvidia Graphic card cannot be used because of settings in x11.
I updated my laptop and rebooted it.
 
The system HAngs while Booting.
It stops near the  " Checking the battery   [ok] "
 
I came to know that this happens because of Graphic card installation probelms.
 
What should I do to resolve this issue.
 
Regards.

---

### Post by yashie on 2012-03-27
I have followed the below link to resolve my issue.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But, after activating graphic card by using nvidia-config and rebooting,
The system hangs. 

Please help me with a solution.

Thanks in andvance.

---

### Post by mörgæs on 2012-03-27
Moved to the multimedia forum.

---

### Post by Yellow Pasque on 2012-03-27
You have an nvidia Optimus (hybrid graphics) setup. You need to remove the nvidia driver and use bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by jaithehulk on 2012-04-12
Hi can u tell me what does bumblebee do exactly? I have the same Asus Laptop. I have installed Ubuntu 11.10. I need to install something for the nvidia 610m graphics card.

---

