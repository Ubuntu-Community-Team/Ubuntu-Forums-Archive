---
title: "Mythtv user job returned non-zero"
date: 2015-11-19
forum: Mythbuntu
---

### Post by adam_smith4 on 2015-11-19
This maybe something easy I have over looked but I am unable to get Mythtv to execute any scripts. I get an error message in  mythweb user job returned non-zero. I have execute permission set with mythtv user owner. I have tried placing the script in the mythtv user directory. This has failed with three different scripts.

example

#!/bin/bash
echo hello > /home/mythtv/test.txt

Thank you for your help

---

### Post by blm-ubunet on 2015-11-19
I would look into the mythbackend &/or mythjobqueue logs in /var/log/mythtv/

---

### Post by adam_smith4 on 2015-11-20
Thank you for your help. I did check the mythbackend log but found nothing about the error in there. I have found no mythjobqueue log.

---

### Post by blm-ubunet on 2015-11-20
mythjobqueue is an internal process to the backend so normal job queue logging ends up in BE log.
(mythjobqueue is also an external program that can be used to run jobs on non-backends, exactly how you configure that is still a mystery.)

Run below from terminal to boost verboseness of the running backend:
```
mythbackend --setverbose jobqueue
```
Spy on the backend log with:
```
tail /var/log/mythtv/mythbackend.log
```
Caveat: I use syslog.

---

### Post by adam_smith4 on 2015-11-27
Thank you for your help. The issue has been resolved. I am unsure of the fix. I updated my system from 15.04 to 15.10. This removed Mythtv and left the database. I reinstall without any issues.

Thank you again.

---

### Post by blm-ubunet on 2015-11-27
So you're not using the mythbuntu ppa packages (for mythtv) ?
That ppa only targets LTS versions so it doesn't help you now.

---

