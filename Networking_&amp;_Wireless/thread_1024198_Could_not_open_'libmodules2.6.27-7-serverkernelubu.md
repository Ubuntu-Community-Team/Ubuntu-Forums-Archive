---
title: "Could not open '/lib/modules/2.6.27-7-server/kernel/ubuntu/ndiswrapper/ndiswrapper.ko"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Nicsoft on 2008-12-28
Hello, I am a total newbie to this with Wireless and almost as much newbie on Linux. I have searched forums for two days now and getting very tired... Nothing has helped. :( When compiling things the header files cannot be found even though I have installed them. It's quite obvious reading the error messages when compiling that the header files are not installed where the the compiling process is looking. But that's not what I am wondering about here (unless some kind person want to help me out there as well...). 

I am using 8.10 server version of Ubuntu. 

I am having a WMP54G v4.1 card using Ralink rt61 chipset. I think I have to use the ndiswrapper to get it to work. I tried using the rt61 driver directly from Ralink but didn't succeed. (But I am most willing to listen if anyone has an idea) 

I am using these instructions for ndiswrapper: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

When I come to this instruction:  ```
sudo modprobe ndiswrapper
``` I get the following output: ```

FATAL: Could not open '/lib/modules/2.6.27-7-server/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
``` 

:confused:

What is the problem?

Thank you in advance!

Regards,
Niklas

---

### Post by Nicsoft on 2008-12-29
Hello again,

This is what I did. I re-installed Ubuntu 8.10. Mainly because I wanted to start from a clean installation but also because I think I did install the acutal card after I installed Ubuntu before. Just to make sure I didn't do exactly in the same way again I installed the desktop version instead of the server version. 

I used the Network Manager Applet in the top-left to configure my network and unplugged the fixed cable. Voiala, not it works. 

So, I actually have no idea what all problems was, but most likely I messed up to much before and I didn't use the NM Applet before things were already destroyed. 

Thanks for your time anyway. 

Best Regards,
Niklas

---

