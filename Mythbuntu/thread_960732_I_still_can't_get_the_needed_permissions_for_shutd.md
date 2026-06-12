---
title: "I still can't get the needed permissions for shutdown"
date: 2008-10-27
forum: Mythbuntu
---

### Post by orangeek on 2008-10-27
Hi.
I'm a new mythbuntu user but I use mythtv under debian and knoppmyth since years.
I noticed that the 'mythtv' user in mythbuntu isn't a normal user like the one created during the installation.
I configured mythtv to use mythwelcome and to shutdown after 300secs of inactivity, but I can't understand how can I grant permissions to shutdown to the user 'mythtv' who, in fact, is the owner of the mythtv processes (mythwelcome, mythfrontend, etc).

I tried messing up the sudoers file (writing 'mythtv ALL=NOPASSWD: ALL', adding the normal user and the mythtv user to the 'sudo' group and uncommenting the proper line), the HAL authorizations (trough the "system>authorizations" menu) but I still can't shutdown the system trough mythwelcome. in the 'general' section in mythtv-setup, I inserted the shutdown command as 'sudo /sbin/halt -p' and '/usr/share/mythtv/myth-halt.sh' and 'shutdown -h now' but with no luck.
I searched in the forums but I can't find any thread with a solution.
I'm using mythbuntu 8.04.

thank you,
orangeek

---

### Post by SpeedyZeroTwo on 2008-10-31
Hi Orangeek,
I'm a novice GNU/Linux user be manged to get mythwelcome to work of sorts....

Have you looking in the mythwelcome log to see the error ?

regards
S02

---

### Post by orangeek on 2008-10-31
hi.
thank you for your answer.
I can see the error in the mythbackend log: it's either related to the °no permission to perform the action/need to be root" or it prompts me to input the sudo password. the latter case doesn't make any sense since the system should shutdown itself without asking any password.
Actually I solved suidding (chmod +s) the shutdown bin.

---

### Post by SpeedyZeroTwo on 2008-11-03
Hi orangeek,

Glad you have it working, although there is a slight security risk that way.

A better way IMHO is to edit sudoers as mentioned here
[http://ubuntuforums.org/archive/index.php/t-305751.html](http://ubuntuforums.org/archive/index.php/t-305751.html)

Step 9

Regards
S02

---

