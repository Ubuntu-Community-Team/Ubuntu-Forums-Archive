---
title: "How to autodetect graphics card"
date: 2008-06-10
forum: Multimedia Software
---

### Post by RonakG on 2008-06-10
Hi,

I have installed ubuntu 8.04 on my Transcend 160 GB USB hard drive. So that I can carry my OS everywhere I go. It works fine on almost all laptops.

But the problem occurs when I try to boot from a desktop with 20" LCD screen. It always runs in low graphics mode even after I select the LCD model and resolution from drop down menu.

Pls reply if you have any solution or workaround for this issue.

Thanks,
Ronak

---

### Post by RonakG on 2008-06-10
Some more information. 

When I installed Hardy on the external harddrive, it was connected to my Lenovo T61 which has NVIDIA graphics card. I had opted for dual boot option and then reconfigured the MBR on windows and installed GRUB on external drive. I am very very new to Linux, so didn't know any other way to do this.

The desktop on which I am trying to boot from external drive has max resolution of 1600x1200 on Windows XP. But I am not able to chose more than 800x600 on Hardy.

Any help is appreciated.

Thanks,
Ronak

---

### Post by RonakG on 2008-06-11
anybody to help pls????

Or I have raised this question in wrong forum?

---

### Post by frankos44 on 2008-06-11
Problem could be that Ubuntu did not detect your monitor correctly during installation. Have you tried to re-detect?

System->Preferences->Screen Resolution

My previous PC used NVIDIA and from memory I downloaded the latest driver from the NVIDIA website when I had an issue with graphics.

---

### Post by RonakG on 2008-06-11
Thanks for the response.

Yes I have tried that. But it shows only 800x600 maximum resolution. May be it doesnt know that the desktop LCD and graphics driver combination supports more resolution than this. 

How do I make it aware about this?

---

### Post by frankos44 on 2008-06-11
One of my not so strong points is memory and I don't have a PC here with NVIDA so excuse me if I got this wrong.

$ sudo apt-get install nvidia-settings
$ sudo nvidia-settings

and go from there.

---

### Post by RonakG on 2008-06-11
Thanks for replying.

I think I have confused you here. 

The problem is with the desktop which has Intel in-built graphics card.

When I installed ubuntu on external drive, it was attached to a Laptop with NVIDIA graphics card. So whenever I boot, it expects (I believe) nvidia graphics card to be present. When it doesn't find that, it runs in low graphics mode. 


Thanks,
Ronak

---

### Post by frankos44 on 2008-06-11
OK no problem, which graphics card do you have?

---

