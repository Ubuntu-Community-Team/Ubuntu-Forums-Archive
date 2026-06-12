---
title: "schedules direct help"
date: 2009-05-09
forum: Mythbuntu
---

### Post by bgolpmp on 2009-05-09
Thanks for reading. I have everything working pretty good so far, but am having trouble getting the names of the showes to come up on the guide. It says unknown. It does have the channel names, but not the shows. With the little I was able to find, the setup kinda seems very easy. Am I missing something???????
 
All I did was setup the video in myth setup. Was there more?
I am not sure if it matter, but the card in a Hauppauge 500
Thanks
 
Andy

---

### Post by Dewey_Oxberger on 2009-05-09
Do you have a Schedules Direct account?

Did you put your account info into myth?

If so then check the logs (/var/log/mythtv) and see what you can find.

---

### Post by bgolpmp on 2009-05-11
Thanks for the reply
 
Yes I do have an a schedules direct account. I paid for a year. I did put all the info into myth setup. I looked for anything in the log, and can't find anything. I did get some of the channels names and programs, but maybe only half. The other half still says unknown. And it won't let me record on those of course. 
 
Please help!!!
 
 
Andy

---

### Post by 4dognight on 2009-05-11
Did you run mythfilldatabase?

---

### Post by bgolpmp on 2009-05-12
Thanks for the reply. Mythfilldatabase runs automatically when I finish running the myth setup right?
 
Thanks
 
Andy

---

### Post by iitywygms on 2009-05-12
First , make sure you xmlid is correct for each channel.  You will find that info at schedules direct.  After you are sure the xmlid is correct, run mythfilldatabase with the refresh-today option.
See if that helps.

---

### Post by bgolpmp on 2009-05-12
I fixed it! All I did was delete the old input setting and create a new one. Then all the channels were there.
 
Thanks for all the help!
 
Andy

---

