---
title: "unstable network connection"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by Questionmana on 2012-02-07
Good Day.

I have installed ubuntu 11 on a dell inspiron 620 and everything seems to work fine, except for the network connection.

It is very unstable. It works one minute and not the next. 

Prior to installing Ubuntu, the machine had windows 7 installed and the nic worked perfectly so I suspect that this is perhaps a driver issue.

I am a total newbie at linux and appreciate any and all help.

Thanks

---

### Post by h41 on 2012-02-07
i think i got the same problem and after a few hours of googling i found the problem with some solutions but im way overstrained to get them working cause im pretty new to ubuntu

the problem seems to be the r8169 driver

found this bug report on launchpad -> [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393)

this describes the problem and in the comments there is a solution with a few "its working" replies related to the linux-backports-modules-3.0.0 package


but i have no idea how to get it working and need some help


edit:

i just found a threat on aksubuntu.com which referes to a similiar solution but it also overstrains my skills

[http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping](http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping)

---

### Post by h41 on 2012-02-07
alright, fixed the problem but its a little tricky

after searching again i found a threat from this forum : P

[http://ubuntuforums.org/showthread.php?t=1865436&highlight=8168B+realtek](http://ubuntuforums.org/showthread.php?t=1865436&highlight=8168B+realtek)

its basicly a instruction how to deinstall r8169, set it on the blacklist and install the r8168

i recomment u to read the hole threat (only 3 pages) but here is how it worked for me

follow the instructions from wildmann39 and hit the commands in the terminal one by one.


i had to enter the  
[FONT=monospace]```
sudo ./autorun.sh
```twice cause in the first time i got an error
```
FATAL: Module r8168 not found.
```after the procedure everything worked fine for me



but still wondering if there is an easyer solution

[/FONT]

---

### Post by Questionmana on 2012-02-08
Thank you for the help.

I also got stuck at:
sudo ./autorun.sh

It produces the follow output:
@user-Inspiron-620:~/r8168-8.025.00$ sudo ./autorun.sh

Check old driver and unload it.
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
FATAL: Module r8168 not found.
Completed.
user@user-Inspiron-620:~/r8168-8.025.00$ 


I have attached the log file that is created.

Thank you for your help.

---

### Post by Questionmana on 2012-02-10
Fyi - I resolved the issue by moving to Fedora.

---

