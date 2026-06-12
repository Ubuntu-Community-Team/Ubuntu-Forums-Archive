---
title: "mythfilldatabase not updating"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-05-24
Feisty myth frontend/backend on the testmule.

If I run mythfilldatabase from the terminal I get the 2 weeks of programming, but no daily updates after that.

I did run the setup changes and checked the box to automatically run mythfilldatabase and to run it at times suggested by the grabber.  

I just restarted the backend, I'm hoping that it will update the DB after the restart.

---

### Post by barney_1 on 2007-06-11
I'm running into this same problem after setup up a mythtv box from scratch using Feisty.  I can run mythfilldatabase no problem, but it's not running automatically.

Did you ever find a solution for this issue?

Edit:  I didn't have the frontend settings for it:  Utilities/Setup-->Setup-->General on the last page select "Automatically run mythfilldatabase"

---

### Post by mcpish on 2007-06-12
best thing to do is just put in in your crontab of your mythtv user and specify for mythfilldatabase to run at a certain time each day

at a shell type:

crontab -e

add the following line for it to run automatically at 6AM every morning (edit the number 6 for a different time):

0 6 * * * mythfilldatabase

---

### Post by canzi on 2007-10-11
same thing for me, im using the crontab solution.

the problem is that in feisty mythtv runs as the user 'mythtv' and does not have access to (in my case) tv_grab_au because shepherd is in the home directory of the user i created.

a solution would be to login as mythtv and setup shepherd (tv_grab_au) for that user

---

### Post by oobe-feisty on 2007-11-15
> **canzi said:**
> same thing for me, im using the crontab solution.

the problem is that in feisty mythtv runs as the user 'mythtv' and does not have access to (in my case) tv_grab_au because shepherd is in the home directory of the user i created.

a solution would be to login as mythtv and setup shepherd (tv_grab_au) for that user

thank you your post helped me solve this issue 

this is what i did to work around it 

ln -s ~/.shepherd /home/mythtv
ln -s ~./.mythtv /home/mythtv

chmod -R 777 ~/.shepherd ~/.mythtv

i added the chmod as i was getting this error . FAILED: xmltv returned error code 3328.

which turned out to be read write permissions for myth user i found this out by
 su - mythtv then running mythfilldatabase
i could see what the problem was i hope this helps someone

i did all this cause for some reason the crontab solution would not work for me

---

