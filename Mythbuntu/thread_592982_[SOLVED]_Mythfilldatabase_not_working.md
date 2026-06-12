---
title: "[SOLVED] Mythfilldatabase not working"
date: 2007-10-26
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-10-26
When I installed Mythbuntu I neglected to run mythfilldatabase after I'd setup everything else in Myth TV Setup.  Come to think of it I don't know why I chose not to run mythfilldatabase but I continued with everything else.  

In my last post I setup my LVM and it worked swimmingly.  After setting up the LVM, I ran mythfilldatabase for the first time and it doesn't seem to be working.  I still have no program information.  Mythtv Frontend seems to be working fine.  It's opening up without any problems.  Which to me has meant that it was able to connect to the database.  

When I run mythfilldatabase from the xterm it appears to work.  At least it appears to be doing the same stuff as usual.  But when I go into schedule recordings or look at system information through mythfrontend it says that there's no programming.

Did I mess up by setting up my LVM before running mythfilldatabase for the first time?

I do believe that I've provided the correct username and password for schedules direct because while mythfilldatabase is running it shows that my subscription expires on 10/1/08 which to me tells me that it was able to authenticate my user account.

---

### Post by Meph1st0 on 2007-10-26
Nevermind, I fixed it.  I went back into MythTV backend setup and found that in the Video Sources section I forgot to retrieve my lineup.  Once I did that I was able to get program information.

This thread can be marked as solved as well.

---

### Post by mythbuntu101 on 2010-01-28
i did this and still can;t get it to work. can you provide a step-by-step?

---

