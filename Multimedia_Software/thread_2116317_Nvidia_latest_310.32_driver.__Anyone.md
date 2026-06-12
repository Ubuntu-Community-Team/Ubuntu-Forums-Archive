---
title: "Nvidia latest 310.32 driver.  Anyone?"
date: 2013-02-15
forum: Multimedia Software
---

### Post by homeeey on 2013-02-15
I'm on a mission to get this installed. Not sure why. So far no luck, but I'm learning a lot.
 
I was just wondering if anyone has successfully installed this driver? 
 
I'm running 12.04 (mythbuntu) and a GT630 card.
 
So far no dice. 304 drivers work, but I'm stubborn.
 
Thanks for any help.

---

### Post by MAFoElffen on 2013-02-15
While testing dev... nVidia 310.32 had problems with Ubuntu and Debian. Newer nVidia 313.09 worked fine.

Try that version instead.

---

### Post by homeeey on 2013-02-15
QUOTE=MAFoElffen;12511555]While testing dev... nVidia 310.32 had problems with Ubuntu and Debian. Newer nVidia 313.09 worked fine.
 
Try that version instead.[/QUOTE]
 
Go figure, and it's their certified driver.  I think I'm going to go back to 304, it seemed to work pretty good.  We'll see how it goes, currently I'm stuck in terminal mode, wth 20x10 resolution (well might be exagerating a little). :)   
 
I've spent a good amount of time reading guides and and such, you name comes up a lot, just want to say thanks for all the help, I was just going through the guide in your signature.

---

### Post by Frogs Hair on 2013-02-15
I found the 304 experimental driver to work better than Nvidia current which is tested. :confused: I do have 3.10.14 available in software sources but haven't tried it since October.

---

### Post by homeeey on 2013-02-15
> **Frogs Hair said:**
> I found the 304 experimental driver to work better than Nvidia current which is tested. :confused: I do have 3.10.14 available in software sources but haven't tried it since October.
 
3.10.14 worked ok once in the gui, but the splash (bootup) screen and shutdown screen were both pretty funky looking.

---

### Post by Frogs Hair on 2013-02-15
I had text during shut down with 3.10 but there have been a few kernel updates since October,so it may be worth trying again if needed.

---

### Post by MAFoElffen on 2013-02-15
> **homeeey said:**
> QUOTE=MAFoElffen;12511555]While testing dev... nVidia 310.32 had problems with Ubuntu and Debian. Newer nVidia 313.09 worked fine.
 
Try that version instead.
 
Go figure, and it's their certified driver.  I think I'm going to go back to 304, it seemed to work pretty good.  We'll see how it goes, currently I'm stuck in terminal mode, wth 20x10 resolution (well might be exagerating a little). :)   
 
I've spent a good amount of time reading guides and and such, you name comes up a lot, just want to say thanks for all the help, I was just going through the guide in your signature.[/QUOTE]
You are very welcome. I am in the middle of rewriting and updating "everything" to replace that thread.

Frustratingly, that thread has been there long enough that I cannot update the first three posts any longer. So not all the links in post #2 point to what is current in that thread.

I have a new plan to remedy that...

---

### Post by QwUo173Hy on 2013-02-19
I'm going to try 313.09 too since I lost 3D acceleration with 310 driver. Is it possible that my card isn't supported (7600 GT)?

---

### Post by Bucky Ball on 2013-02-19
*Thread moved to **Multimedia & Video**.*

---

### Post by QwUo173Hy on 2013-02-19
> **TenLeftFingers said:**
> I'm going to try 313.09 too since I lost 3D acceleration with 310 driver. Is it possible that my card isn't supported (7600 GT)?
Found the supported cards list. I'm out of luck. Here are the supported cards for this driver:
**GeForce 600 series:**
GTX 690, GTX 680, GTX 670, GTX 660 Ti, GTX 660, GTX 650 Ti, GTX 650, GT 645, GT 640, GT 630, GT 620, GT 610, 605

**GeForce 600M series:**
GTX  680M, GTX 675MX, GTX 675M, GTX 670MX, GTX 670M, GTX 660M, GT 650M, GT  645M, GT 640M LE, GT 640M, GT 635M, GT 630M, GT 620M, G610M

