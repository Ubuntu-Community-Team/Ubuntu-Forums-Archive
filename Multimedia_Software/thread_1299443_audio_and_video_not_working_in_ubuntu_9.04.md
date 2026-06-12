---
title: "audio and video not working in ubuntu 9.04"
date: 2009-10-23
forum: Multimedia Software
---

### Post by shibinjohn on 2009-10-23
hi 
i am not able to install vlc or any other multimedia handling softwares. when i searched vlc in the synaptic package manager it found no matches. When i typed the command 
sudo apt-get install vlc vlc plugin-esd the result was
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
akhil@akhil-laptop:~$ 

how can it be soved. My laptop is Compaq CQ40. How can i download vlc or any other software... please help.. thanks in advance..

---

### Post by jbrown96 on 2009-10-23
You need to activate the restricted software repositories. In Synaptic, there is a repository option in one of the menu. I believe on the first tab you can select your repositories. Make sure all of them are selected (multiverse, universe, etc.). Click ok, then reload your package info. Now you can find vlc and ubuntu-restricted-extras

---

