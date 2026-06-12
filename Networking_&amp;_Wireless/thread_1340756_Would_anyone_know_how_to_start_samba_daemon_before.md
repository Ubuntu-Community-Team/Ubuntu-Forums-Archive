---
title: "Would anyone know how to start samba daemon before Ubuntu loads the login screen?"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by tiras_dude on 2009-11-28
Here is my situation: I want to run a shared folder on my network to access from windows machines. I have a Karmic amd64 system that has 4 users on it, and only one can administer anything and he is not the primary user. Presently, as I understand, the system acquires network IP only after one of the users logs-in, but samba server does not start automatically if the non-administrative user starts the system.
 

 Can anybody give instructions on how to force the system to automatically acquire the IP address and start samba without anyone actually logging-in to the system. Meaning that samba is already running when the boot screen loads.
 

 Thanks

---

### Post by headvampyre@hotmail.co.uk on 2009-11-29
i think samba starts before anyway coz if you read the white lines when your booting generally it will say "startin samba daemons       [ok]" or something like that

---

### Post by tiras_dude on 2009-11-29
negative,

most of the time I have to sudo /etc/init.d/samba start (or restart) to get it going unless admin logs in immediately on boot.

I also tried switching to run-level 19 from default 20, still no go.

---

