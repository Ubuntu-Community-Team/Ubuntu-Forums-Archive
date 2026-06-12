---
title: "Lost my wifi all together"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by smooth5959 on 2011-06-20
I was running a patch of my wifi connection and now i have NO wifi at all. I am totally lost right now. i have been running throught all the threads but nothing is really working. Is there a way do a full system restore (like windows) that will undo all my mistakes? my wifi has always worked until i screwed something up!

---

### Post by Brad_J on 2011-06-20
I'm pretty new to linux but I'll try to help. What version of ubuntu are you using? Is there a wireless symbol on the top bar? What does it say when you click it?

---

### Post by smooth5959 on 2011-06-20
i have been running 11.04 since it came out, it has been working until i went to the compat-wireless page today and strated following the update instructions. On the top menu i have a connection icon, but nothing says wireless just Wired networks (and i dont have wired connection hooked up to the laptop)

---

### Post by smooth5959 on 2011-06-20
ok i think i fixed it, i used the following commands
Make sure you are in the directory "compat-wireless-2011-06-19" (or the date you d/l the new drivers)
$ cd compat-wireless-$(date -I) $ sudo make uninstall $ sudo make wlunload[FONT=Verdana]
 then restart the computer with the wifi switch in the on position. thanks for the support 
[/FONT]

---

### Post by Brad_J on 2011-06-20
EDIT: Posted right after you said you fixed it

---

### Post by smooth5959 on 2011-06-20
Thanks man, i appreciate your offer to help. Good looking out.

---

