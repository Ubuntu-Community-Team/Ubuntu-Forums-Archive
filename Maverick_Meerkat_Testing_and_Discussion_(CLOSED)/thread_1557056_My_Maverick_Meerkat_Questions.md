---
title: "My Maverick Meerkat Questions"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by c00lwaterz on 2010-08-20
Hi,

I want to ask some questions about maverick meerkat. I hope this will help me.

1. From Lucid experience in High temperature (the fan doesn't work), Will it work in maverick?(did they put solutions from the past issues?)
2. Will maverick meerkat solve the problem of high temp of GPU in Lucid?

By the way, I'm using Toshiba M900 and did not solved the issues of high temperature.

I am currently using windows vista to play safe on my laptop. I have tried many times ubuntu and ask help with people and look for solution but did not work. I hope it will be solve in future development.

Thanks

---

### Post by sharathcshekhar on 2010-08-20
Fan Problem mostly looks like an issue with BIOS. One thing you can try out is, add a CPU frequency scaling monitor to you panel and monitor your CPU frequency. If you observe your core is overheating, most likely the CPU will be clocking max speeds, you can reduce the speed and force it to under clock. You can also install sensorsd to monitor you core temperature, by giving the command "sensors" once sensorsd is installed.
This problem is unlikely to be solved in Maverick also. 
Also make sure modules like "k8temp" are inserted by seeing the output of lsmod.

Sharath

---

### Post by c00lwaterz on 2010-08-20
> **sharathcshekhar said:**
> Fan Problem mostly looks like an issue with BIOS. One thing you can try out is, add a CPU frequency scaling monitor to you panel and monitor your CPU frequency. If you observe your core is overheating, most likely the CPU will be clocking max speeds, you can reduce the speed and force it to under clock. You can also install sensorsd to monitor you core temperature, by giving the command "sensors" once sensorsd is installed.
This problem is unlikely to be solved in Maverick also. 
Also make sure modules like "k8temp" are inserted by seeing the output of lsmod.

Sharath

Hi sharath,

Thanks for the response. I have already tried sensors that i can see temperature, but the heat is really fast that it can't hold longer. When I use ubuntu for 5 to 10 minutes then the temperature goes high that my hands can't tolerate it. I have also tried bios update and some fixes but did not solve the problem. if meerkat won't solve the problem then I need to wait again.

Thanks for the info so I won't waste time downloading and installing again and again. I hope in future there are solution for the temperature (CPU, GPU) so I can use ubuntu :p

---

### Post by dino99 on 2010-08-20
> **c00lwaterz said:**
> Hi sharath,

Thanks for the response. I have already tried sensors that i can see temperature, but the heat is really fast that it can't hold longer. When I use ubuntu for 5 to 10 minutes then the temperature goes high that my hands can't tolerate it. I have also tried bios update and some fixes but did not solve the problem. if meerkat won't solve the problem then I need to wait again.

Thanks for the info so I won't waste time downloading and installing again and again. I hope in future there are solution for the temperature (CPU, GPU) so I can use ubuntu :p

is these high temps are only with ubuntu ? First be sure of your hardware and its settings: are fans well plugged and working, are your hardware (motherboard and/or graphic card overclocked, is your box dusty or cant easy breath (to much stuff around/on/to close of other things)?

most of the sensors are directly managed by the kernel (sensors-detect often get the system confused if you add what it find), but for a better temperature system control, everyone is waiting the future 2.6.36 kernel as huge efforts is made to resolve the numerous temp issues, mostly with laptops.

---

### Post by c00lwaterz on 2010-08-21
> **dino99 said:**
> is these high temps are only with ubuntu ? First be sure of your hardware and its settings: are fans well plugged and working, are your hardware (motherboard and/or graphic card overclocked, is your box dusty or cant easy breath (to much stuff around/on/to close of other things)?

most of the sensors are directly managed by the kernel (sensors-detect often get the system confused if you add what it find), but for a better temperature system control, everyone is waiting the future 2.6.36 kernel as huge efforts is made to resolve the numerous temp issues, mostly with laptops.

Hi dino99,

Thanks for the response.
The problem occurs when using linux. I have tried linux mint, ubuntu, and others. I also tried the update in kernel the fixes on what other people told me but no luck yet. Right now, I use pre-installed windows vista. The fan is not working on linux when the temperature goes up (linux). I suspect it has to do with GPU or CPU. my processor is 2.4 core 2 duo and my GPU is ATI radeon.

In my case, nothing to hurry to install linux. I can wait to get suitable linux for my laptop.

---

### Post by philinux on 2010-08-21
> **c00lwaterz said:**
> Hi dino99,

Thanks for the response.
The problem occurs when using linux. I have tried linux mint, ubuntu, and others. I also tried the update in kernel the fixes on what other people told me but no luck yet. Right now, I use pre-installed windows vista. The fan is not working on linux when the temperature goes up (linux). I suspect it has to do with GPU or CPU. my processor is 2.4 core 2 duo and my GPU is ATI radeon.

In my case, nothing to hurry to install linux. I can wait to get suitable linux for my laptop.

This might help. I don't have a laptop myself. Doesn't seem an ideal solution though.

[http://ubuntuforums.org/showthread.php?t=1469475&page=2](http://ubuntuforums.org/showthread.php?t=1469475&page=2)

---

### Post by c00lwaterz on 2010-08-22
> **philinux said:**
> This might help. I don't have a laptop myself. Doesn't seem an ideal solution though.

[http://ubuntuforums.org/showthread.php?t=1469475&page=2](http://ubuntuforums.org/showthread.php?t=1469475&page=2)

Hi philinux,

Thanks for the response.

I saw the workaround using the kernel (karmic) but I have tried some workaround of kernel already but no luck also and I also try koala karmic but also gets high temperature.

My laptop fan doesn't work well with ubuntu, so I suspect my processor and GPU gets hot without air moving inside.

---

