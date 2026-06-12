---
title: "Nvida. After Installing Driver System wont boot"
date: 2011-02-10
forum: Multimedia Software
---

### Post by Krabby.Linux on 2011-02-10
Hey, i have a biiig Problem.

I updated to Natty Narwhal. Everything went fine for a few days. Then i activated one of the additional Drivers recommended by the Additional Drivers utility. After restarting my system i am not able to see anything. System wont boot. I can enter the Terminal. If I try to switch with strg+alt+F7 to the graphic environment i see some processes with an [OK] at the right. Nothing more.

I asked a friend of mine....
What i did :
Deletet Xorg.conf
used command => "sudo dpkg -r nvidia-xxxx"     xxxx= all files possible except nvidia-common. Which means that the drivers should be deletet.

I cant do anything about it ... dont know what to do :(. apt-get wont work because it seems that my eth0 connection to the internet does not work, it seems to be disabled or not activated. It would be a nice help if you can tell me how i can activate the eth0 connection to get internet access and which nvidia package to install and how.

Any Ideas

Thank you very much.

Krabby

---

### Post by Krabby.Linux on 2011-02-10
I have searched the Forum. It seems that there are similar Problems with Nvidia drivers on different Ubuntu Releases. Dont think that this is because of Natty.

---

### Post by Krabby.Linux on 2011-02-10
Guess i posted in the wrong Forum... Sorry. So here again my Post. Please help :).


Hey, i have a biiig Problem.

I updated to Natty Narwhal. Everything went fine for a few days. Then i  activated one of the additional Drivers recommended by the Additional  Drivers utility. After restarting my system i am not able to see  anything. System wont boot. I can enter the Terminal. If I try to switch  with strg+alt+F7 to the graphic environment i see some processes with  an [OK] at the right. Nothing more.

I asked a friend of mine....
What i did :
Deletet Xorg.conf
used command => "sudo dpkg -r nvidia-xxxx"     xxxx= all files  possible except nvidia-common. Which means that the drivers should be  deletet.

I cant do anything about it ... dont know what to do :sad:.  apt-get wont work because it seems that my eth0 connection to the  internet does not work, it seems to be disabled or not activated. It  would be a nice help if you can tell me how i can activate the eth0  connection to get internet access and which nvidia package to install  and how.

Any Ideas

Thank you very much.

Krabby

---

### Post by P4man on 2011-02-10
Its still the wrong forum, since this is about Natty Alpha, you should post it here:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

But please dont post it a 4th time, ask a moderator to move it.

BTW, you shouldnt run alpha releases if bricking it means 'big problems'. Alpha releases are big problems by definition.

---

### Post by Krabby.Linux on 2011-02-10
No Idea ? I need my Computer for a important Presentation tomorrow :(

---

### Post by Krabby.Linux on 2011-02-10
Its just the Driver ... Nothing more ... :(. Alpha worked fine....

---

### Post by P4man on 2011-02-10
Its just a driver that doesnt yet support the X server in natty.

---

### Post by Krabby.Linux on 2011-02-10
And how do i get the old one back?

---

### Post by P4man on 2011-02-10
No idea im afraid. But I would strongly recommend you reinstall 10.10 or 10.04 since you seem to depend on the install for work, and install natty on a separate partition to test/play with, so that you can wipe and reinstall it whenever needed.

---

### Post by overdrank on 2011-02-10
Threads merged. :) Please feel free to start a new thread in [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394"). :)

---

### Post by Krabby.Linux on 2011-02-10
So If I have a Ubuntu 10.10 Live CD. Can I reinstall it without getting any Data or Information lost? I just want my old system back or a nvidia graphics driver which is working....

---

### Post by P4man on 2011-02-10
No, reinstalling will pretty much wipe your drive. 
Make a backup first.

Anyway, get this thread moved to the right forum, and maybe someone more experienced with natty can help you out temporarily fix your install, but you really shouldnt be running alpha versions for productivity.

---

### Post by Krabby.Linux on 2011-02-10
Ok, thanks. Will ask my mate if he can help me out :(.


If there is anyone with any ideas... I would be thankful if anyone solves my problem :)

---

### Post by erolerten on 2011-07-30
dear all, 

i have the very same problem.
After installing the proprietary drivers for my ati graphics card, the system gets messed up, apart from the installation taking ages, sometimes crashing and sometimes not getting completed (yes< i have tried many times).

big disappointment for a linux user, since 5 years... never had a distro update which was flawed this much..

---

