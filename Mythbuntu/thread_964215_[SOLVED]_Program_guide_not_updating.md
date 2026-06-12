---
title: "[SOLVED] Program guide not updating"
date: 2008-10-30
forum: Mythbuntu
---

### Post by luketb on 2008-10-30
I am having an issue with the program guide not updating itself. If I manually run the mythfilldatabase it downloads and updates the program guide just fine but after a while (2 or 3 three weeks) it becomes out of date and I will get no program information.

I had this issue before and I found a solution, I 'think' it was some sort of permission issue, but I cannot seem to find the solution to this problem.

---

### Post by db260179 on 2008-11-02
Sounds like a common problem of mythfilldatabase not set to run automatically.

see 
[mythtv manual]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#Mythfilldatabase")

find mythfilldatabase

Check the frequency of days run and the execution start or stop time

I have mine set to run daily and a time between 5am to midnight as i dont have the box on all the time.

Hope this helps?

> **luketb said:**
> I am having an issue with the program guide not updating itself. If I manually run the mythfilldatabase it downloads and updates the program guide but it will after a while (2 or 3 three weeks) become out of date and I will get no program information.

I had this issue before and I found a solution, I 'thin' it was some sort of permission issue, but I cannot seem to find the solution to this problem.

---

### Post by SiHa on 2008-11-02
I've found my backend just needs a reboot every couple of weeks, once I notice that the guide data has dropped to less than 8 days, I do Exit & Reboot.

---

### Post by db260179 on 2008-11-03
A bit extreme. If you look at the mythtv manual, you can set it to run automatically. Also in the UK, they keep changing the dvb-t streams so i have to keep running mythtv-backend setup then rescanning the channels again, very annoying.

> **SiHa said:**
> I've found my backend just needs a reboot every couple of weeks, once I notice that the guide data has dropped to less than 8 days, I do Exit & Reboot.

---

### Post by luketb on 2008-11-12
Thanks db260179, that was it, so simple yet so frustrating. I was making it way more complicated than it had to be lol.

Cheers

---

### Post by db260179 on 2008-11-25
No problem

---

