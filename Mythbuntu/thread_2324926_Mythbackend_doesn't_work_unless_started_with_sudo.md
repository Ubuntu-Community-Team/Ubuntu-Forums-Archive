---
title: "Mythbackend doesn't work unless started with sudo"
date: 2016-05-17
forum: Mythbuntu
---

### Post by alforddm on 2016-05-17
We canceled our directtv and I'm trying to get mythtv set up on an old laptop that has a broken screen but an hdmi port.  :D  I'm using an HDhomerun and this is a fresh mythbuntu install (just installed this morning).   I've used mythcontrol and added the repos for mythtv 28 and then updated and upgraded everything.    I complied and installed the HDhomerun software from silicon following the instructions on their website.  I did this in an attempt  to figure out why it wasn't working.  

I have everything working except, I have to start mythbackend with sudo to get it to find and use the tuners.    At least I assume that is what is happening.  Mythfrontend finds mythbackend but if you try to "watch tv" it doesn't do anything.  If the computer restarts for any reason, I have to manuall "killall mythbackend" and the start a terminal and use sudo to start mythbackend.   After running with sudo I can watchtv and record fine.  This is a bit of a pain as I stated this is an OLD laptop (6 years) and I expect it to have to restart frequently.       

Any idea why this is happening?   I'm not a complete ubuntu noob (I use it for my main computing)  However, I'm not at all an expert.  Any suggestions on where to look to find the problem would be appreciated.  

Thanks much for your time.

---

### Post by blm-ubunet on 2016-05-17
Mythbackend is normally started as a daemon service & runs as user "mythtv".
It is started automatically.
If you start the backend as other "user" the config.xml file path is different.
Started as root the search path /home/root/.mythtv/config.xml shoud fail & then /etc/mythtv/config.xml (from memory) is used.


In 14.04 it is started by upstart:
sudo initctl [start|stop|restart|status] mythtv-backend
In 16.04 systemd (I believe)
sudo sysctl start mythtv-backend ??

Mythbuntu adds some script wrapper (around real program) for auto restarting.

User "mythtv" has to be a member of various groups to access/control stuff.

HDHomerun is an external networked tuner device?

---

### Post by alforddm on 2016-05-18
> **blm-ubunet said:**
> Mythbackend is normally started as a daemon service & runs as user "mythtv".
It is started automatically.
If you start the backend as other "user" the config.xml file path is different.
Started as root the search path /home/root/.mythtv/config.xml shoud fail & then /etc/mythtv/config.xml (from memory) is used.


It is started automatically upon restart and mythfrontend finds mythbackend.  However, It doesn't record or allow you to watch live tv.    I then have to "sudo killall mythbackend" and "sudo mythbackend" and everything starts to work.  

> In 14.04 it is started by upstart:
sudo initctl [start|stop|restart|status] mythtv-backend
In 16.04 systemd (I believe)
sudo sysctl start mythtv-backend ??


I don't know I just use the command "sudo mythbackend" to start it.   [/quote]
 
> 
HDHomerun is an external networked tuner device?

Yes, I have it connected directly to the laptop via the Ethernet port set as a local only.  The laptop accesses the internet via wifi.

---

### Post by alforddm on 2016-05-23
I'm still trying to solve this.  I finally figured out it has something with mythtvbackend not finding the hdhomerun tuners.  I don't have to start with sudo just shutdown mythtv and restart the backend and then everything works.  

How do I delay the starting of mythtv so that the tuners have a bit of extra time to initialize?

---

