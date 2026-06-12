---
title: "Ubuntu 14.04 LTS and &quot;current user does not have permission to access serial devices&quot;"
date: 2015-10-04
forum: Multimedia Software
---

### Post by charles_hidalgo on 2015-10-04
I really need to use this software but have tried and I cannot. When it starts I get a message saying.....     The current user does not have correct permissions to access serial devices. Use "sudo adduser <username> dialout" and then log out and in again     ...... I have tried this:

[COLOR=#111111][FONT=Consolas]sudo usermod -a -G dialout username

[/FONT][/COLOR]and the initial message has went away but I now get a message saying 

      Error opening port: Permission denied

I really have been looking around reading trying to help myself before I asked for help here. If anyone can help or point me in the right direction I would appreciate it. Thank you.

Charlie

---

### Post by coldraven on 2015-10-04
I'm not a great expert on serial devices but to get the ball rolling what command are you running that gives the error messages above? Also what device are you trying to connect to?

---

### Post by charles_hidalgo on 2015-10-04
I'm opening a program called APM Planner. It connects to a multirotor I fly and it allows autonomous mapping and flight controller (PixHawk in this case) adjustments. It connects with a USB hardwire or a USB wire to a wireless 900mhz radio telemetry system.

---

### Post by charles_hidalgo on 2015-10-04
Ok I got lucky. I installed PuTTy SSH Client and it all works for now. Maybe this will help others. Thank you for your help coldraven.

---

### Post by coldraven on 2015-10-04
OpenSSH is installed by default so you can SSH directly from the terminal, Putty is only really useful for Windows users. 
A nice tutorial explaining SSH config files can be seen here: [http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/](http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/)

---

### Post by charles_hidalgo on 2015-10-04
Thanks for the link there's some good reading.

---

