---
title: "Mythtv: Mythmusic settings hang then crash mythfronten"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by pssturges on 2007-08-03
Hi,

I have my myth setup pretty well now after several weeks. One of my few remaining issues is with Mythmusic. When I try to go to the settings for mythmusic, so as I can input the location of my music library, it hangs...There is much hdd activitiy for anything upto 1/2 an hour. Then myth frontend crashes. The same thing happens when I try to enter any menu related to music.

Are there any logs or similar that I could look at in order to track down this problem?

Thanks
Phil

---

### Post by Scorpuk on 2007-08-03
There is a log file for the mythtvbackend and is located here:


/var/log/mythtv


Another way to see what is happening when you run the frontend though is to run mythfrontend from a terminal. If the frontend crashes then what was happening at the time will be logged in the terminal.



Hope this is of some help to you.

---

### Post by jayx101 on 2007-08-05
Hi, am having exactly the same issue, have you found a solution yet? Would really appreciate it!

---

### Post by newlinux on 2007-08-05
show us the output of your mythfrontend and backend logs when this happens. that will help us help you.

---

