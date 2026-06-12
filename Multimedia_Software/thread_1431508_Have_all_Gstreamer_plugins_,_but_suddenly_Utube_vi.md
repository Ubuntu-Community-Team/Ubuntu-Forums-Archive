---
title: "Have all Gstreamer plugins , but suddenly Utube videos dont play"
date: 2010-03-16
forum: Multimedia Software
---

### Post by typos1 on 2010-03-16
Cant view Youtube videos and some animated sites (such as AlfaRomeo.com) , have been able to before.

Anyone know why not?

Recently uninstallled all Gstreamer plugins to try and sort a problem, but re-installed them after and everything else seems to work ok.

---

### Post by typos1 on 2010-03-17
Any ideas anyone?

---

### Post by J_Stanton on 2010-03-17
youtube depends on flash, not gstreamer plugins. completely remove flash then do: sudo apt-get clean && sudo apt-get autoremove then reinstall flash.

---

### Post by typos1 on 2010-03-17
Ah, oops, sorry-I should know the difference-I had had months and months where I couldnt view any Flash stuff at all (used to be a bad prob with 64 bit) and had to keep messin about with it to try and get it to work. I ll try that.

---

### Post by typos1 on 2010-03-18
Doesnt work-says cant find package. 

Downloaded latest version and when I click on open with gdebi or sudo, I hear processor noises, but nothing happens. 

In system monitor neither sudo or gdebi are shown as running.

I havent touched it so dont know why it doesnt work suddenly.

---

### Post by typos1 on 2010-03-18
Did a re start and does work now!!

---

