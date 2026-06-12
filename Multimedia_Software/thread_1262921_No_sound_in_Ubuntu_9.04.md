---
title: "No sound in Ubuntu 9.04"
date: 2009-09-10
forum: Multimedia Software
---

### Post by Iwavns on 2009-09-10
[SIZE=3]I have just installed Ubuntu 9.04 on my laptop, but there is no sound in Ubuntu at all. I also have Windows Vista in my laptop and there are no sound problems in Vista so I think there must be some software issues in my Ubuntu, can anyone help please? 
 
Below are the details of my sound hardware: 
IDT High Definition Audio CODEC 
IDT 92HD71B7X 
 
Intel (R) High Definition Audio HDMI 
Intel G45 DEVCTG 
 
(I already have the most recent version of ALSA-driver) 
 
[/SIZE]

---

### Post by Iwavns on 2009-09-15
I have since tried some troubleshooting myself since no one replied me... I've found out that the Intel Sound Card in my laptop is not supported by ALSA since it  belongs to the ICH9 family. But I am quite sure that the IDT Sound Card (IDT 92HD71B7X) is supported because "92HD71X" is listed in the official ALSA site. But the problem is Ubuntu does not detect the IDT Sound Card. I've also found out in ALSA-configuration.txt that 92HD71B* only has configuration for Dell Desktops, mine is a Compaq CQ40 Laptop. What can I do?

---

### Post by Iwavns on 2009-09-15
..I searched for CQ40 in this forum and found the solutions to my problem in this thread: [http://ubuntuforums.org/showthread.php?t=1210088](http://ubuntuforums.org/showthread.php?t=1210088). So the problem is solved now!:) Anyway, I am grateful for those who took the trouble to read my posts.

---

