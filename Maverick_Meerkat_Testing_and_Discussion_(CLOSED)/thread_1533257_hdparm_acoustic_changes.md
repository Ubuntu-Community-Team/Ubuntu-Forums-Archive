---
title: "hdparm acoustic changes"
date: 2010-07-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bladerunner6 on 2010-07-17
recent update of hdparm now overrides the acoustic level in maverick, I have it set to 200 but the recent update changes it to max setting

---

### Post by andrek on 2010-07-18
Sorry for spamming in your thread, but i've got a question regarding hdparm. How do I set it so that it could run on startup without asking me for password? I'd like to set APM and AAM to 230, thus I need to do sudo hdparm -B 230 /dev/sda and (...) -M 230 (...).

---

### Post by MacUntu on 2010-07-18
You'd put that command (without sudo) into the file '/etc/rc.local' (make sure 'exit 0' stays the last line).

---

### Post by andrek on 2010-07-18
> **MacUntu said:**
> You'd put that command (without sudo) into the file '/etc/rc.local' (make sure 'exit 0' stays the last line).

Would it be like
```
hdparm -B 230 /dev/sda &
hdparm -M 230 /dev/sda
exit 0
```
?

Thanks.

***edit***


> **MacUntu said:**
> Without the '&' and I guess you can combine it to```
hdparm -B 230 -M 230 /dev/sda
exit 0
```

Thank you.

---

### Post by MacUntu on 2010-07-18
Without the '&' and I guess you can combine it to```
hdparm -B 230 -M 230 /dev/sda
exit 0
```

---

### Post by bladerunner6 on 2010-07-20
doesnt work for me,

maverick overrides

---

### Post by psyke83 on 2010-07-21
There's already a dedicated config file for hdparm: /etc/hdparm.conf

Editing this file should have the desired effect (on subsequent reboots).

---

### Post by MacUntu on 2010-07-21
> **bladerunner6 said:**
> doesnt work for me,

maverick overrides

Sorry, missed your point. :oops:

> **psyke83 said:**
> There's already a dedicated config file for hdparm: /etc/hdparm.conf

Editing this file should have the desired effect (on subsequent reboots).

Just tested it with APM (my Seagate Momentus 7200.3 doesn't have AAC) and it didn't work (like with putting it in rc.local). Maybe it's overwritten by /usr/lib/pm-utils/power.d/95hdparm-apm - but I haven't found anything connected to AAC. :confused:

Also very weird: on battery, my APM value goes down to 1 - shouldn't be good for the load cycle count.

---

### Post by bladerunner6 on 2010-08-03
bumping this,
i had it work but it overrides again (latest updates)

---

### Post by cariboo on 2010-08-03
Have you created a bug about the problem? I can't seem to find anything.

---

### Post by bladerunner6 on 2010-08-04
I figured it out,

pm-utils related 

the acoustic setting in /usr/lib/pm-utils/power.d/harddrive 
is maxed which is causing the override.

DRIVE_ACOUSTIC_MGMT_AC="${DRIVE_ACOUSTIC_MGMT_AC:-254}"
DRIVE_ACOUSTIC_MGMT_BAT="${DRIVE_ACOUSTIC_MGMT_BAT:-254}"

i change the 254 to something lesser to get aam to my liking

---

### Post by andrek on 2010-08-04
I just wish this bug would be fixed anytime soon : [https://bugs.launchpad.net/ubuntu/+bug/399978](https://bugs.launchpad.net/ubuntu/+bug/399978)

---

