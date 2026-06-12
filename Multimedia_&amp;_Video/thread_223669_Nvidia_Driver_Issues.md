---
title: "Nvidia Driver Issues"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by treak007 on 2006-07-26
I recently tried to install nvidia drivers (both the ones from the repos and from nvidia's site) onto my ubuntu x86 desktop. Everytime I attempt to do so, I get an error about my xorg.conf file being configured. When I attempt to manually edit my xorg.conf file graphics driver from "nv" to "nvidia" my xorg server wont start anymore .I  got the drivers to work back when I had x64 ubuntu installed, I don't know why they dont work in x86.

Btw- I already tried following the guide here : [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
it resultsed in a blank screen when attempting to load the xorg server

---

### Post by tseliot on 2006-07-26
1) Which method of the guide did you use?

2) Did you get any error during the installation of the driver?

3) can you try point 4 of the Problems Section?

4) can you post the model of your graphic card?

---

### Post by treak007 on 2006-07-26
well first, I would like to thank you for your quick response. 

1) I attempted method 1 only because I need the restricted Modules for my atheros wireless device

2) No errors following your method, It just booted into a black screen b/c xorg.serv wouldnt start, when I followed the faq's instructions, I recieved an error about my xorg.conf file being written.

3)I dont have any control over my mouse 

4) Bfg agp 8x 256 geForce 6200 oc

---

### Post by tseliot on 2006-07-27
> **treak007 said:**
> 3)I dont have any control over my mouse
You can use your keyboard

---

### Post by treak007 on 2006-07-27
Ok. I tried that and this time it worked. Thanks so much for your help and sorry for wasting your time on such a stupid question that was anwered in the problems section.

---

