---
title: "[SOLVED] myth-backend at startup"
date: 2007-10-25
forum: Mythbuntu
---

### Post by dwf_starband on 2007-10-25
I have a fresh install of 7.10 and added the mythbuntu control center.
After configuring everything (well some things) I started the frontend and It said it couldnt connect to the backend.  I thought it was issues with mysql and asked in the ubuntu-mythtv irc room and someone there thought the same thing.  I messed around with it for an hour or so last night and finaly went to bed without figuring it out.  Woke up this morning and tried the obvious, I started myth-backend from the command line.  Then the frontend could connect just fine.

Does myth-backend not automaticly start during startup?  
If it is, what have I done to mess it up. 
If it isnt, what is the best way to make it start up automaticly when I start my computer?

Thanks for your help,

dennis

---

### Post by superm1 on 2007-10-25
Dennis:

It does start on system startup.  If its not starting, check out /var/log/mythtv/mythbackend.log

---

### Post by dwf_starband on 2007-10-25
Thanks,

I figured out that my problem was that I didnt have the right permission on the drive I was using for recordings.  Once I changed the permissions mythbackend started properly at startup.

thanks again,

dennis

---

