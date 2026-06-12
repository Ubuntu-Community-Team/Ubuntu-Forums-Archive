---
title: "GTX 560 + Ubuntu 13.04"
date: 2013-09-25
forum: Multimedia Software
---

### Post by Matas_Demarchi on 2013-09-25
HI! I'm not an english speaker, so sorry if I don't write well.
I have a problem with my nVidia GeForce GTX 560 and my Ubuntu 13.04. When I leave my PC on for six or eight hours, I notice that my PC shows artifacts (and sometimes the video goes out) and the SO crashes, so I have to reboot my PC. (Find image attached.)

My current driver is "NVIDIA binary Xorg driver, kernel module and VDPAU library desde nvidia-325 (open source)"
And I don't understand why it says "open source" if it is the nVidia driver and not the nouveau driver.

I tried with this other drivers and the problem is the same (sorry, it is in spanish):
"Controlador Xorg NVIDIA binario, módulo del núcleo y biblioteca VDPAU desde nvidia 313-updates (privative)"
"Controlador Xorg NVIDIA binario, módulo del núcleo y biblioteca VDPAU desde nvidia 310-updates (privative)"
"NVIDIA binary Xorg driver, kernel module and VDPAU library desde nvidia-304 (open source)"
"Controlador Xorg NVIDIA binario, módulo del núcleo y biblioteca VDPAU desde nvidia 304-updates (privative)"

I know that the problem is not from the GPU because in Windows it works fine, so can you help me to find the solution?

---

### Post by Matas_Demarchi on 2013-09-26
Any help? It's very annoying and I didn't find any solution in spanish forums.

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Multimedia & Video**.*

Welcome. Removed the large image from the body of your post and  attached it instead. Please attach large images rather than insert them in the body of your post. Also, please wait 24 hours before bumping the thread. If no-one has responded, they have nothing to add. There is, of course, nothing preventing you from keeping the community updated by adding any new developments if you try something to fix the problem. 

Wondering if perhaps this is hardware related and nothing to do with drivers. Sure a strange one.

Good luck. ;)

---

### Post by Matas_Demarchi on 2013-09-26
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

Welcome. Removed the large image from the body of your post and  attached it instead. Please attach large images rather than insert them in the body of your post. Also, please wait 24 hours before bumping the thread. If no-one has responded, they have nothing to add. There is, of course, nothing preventing you from keeping the community updated by adding any new developments if you try something to fix the problem. 

Wondering if perhaps this is hardware related and nothing to do with drivers. Sure a strange one.

Good luck. ;)

Thanks. It's my first english forum, so I don't understand it very well.

The problem doesn't happen in Windows, so I think it is not a problem with the graphics card. I have tried with all of those drivers, but I now I will try with the "nouveau" driver.

---

### Post by Bucky Ball on 2013-09-26
> **Matas_Demarchi said:**
> I have tried with all of those drivers, but I now I will try with the "nouveau" driver.

Good plan. ;)

---

### Post by Matas_Demarchi on 2013-09-27
I am trying with the nouveau driver, I haven't tried the 6 hours yet, but now with this driver the image is too blurry and it hurts my eyes. I don't know why.

---

### Post by Yellow Pasque on 2013-09-27
> When I leave my PC on for six or eight hours, I notice that my PC shows artifacts (and sometimes the video goes out) and the SO crashes, so I have to reboot my PC.
Are you monitoring the temperature (of the CPU and GPU) when it does this?

---

### Post by Matas_Demarchi on 2013-09-27
Psensor says aprox. between 35º-40ª of temperature in CPU and GPU. And it is the same everytime.

---

### Post by Matas_Demarchi on 2013-09-28
Well, I tried with the nouveau driver and it seems to work fine, but I don't know why with this driver the image is too blurry and it hurt my eyes. And I don't know if I have the same 3D acceleration than I had with the nVidia driver. I want to use the nVidia's but they crash when I put them on for six or seven hours.

---

### Post by Matas_Demarchi on 2013-10-07
Well, I found the origin of the problem, but I didn't find a solution, this is what the Ubuntu Crash Report says:



ExecutablePath: /usr/bin/Xorg

Package: xserver-xorg-core 2:1.13.4~git20130508+server~1.13-branch. 10c42f57-0ubuntu0ricotz~raring [origin: LP-PPA-xorg-edgers]

ProblemType: Crash

Title: Xorg crashed with SIGABRT

.proc.driver.nvidia.gpus.0: Error: [Errno 21] Es un directorio: ' /proc/driver/nvidia/gpus/0'




I copied it by hand, so I don't have time to copy more, Where I can find it to copy and paste?

---

### Post by Matas_Demarchi on 2013-10-12
I have that problem everyday, but when I search it in Google, it leads me to bug reports in the Launchpad forums, but i didn't find a solution.

---

### Post by Matas_Demarchi on 2013-10-22
Today I had the same problem but now it says:

Xorg crashed with SIGSEGV in _Unwind_Backtrace()

When I search this crash in Google, it leads me to bug reports in the Launchpad forums again.

---

### Post by dannyboy79 on 2013-10-22
i would suggest NOT using the xorg-edgers ppa. go to tty1 and stop your x-server, remove that ppa and install the latest stable nvidia proprietary driver from their website. i think its 319.60 OR even the newest BETA 331.17. Good luck

---

### Post by Matas_Demarchi on 2013-11-06
Well, I decided to format and reinstall Ubuntu (now with 13.10) and the problem persist, it only happens with all the privative drivers from nVidia. Here is another example, but the last time with the artifacts misteriously a nvidia logo appeared.

Here is the first lines of the crash report of that misterious logo:

Executable Path:
/usr/bin/Xorg

Package:
xserver-xorg-core 2:1.14.3-3ubuntu2

Problem Type:
Crash

Title:
Xorg crashed with SIGABRT

.proc.driver.nvidia.gpus.0:
Error: [Errno 21] Es un directorio: '/proc/driver/nvidia/gpus/0'

---

