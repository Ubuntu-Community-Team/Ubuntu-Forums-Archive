---
title: "Brand New Install Problem"
date: 2007-10-25
forum: Mythbuntu
---

### Post by stumped_guy on 2007-10-25
Ok, I had a working install of Mythbuntu and changed something, the computer crashed, and then nothing happened from there. Decided to redo the install (i had tweaked many things earlier to play around) and then redo the install mythbuntu control centre. That is when the problem started. Igo this message in the frontend setup after setting up the master backend (everything checked out in the be) and it said it "could not connect to the master backe -- is the correct setting of the IP in the config file?" Everything is in the defalut settings the loopback address (127.0.0.1) and nothing has changed. I even tried changing the IP address to the one assigned by my router. The same message. I even tried re-downloading the cd, checking for the correct md5sum and then checking the burnt cd for defects. The same thing.


My Setup:
The computer is a Master Backend/Frontend
A Dell E510 (3.2 GHZ P4 w/ HT
1 GiB RAM
Nvidia 7600 GS (512 RAM)
3 - 160 GiB HDD (2-SATA 2 1-IDE)
Newest envy installed nvidia driver



Could someone please tell my what is going on here as I have changed nothing. No passwords, no locations, no MySQL setting, nothing but seeing if the IP address had anything to do with it.

I thank you in advance!



EDIT: I went to the command line and tried to restart the mythtv-backend. I tried the restart command and it said "no mythtv-backend running to none killed" but said nothing about starting. The i gave it the stop command and it said "no backend running so none killed" I am getting conflicting messages (going to Mythtv-backend setup it says it is running but the command line says it is not) but from what I can tell, mythtv-backend is not starting or is not starting properly. I watched the startup display and checked dmesg but there are no anomalies. :confused:

---

### Post by superm1 on 2007-10-25
> **stumped_guy said:**
> Ok, I had a working install of Mythbuntu and changed something, the computer crashed, and then nothing happened from there. Decided to redo the install (i had tweaked many things earlier to play around) and then redo the install mythbuntu control centre. That is when the problem started. Igo this message in the frontend setup after setting up the master backend (everything checked out in the be) and it said it "could not connect to the master backe -- is the correct setting of the IP in the config file?" Everything is in the defalut settings the loopback address (127.0.0.1) and nothing has changed. I even tried changing the IP address to the one assigned by my router. The same message. I even tried re-downloading the cd, checking for the correct md5sum and then checking the burnt cd for defects. The same thing.


My Setup:
The computer is a Master Backend/Frontend
A Dell E510 (3.2 GHZ P4 w/ HT
1 GiB RAM
Nvidia 7600 GS (512 RAM)
3 - 160 GiB HDD (2-SATA 2 1-IDE)
Newest envy installed nvidia driver



Could someone please tell my what is going on here as I have changed nothing. No passwords, no locations, no MySQL setting, nothing but seeing if the IP address had anything to do with it.

I thank you in advance!



EDIT: I went to the command line and tried to restart the mythtv-backend. I tried the restart command and it said "no mythtv-backend running to none killed" but said nothing about starting. The i gave it the stop command and it said "no backend running so none killed" I am getting conflicting messages (going to Mythtv-backend setup it says it is running but the command line says it is not) but from what I can tell, mythtv-backend is not starting or is not starting properly. I watched the startup display and checked dmesg but there are no anomalies. :confused:

The best place to start out is checking /var/log/mythtv/mythbackend.log.  This will tell you why the backend wouldn't be setup/starting.

---

### Post by stumped_guy on 2007-10-25
I found out why the frontend would not work. turns out the backend really wasn't starting. I now have to run:
```
/usr/bin/mythtv-setup
```
for the backend to really start. Then I can do all I want with the frontend
Now, just to figure out why the backend doesn't start like it is supposed to...

---

### Post by superm1 on 2007-10-25
> **stumped_guy said:**
> I found out why the frontend would not work. turns out the backend really wasn't starting. I now have to run:
```
/usr/bin/mythtv-setup
```for the backend to really start. Then I can do all I want with the frontend
Now, just to figure out why the backend doesn't start like it is supposed to...
That will start it.  Honestly best way to find out why its not doing it on its own: reboot.

First thing tail /var/log/mythtv/mythbackend.log

It will tell you exactly what's going on.

---

### Post by stumped_guy on 2007-10-25
I went and checked the backend's log and it said error about no user 'mythtv'. I went to try and create that user but it said that username was already taken and to use another. :confused:


Oh well, tomorrow is Friday and then I have time to work on it again, reainstall and reconfigure and learn from my mistakes. 


Thankyou for helping me. I am still new to linux but I am learning from my mistakes. :lolflag:

---

### Post by superm1 on 2007-10-26
From the tone of your first post it sounds like you did an Ubuntu install and then added mythbuntu to it.  If this is the case, please do install from the live cd this time around.  Good luck!

---

