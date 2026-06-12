---
title: "Running scheduled task as SU"
date: 2008-04-23
forum: Mythbuntu
---

### Post by uMuppet on 2008-04-23
I have to run a script every few days to update my listings, problem being it is a SUDO script.  Are there any scheduled task managers that will run a task as SU?  All the ones I have tried prompt for a password when the script is run, and if you're not sitting in front of the PC at the time, its useless.

---

### Post by Lindsay.Mathieson on 2008-04-23
sudo crontab -e

Will launch the crontab editor as root.

---

### Post by KillerKiwi on 2008-04-23
if you like a nice ui check out [gnome-schedule]("apt://gnome-schedule")

---

### Post by txcrackers on 2008-04-24
There are some directories in /etc that run a bunch of scripts on various, repeated schedules:
```
/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly

```
Any **executable** script in one of those directories will run at the indicated frequency - and will be run by the **root** user. If you need something "in between" daily and weekly, you can have your script check to see if it's a day of week, or a date that's easily divisible by 3, etc. You might also want to be aware of *when* each of those sets of scripts runs:
```
/etc/crontab
```

---

### Post by laga on 2008-04-24
Or fix your script so it doesn't need to be run with root privileges.

---

### Post by uMuppet on 2008-05-18
I thought I had this sorted, but it just will not run for me.

her is the script I need to run daily

```
#!/bin/sh
mono /home/pvr/xmlTVNZ/xmlTVNZ.exe /home/pvr/xmlTVNZ/tvguide.xml -days 5  default_tv1 default_tv2 default_tv3 default_c4 default_prime default_triangle default_maori 
mythfilldatabase --file 1 /home/pvr/xmlTVNZ/tvguide.xml 

```

I have it in a file called "grabber" in the /etc/cron.daily folder, it is set to run as a progrm, it is root:root with 755 permissions.

I can't see why this is giving me such a dam headache.  I can run it in a terminal as sudo just fine.

---

