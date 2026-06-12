---
title: "Cinelerra"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by alex1974 on 2007-05-30
Please I need help.

I installed cinerella  2.1CV (C) but when I start I get:

[COLOR="DarkSlateGray"]void MWindow::init_shm():Warning:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7ffffff" >/proc/sys/kernel/shmmax
virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:
[/COLOR]
Any help?

Alex

---

### Post by paparappa on 2007-06-02
I got the exact same problem :/

---

### Post by Alexander Grundner on 2007-07-17
Cinelerra message - echo "0x7fffffff" > /proc/sys/kernel/shmmax

Refernce: [http://osdir.com/ml/video.cinelerra-cv.general/2006-11/msg00115.html](http://osdir.com/ml/video.cinelerra-cv.general/2006-11/msg00115.html)

Add the following in my /etc/sysctl.conf and reboot:

# make cinelerra happy
kernel.shmmax = 2147483647

-----
Worked for me!

---

### Post by Kpax1 on 2007-08-15
I had the same error message.

If you enter that command in terminal as root, then run cinelerra, it will run without the error message as well...

---

### Post by TKR101010 on 2007-08-16
Here's some helpful information I got from someone on another newsgroup ...

do this ...

sudo vi /etc/ini.d/local

Or

sudo nano /etc/init.d/local

Copy and paste the following into the file:

#!/bin/sh
#local boot script
#Entry for Cinelerra
echo "0x7fffffff" > /proc/sys/kernel/shmmax

Run the following command to make the script we created executable:

sudo chmod 755 /etc/init.d/local

Next,  set it to start on run levels 2 through 5. Run
the following command:

sudo update-rc.d local start 99 2 3 4 5

Run cinelerra...by the way...it runs better as root

---

### Post by Sjovan on 2007-08-25
I got another strange prob... The install worked like a charm, but it wont start up.

```
sjovan@xxxxxx:~$ cinelerra
Illegal instruction (core dumped)

```
Any one that knows what I can do?

---

### Post by rhodry on 2007-08-25
> **TKR101010 said:**
> Here's some helpful information I got from someone on another newsgroup ...

do this ...

sudo vi /etc/ini.d/local

Or

sudo nano /etc/init.d/local

Copy and paste the following into the file:

#!/bin/sh
#local boot script
#Entry for Cinelerra
echo "0x7fffffff" > /proc/sys/kernel/shmmax

Run the following command to make the script we created executable:

sudo chmod 755 /etc/init.d/local

Next,  set it to start on run levels 2 through 5. Run
the following command:

sudo update-rc.d local start 99 2 3 4 5

Run cinelerra...by the way...it runs better as root

Followed this ok but get an error when setting the run level:

paul@greywolf:~/download$ sudo update-rc.d local start 99 2 3 4 5
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force

I presume the 99 is the problem but I am unsure how to fix this? Guidance appreciated!

Rhodry.

---

