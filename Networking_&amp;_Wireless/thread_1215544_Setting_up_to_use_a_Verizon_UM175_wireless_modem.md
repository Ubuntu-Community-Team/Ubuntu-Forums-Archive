---
title: "Setting up to use a Verizon UM175 wireless modem?"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by whipsaw on 2009-07-17
Hi,

I'm a new user (long time Mac user) and am attempting to set up my Dell mini 10 so that I can use a Verizon UM175 wireless modem. The Verizon CDs are for use with Windows and Mac OS. 

Is there some simple way to do this?

Thanks in advance.

---

### Post by jprogers5181 on 2009-09-30
I searched for several days trying to find help with this same problem and finally found a solution. However, I did not save the solution URL (sorry). Essentially, I had to initialize the Verizon account using a Windows operating system. I installed the VZAccess Manager software on the Windows machine and followed all the prompts. Once the UM175 was communicating as advertised, I plugged it into my Ubuntu 9.04 machine (freshly updated!!!) and the modem was recognized and I connected immediately. On previous install attempts I did enter all the required information requested in the NetworkManager|Mobile Broadband tab. That may have been why it seemed like a seemless solution. After I got the Ubuntu machine communicating with the Internet I uninstalled the VZAccess Manager from the Windows machine and all is well. By the way, I tried installing the VZAccess Manager in a Windows VirtualBox, but could not get access to the USB port. I've read other forums that corraborate this problem so don't bother trying that route. Use a pure Windows machine or a Windows partition and it will hopefully get you connected quickly.

---

