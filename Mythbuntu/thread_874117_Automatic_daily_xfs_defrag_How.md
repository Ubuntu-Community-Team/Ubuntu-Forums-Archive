---
title: "Automatic daily xfs defrag? How?"
date: 2008-07-29
forum: Mythbuntu
---

### Post by Markus72 on 2008-07-29
Hi,

I've just installed Mythbuntu 8.04 and was glad to find that option named something like "automatic xfs filesystems defrag"... I checked it. It installed something.

How does this work now? When is the defrag started and by what (it's no cron).

Any idea or help will be appreciated. Just want to know if it really works.

Thx
Markus

---

### Post by transactionlogfiller on 2008-07-29
I don't know about what you have installed, but I found this article about defraging xfs to be useful.

[http://www.linux.com/feature/141404](http://www.linux.com/feature/141404)

---

### Post by laga on 2008-07-29
It should have created '/etc/cron.daily/mythtv-xfs-defrag'. Is something broken?

---

### Post by Markus72 on 2008-07-30
Hi,

thanks for the information. I've not checked that yet (but I will ;-))

I just was wondering why it didn't start after I switched on the option and even rebooted twice.

I have to admit that I'm not familiar with these cron things... but I'll find out (if you have an short explanation, I would be glad, nevertheless ;-))

Thanks
Markus

---

### Post by Markus72 on 2008-07-31
Hi,

jepp, there is some entry... but when does it execute?
I (re)booted now two days in a row without a run.

Markus

---

### Post by laga on 2008-07-31
Well, why do you reboot? And how do you know that it doesn't run?

---

### Post by Archmage on 2008-07-31
I think the idea of it is to do the defrag, when you are not watching (and the PC isn't something that is using the harddrive).

---

### Post by newlinux on 2008-07-31
The way ubuntu is setup anacron actually ends up running cron.daily (although anacron is called by cron). So you can find (and change) the time it is run in /etc/cron.d/anacron. Note this will change the time of day when all cron.daily tasks are run.

---

### Post by Markus72 on 2008-08-04
Hi,

my Mythbuntu machine is not running all the time.
It's more or less powered off unless it starts automatically for recording or if I start it manually.

I expected that mythtv controls the xfs rebuild by itself (since it's an option within the admin gui).

Like e.g. mythfilldatabase I expected that mythtv would stay up and running until defragmentation is done and after that shut down.

Is that defragmentation option useful in my case?
Is data consistency harmed if mythtv decides to shut down automatically during an xfs defrag?

Markus

---

### Post by newlinux on 2008-08-04
The way anacron works, if the job hasn't been run in n periods (whatever is specified in anacrontab) I think it should run on boot... How did you determine it did not run? Depending on the fragmentation you have and the size of your hard drive it shouldn't take too long to run. However I have no idea how it would react to being shutdown during the middle of of a defrag and what the consequences would be.

---

