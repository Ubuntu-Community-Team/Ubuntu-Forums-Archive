---
title: "Question about Nvidia Drivers"
date: 2010-12-13
forum: Multimedia Software
---

### Post by Fordc307 on 2010-12-13
Hi there!
 
I have Zotac 9500GT DDR2 VGA card installed in my PC. I recently installed the Ubuntu 10.04 LTS on it. 
 
As you know when you first start a window will pop up telling you to install the additional diriver for your VGA or to choose the priority one.
 
Anyway I installed the latest driver from Nvidia.com Version: [SIZE=2]260.19.29 Certified[/SIZE]
 
[SIZE=2]The additional dirver window will give two options to activate:[/SIZE]
 
[SIZE=2]1. Nvidia Driver version 173[/SIZE]
[SIZE=2]2. Nvidia Driver - current (Recommended).[/SIZE]
 
[SIZE=2]So now I have 3 options the one I downloaded from Nvidia.com and other two givin by Ubuntu.[/SIZE]
 
[SIZE=2]my two questions are:[/SIZE]
 
[SIZE=2]1. what is the difference between these three drivers?[/SIZE]
[SIZE=2]2. Which one of them should I install that would work the best for me?[/SIZE]
 
[SIZE=2]I have AMD Athlon x64 C2D - 5000+(2.6GHZ), 4GB Ram.[/SIZE]
 
[SIZE=2]I am asking this cuz before I faced some troubles with it when trying to shift between them, sometimes no xwindows only terminal, poor video quality...etc.[/SIZE]
 
[SIZE=2]Sorry if that if it was long and thanks for your help.[/SIZE]

---

### Post by cascade9 on 2010-12-13
The difference is that the 173.xx drivers were never made for 9500s, they were for the FX series (there is some support for the 9XXX series chips in the 173.xx drivers, but its not a good thing to try unless everythign else has failed. 

Nvidia-current from the repos is the easiest way to go. If you get a newer kernel, etc, with manually installed nvidia drivers, you might need to remove and then reinstall them to get your desktop back. 

The manually d/led drivers would be a tiny bit newer, but its not worth worring about.

---

### Post by Fordc307 on 2010-12-13
Thank you for the advice. I will go with the current one then.

---

### Post by cascade9 on 2010-12-13
Its the easiest option. 

Good luck, not that you should need any luck ;)

---

