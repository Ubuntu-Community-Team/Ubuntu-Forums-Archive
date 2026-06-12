---
title: "Flash9 in Mozilla but not in Firefox still Flash7"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by free10 on 2007-01-25
OK I got Flash 9 loaded and working fine in Mozilla, including sound with a reboot, but but Firefox is still t Flash7. I think I see the problem as /user/lib has one folder labeled mozilla-firefox and another one labeled firefox, and the plugin folder for mozilla-firefox plugin folder seems to have the new larger flash9 so file, but not in the firefox folder plugin folder which has the smaller 2.0mb so flash7 file. Now I am guessing here, that I just need to delete the two older flash files out of the plugin folder in firefox, and copy over the two newer ones out of moxilla-firefox plugins but don't know how since Ubuntu doesn't let us write to those file normally. I also figure it can be handled with terminal and sudo something but don't know the command. Got any suggestions?? Thanks Dwight

---

### Post by benerivo on 2007-01-25
Your plan should work. Try

sudo nautilus 

in a terminal and it should open a normal windows explorer / browser but with root privileges so thjat you may cut, copy and paste almost anywhere in your system.

---

### Post by free10 on 2007-01-25
Yep, you were right and that is a handy command to know and I am saving it in an email draft. That is where I save a lot of useful info for easy recall later. Firefox is now running Flash9 with no problems at all. I found another set of Firefox plugins over in OPT and those were the Flash ones needing replacing with the ones from Mozilla to get it to work. I sure do thank you---Dwight

---

### Post by IcemanV9 on 2007-02-15
I have same exact problem - Firefox sees flash7 & flash9. Some websites do not see flash9, only flash7. It drives me batty. Anyhow, I simply removed flash7 from my home directory - .mozilla/plugins. Now, Firefox sees flash9.

---

