---
title: "Startup Programs Starting Twice!"
date: 2009-01-10
forum: Mythbuntu
---

### Post by jonno on 2009-01-10
I installed some upgrades this morning and ever since, when I restart my system all the programs set to launch on startup are starting twice. Ie there are 2 versions of Mythfrontend running. Any ideas on what could be causing this and how to fix it?

---

### Post by jMon54 on 2009-01-10
I just noticed I had two frontends autostarting too.  I deleted one and after that I had trouble getting my remote to work.

---

### Post by jonno on 2009-01-10
Too weird.

Here's the Synaptic log of what was upgraded:

> Commit Log for Sat Jan 10 08:37:33 2009


Upgraded the following packages:
bind9-host (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
dnsutils (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libbind9-40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libdns43 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisc44 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisccc40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisccfg40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
liblwres40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libssl-dev (0.9.8g-10.1ubuntu2) to 0.9.8g-10.1ubuntu2.1
libssl0.9.8 (0.9.8g-10.1ubuntu2) to 0.9.8g-10.1ubuntu2.1
ntp (1:4.2.4p4+dfsg-6ubuntu2.1) to 1:4.2.4p4+dfsg-6ubuntu2.2
ntpdate (1:4.2.4p4+dfsg-6ubuntu2.1) to 1:4.2.4p4+dfsg-6ubuntu2.2
nvidia-177-kernel-source (177.80-0ubuntu2) to 177.82-0ubuntu0.1
nvidia-177-modaliases (177.80-0ubuntu2) to 177.82-0ubuntu0.1
nvidia-glx-177 (177.80-0ubuntu2) to 177.82-0ubuntu0.1
openssl (0.9.8g-10.1ubuntu2) to 0.9.8g-10.1ubuntu2.1


---

### Post by jonno on 2009-02-04
I'm still having this problem. Where does linux store the startup program information or does it just depend? Any hints of places to start looking would be nice.

---

### Post by jonno on 2009-02-04
Or even better, once a program has started is there a way to tell how it was started? This is on the xfce environment.

---

### Post by fenx7 on 2009-02-05
I had the exact problem - googled - and found that it had to do with the session being saved with 1 version of mythfrontend and the 2nd was being autostarted as desired. I do not have the link handy unfortunately. It mentioned other methods to fix, but what I did is load mythbuntu. Gracefully exit all programs, log off from the menu and ticked save session.

In xfce settings from the application menu --> autostarted apps shoudl contain an entry to start mythfrontend.

autostart apps works by placing the ".desktop" file that link to the app into /etc/xdg/autostart

---

### Post by jonno on 2009-02-05
Just noticed that a Terminal also opens up in the background on boot along with the 2 Skype sessions and 2 mythfrontend sessions.

I did some digging and found the following in ~/.config/autostart/
mythtv.desktop nm-applet.desktop Skype.desktop
I renamed the Skype one to Skype.desktop.bak and rebooted and it only started up one session of Skype. That tells me that my system is not somehow using the scripts in autostart twice.
The launching of the terminal makes me think that somehow a session got saved on shutdown when I had a terminal open and now it's starting all those currently running programs along with the ones it should be starting.
If it matters, the Exec line in mythtv-desktop is:
Exec=mythfrontend --service

Now I still have to find where it is launching the other versions of the programs.

---

### Post by fenx7 on 2009-02-05
Think you should leave the autostart items, login as normal, close all programs then logout and tick save session. Log back in and hopefully there will be no duplicates.

---

### Post by jonno on 2009-02-06
Thanks for the suggestion fenx7. I'll try later today.

That did the trick.

---

### Post by jMon54 on 2009-02-17
In playing around with my settings I made a mess.  Now I get a kubuntu login screen that does not like my password.  The only way I can start Mythbuntu is by logging in at the console then sudo startx.  I have kubuntu not starting at startup but still it comes up and worse does not let me in!!  How can I repair this thing??

---

