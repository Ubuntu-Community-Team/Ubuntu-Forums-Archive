---
title: "Poor Display"
date: 2008-10-03
forum: Multimedia Software
---

### Post by VarunKrishna on 2008-10-03
Hello Friend,

I am using Windows XP and Ubuntu 8.04.1 LTS Desktop Edition. I was successful in Installing Ubuntu but I found that there is no graphics driver for display which resulted in some lines which are diagonal across the screen. My mother Name is Asus and mother board version is P5VD2-VM SE. I want the help of fellow Ubuntu users to help to get rid of it. 

Bye,

Varun

---

### Post by overdrank on 2008-10-03
Hi and welcome, you may use the command ```
lspci
``` in the terminal and this will identify your hardware. The terminal is located under applications, accessories. Then look for VGA and this is your graphics chipset.  You may also use the command ```
gksu displayconfig-gtk
``` and adjust your graphics there.

---

