---
title: "Avahi Not Broadcasting afp To Network?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by Return Privacy on 2010-09-06
Hi, I still haven't been able to figure out why my new Ubuntu 10.04 computer won't automatically advertise afp thru avahi to the network? This is a new install of Ubuntu 10.04, I downloaded and installed newest version of Netatalk, and the Avahi daemon. Both installed with no issues. (I followed instructions from articles on here) I can manually login to Ubuntu afp share from my iMac, by going to "Go to Server" and typing in the ip 10.0.1.3 and putting in the Ubuntu username and password. I just can't get it to advertise or broadcast itself to the network like it is supposed to using netatalk and avahi. I've followed all of the tutorials I can find on this, but nothing works. Even if I issue the command to restart avahi daemon, Ubuntu still isn't seen in the iMac's finder window? Because I can manually login to it, I am assuming that netatalk is working properly. I've even tried to issue the command to restart netatalk first, then restart avahi, but still nothing? This is driving me crazy! Please Help, Thanks

---

### Post by lulaz on 2010-09-09
Exactly the same issue here. Running Ubuntu 10.4 on server and MacOS 10.6.4 on the client. In MacOS Finder I can connect to afpd@ubuntu, but Avahi@ubuntu is not advertising services to MacOS - they supposed to show in Finders Sidebar under "Shared" section ;(.
I have spent all day yesterday trying to fix this. I dont have any idea wha can be wrong.
Btw: @ubuntu, command: "avahi-browse -ar" shows all the ubuntus services I want to "advertise".

---

### Post by Return Privacy on 2010-09-10
Hi all,
I kept searching for answers to my problem. Someone(I forget who) suggested to go in and look at the "daemon.log". When I did, I saw an error when it was trying to load the avahi-services.afpd file. It said it was a problem with line 8. Since I had originally just copied and pasted that file during the setup, I figured I messed up. Then I)) read where some people said that when following the how-to's on setting this all up, you have to be careful because sometimes the sytax code is messed up when posted on blogs and some online places. So, I went in and erased the avahi services.afpd file, and got it from another post, and pasted the text in the file. Then, I restarted netatalk and avahi, and it worked perfectly! I can even re-boot the computer and it works automatically like it is supposed to. So, I hope this helps other people with this problem, look at your /etc/var/daemon.log and look for errors when afpd file tries to load. You may have to re-do your file like I did. I hope this helps.

---

