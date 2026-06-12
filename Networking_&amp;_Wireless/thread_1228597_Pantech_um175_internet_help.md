---
title: "Pantech um175 internet help"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by cquigley on 2009-08-01
Hi Everyone-
 
  I am a noob to linux and running ubuntu jaunty.
 
 
I have a Panech um175 which is a usb wireless internet from Verizon. I cannot figure out how to configure it for jaunty.
 
Also, my wireless card is detected in the terminal, but NetworkManager does not see it. How do I get this to work.
 
Any help is greatly appreciated.
 
thx,
 cquigley

---

### Post by jprogers5181 on 2009-09-30
I am a Ubuntu (Linux) noob also. I searched for several days trying to find help with this same problem and finally found a solution. However, I did not save the solution URL (sorry). Essentially, I had to initialize the Verizon account using a Windows operating system. I installed the VZAccess Manager software on the Windows machine and followed all the prompts. Once the UM175 was communicating as advertised, I plugged it into my Ubuntu 9.04 machine (freshly updated!!!) and the modem was recognized and I connected immediately. On previous install attempts I did enter all the required information requested in the NetworkManager|Mobile Broadband tab. That may have been why it seemed like a seemless solution. After I got the Ubuntu machine communicating with the Internet I uninstalled the VZAccess Manager from the Windows machine and all is well. By the way, I tried installing the VZAccess Manager in a Windows VirtualBox, but could not get access to the USB port. I've read other forums that corraborate this problem so don't bother trying that route. Use a pure Windows machine or a Windows partition and it will hopefully get you connected quickly.

---

