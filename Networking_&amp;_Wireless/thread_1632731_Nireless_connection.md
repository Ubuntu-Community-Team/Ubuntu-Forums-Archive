---
title: "Nireless connection"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by hpng on 2010-11-28
I am a Linux newbie.
Just installed Wubi and ubuntu 10.04 LTS onto Win 7 HP laptop.
So I have a dual boot. and Ubuntu resides in a shared partition with windows files and folder.

I cannot get Ubuntu to see wirelesss hardware at all.
However, when I plug the ethernet cable to the laptop,
there is network connection, but somewhat slower than under windows 7
.
I also look "Network Connection" ( icon at top right screen),
there is no display of any wireless data under the Wireless tab.

How do I setup Ubuntu to see the wireless device?
With Win7, it detects the wireles device automatically, so how 
can I do that for Ubuntu?.

Thanks,
HP

---

### Post by uncaspi on 2010-11-28
Probably a wireless driver problem. You have to type a few commands when you have opened a terminal. First post the content of 

sudo lspci -nn

so we can find out which drivers you need.;)

---

### Post by hpng on 2010-11-28
Thanks. I did solve the problem. In Gnome, I select System>Administration>hardware driver menus. Then it search for drivers of hardware in laptop. It  indicated there is no driver for my Broadcom wireless device, amd ask me to download it.  So is good for now.  I am using Gnome,and has no clue on how to use script. By the way, where can I download stuff related to scripting for Ubuntu/Linux? I also like to know were to download documentation stuff for Linux OS API's for programming.  I am very new to Linux. Need to learn how it works from OS side.  Thanks.

---

### Post by uncaspi on 2010-11-28
Remember to put [SOLVED] on the thread. Google is you best friend. Thats the way I learned it. For C++ programming there are several good books.
I used "Problem Solving, Abstraction , and Design Using C++" Authors
Frank L.Friedman and Elliot B. Koffman. ISBN 0-201-52649-2

---

