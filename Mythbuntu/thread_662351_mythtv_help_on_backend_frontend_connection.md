---
title: "mythtv help on backend frontend connection"
date: 2008-01-08
forum: Mythbuntu
---

### Post by taehC on 2008-01-08
How do i connect them?
on my backend machine when i go to the control center i cant change any mysql things.  what do i do to set this up?

---

### Post by taehC on 2008-01-08
basically i want to connect my frontend to my backend but i dont know how.  can someone plz help?

---

### Post by taehC on 2008-01-08
what info do i type into the mysql part in the control center on my frontend?

---

### Post by aaltieri on 2008-01-09
If you look at

/etc/mythtv/mysql.txt

You'll see a file that looks like this:

> 
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=SAferSe23



That's the SQL password the front end is looking for. 

anthony

---

### Post by charlemagne86 on 2008-01-09
i've done that...

another terminal opens with some code..which looks like error msgs...n then poof!!

it closes...bt the backend still is not configured!

help!

---

