---
title: "Could not connect to the master backend server (after the first run)"
date: 2012-12-24
forum: Mythbuntu
---

### Post by batticiof on 2012-12-24
Hi,
I have installed mythbuntu. The first time both backend and frontend worked fine. After the reboot and the selection of country and language, every time that I open the frontend I have the message: Could not connect to the master backend server....
I have checked and the backend is running.
All the IP number are 127.0.0.1.
The dvb usb is working and I have already scan the channels.
I have search for some similar problem in several forum but I was able to find a solution.
Is there someone that as some idea about how to help me. It is one week that I read threads and re-install mythbuntu, but I am sure that there is some configuration to modify.

Thank you for your helpfulness

AG

---

### Post by batticiof on 2012-12-25
I have tried to re-install another time the whole mythbuntu, and now I have got this error from the beginning.
Any suggestion?

AG

---

### Post by jksj on 2012-12-26
What version of mythtv are you installing on which version of ubuntu?
If it is 0.26, check that all versions of config.xml are the same, there will be three copies. For some reason the install routine does not seem to set up the frontend password reliably. If the backend is working the  the password and network address in  
/etc/mythtv/config.xml
should be copied into the version in your home & mythtv
 user directories. Use locate config.xml to find them.
If that does not work follow the trouble shooting guide.
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

---

### Post by batticiof on 2012-12-26
Thank you for you answer. I am installing the last version of mythbuntu. Now, I am trying to install mythtv from Ubuntu. After that I will try to follow the instructions listed in the link that you provide me.

Thank you

AG

---

### Post by batticiof on 2012-12-26
Nothing, I have checked the three files config and all the settings are ok. I have also read the whole Troubleshooting page and no solution is able to solve my problem.

---

### Post by batticiof on 2012-12-28
I have solved the problem. The solution is disable the IPv6.

---