**GeForce 500 series:**
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 560 SE, GTX 560, GTX 555, GTX 550 Ti, GT 545, GT 530, GT 520, 510

**GeForce 500M series:**
GTX 580M, GTX 570M, GTX 560M, GT 555M, GT 550M, GT 540M, GT 525M, GT 520MX, GT 520M

**GeForce 400 series:**
GTX 480, GTX 470, GTX 465, GTX 460 v2, GTX 460 SE v2, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, GT 415, 405

**GeForce 400M series:**
GTX 485M, GTX 480M, GTX 470M, GTX 460M, GT 445M, GT 435M, GT 425M, GT 420M, GT 415M, 410M

**GeForce 300 series:**
GT 340, GT 330, GT 320, 315, 310

**GeForce 300M series:**
GTS 360M, GTS 350M, GT 335M, GT 330M, GT 325M, GT 320M, 320M, 315M, 310M, 305M

**GeForce 200 series:**
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 210, 205

**GeForce 200M series:**
GTX 285M, GTX 280M, GTX 260M, GTS 260M, GTS 250M, GT 240M, GT 230M, GT 220M, G210M

**GeForce 100 series:**
GT 140, GT 130, GT 120, G 100

**GeForce 100M series:**
GTS 160M, GTS 150M, GT 130M, GT 120M, G 110M, G 105M, G 103M, G 102M

**GeForce 9 series:**
9800  GX2, 9800 GTX+, 9800 GTX/GTX+, 9800 GT, 9650 S, 9600 GT, 9600 GSO 512,  9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 SE, 9300 GS,  9300 GE, 9300 / nForce 730i, 9300, 9200, 9100

**GeForce 9M series:**
9800M  GTX, 9800M GTS, 9800M GT, 9800M GS, 9700M GTS, 9700M GT, 9650M GT,  9650M GS, 9600M GT, 9600M GS, 9500M GS, 9500M G, 9400M G, 9400M, 9300M  GS, 9300M G, 9200M GS, 9100M G

**GeForce 8 series:**
8800  Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS,  8600 GT, 8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200,  8100 / nForce 720a

**GeForce 8M series:**
8800M GTX, 8800M GTS, 8700M GT, 8600M GT, 8600M GS, 8400M GT, 8400M GS, 8400M G, 8200M G, 8200M

**NVS Series:**
NVS 510, NVS 310, NVS 300

**Quadro series:**
K5000, 7000, 6000, 600, 5000, 410, 4000, 400, 2000D, 2000

**Quadro FX series:**
FX  5800, FX 580, FX 570, FX 5600, FX 4800, FX 4700 X2, FX 4600, FX 380 LP,  FX 3800, FX 380, FX 370 Low Profile, FX 3700, FX 370, FX 3400/4400, FX  1800, FX 1700, CX

**Quadro Notebook series:**
K5000M, K4000M, K3000M, K2000M, K1000M, 5010M, 5000M, 4000M, 3000M, 2000M, 1000M

**Quadro FX Notebook series:**
FX  880M, FX 770M, FX 570M, FX 380M, FX 3800M, FX 370M, FX 3700M, FX 360M,  FX 3600M, FX 2800M, FX 2700M, FX 1800M, FX 1700M, FX 1600M

**Quadro NVS series:**
NVS 450, NVS 420, NVS 295, NVS 290

**Quadro NVS Notebook series:**
NVS 5400M, NVS 5200M, NVS 4200M, NVS 320M, NVS 160M, NVS 150M, NVS 140M, NVS 135M, NVS 130M

**Quadro Plex series:**
Model IV, Model II, D Series, 7000

**Quadro Sync series:**
Sync, G-Sync II

**Quadro SDI series:**
Quadro SDI

**ION series:**
ION LE, ION

**C-Class Processors:**
Tesla C870, Tesla C2075, Tesla C2070, Tesla C2050, Tesla C1060, T10 Processor

**M-Class Processors:**
Tesla M2090, Tesla M2075, Tesla M2070-Q, Tesla M2070, Tesla M2050, Tesla M1060

**X-Class Processors:**
Tesla X2090

**K-Series Processors:**
Tesla K20m, Tesla K20c, Tesla K10

**NVS Notebook Series:**
NVS 5100M, NVS 3100M, NVS 2100M

---

