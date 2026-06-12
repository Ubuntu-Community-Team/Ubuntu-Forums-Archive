---
title: "reboots"
date: 2007-12-10
forum: Mythbuntu
---

### Post by ghostwalker50 on 2007-12-10
Hi
im trying to schedule a reboots every day , i install KCron in the hope that it will help but i  can do a schedule reboot any help

---

### Post by ubnewbie2 on 2007-12-10
Why on earth would you do this? It's not Windows.  It'll run for months/years with needing to reboot.

---

### Post by uopjohnson on 2007-12-11
I don't know why you would do this either, but here goes.
```
sudo echo '/sbin/shutdown -r now' > /etc/cron.daily/99shutdown
sudo chown root:root /etc/cron.daily/99shutdown
sudo chmod 755 /etc/cron.daily/99shutdown

```
Anything in /etc/cron.daily that is executable gets executed
 every day.  the 99 should ensure it gets done last.  You could also schedule the shutdown for the future by replacing 'now' with a time offset.  ex 
```
shutdown -r +60
``` would bring the system down in one hour.  
Enjoy.

---

### Post by superm1 on 2007-12-11
Something you will most definitely need to be mindful if you are going to do this:

You really should query if the backend or frontend are busy when you reboot is scheduled.  The last thing you want to do is have a recording cut off for 5 minutes while your machine was shutting down and rebooting.

---

### Post by ghostwalker50 on 2007-12-11
every so offen i loss connect to teh backend. it gos offline. os im trying to just reboot the computer every day at 5am. is their some thing im doing worng.  any help

---

### Post by uopjohnson on 2007-12-11
AH.  Ok.  Now we have a question to which the answer is probably not reboot your computer everyday.
The first place I would check is your backend logs to see what might be going on.  You can find them in /var/log/mythtv/mythbackend.log
If you find anything suspicious there post it for analysis.  If there isn't anything there then you should try and issolate the time that the backend dies to discover what it might be doing at that time.

---

### Post by ghostwalker50 on 2007-12-12
i looked at the log and see somuch stuff in it. is their some thing i can look for,  and as for the time it coud me in the am of after noon.

---

### Post by uopjohnson on 2007-12-12
OK well go ahead and post the contents of 
/var/log/messages 
and
/var/log/mythtv/mythbackend.log

I will take a look at them.

---

