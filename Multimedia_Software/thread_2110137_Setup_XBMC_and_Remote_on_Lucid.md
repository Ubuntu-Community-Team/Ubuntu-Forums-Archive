---
title: "Setup XBMC and Remote on Lucid"
date: 2013-01-29
forum: Multimedia Software
---

### Post by arvin555 on 2013-01-29
I would like to share my "ordeal" with setting up my XBMC to be remotely controlled by my Android Smarphone on Lucid.  

Couldn't really get much help after several days of google searches and stumbled on how to do it from bits and pieces from forums.. here goes:

1. I installed XBMC using this repository:
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)  
Keep in mind I am hard headed and still using Lucid Lynx, if you upgraded to newer Ubuntu versions, you will probably have an easier time installing the latest XBMC version.  Mine is XBMC 11 Eden.

2. Installation was straight forward, but I have noticed some slow down/lagging when using XMBC (no thanks to my slow PC processor), also I have had some crashes when accessing my goflex network drive.  

3. I was told that I can control XBMC from my android smartphone using several software that you can download from google play, so I downloaded one, tested, didn't work, so I ended up with 3 apps and all didn't work.

This is how I finally got it to work:

a. Setup XBMC as suggested by XBMC forums and wiki:
Allow control of XBMC via HTTP 
Allow programs on this system to control XBMC 
Allow programs on other systems to control XBMC
Change port to 8080 while you are at it.
b. Check the IP address of your computer on XBMC by accessing /System/Systeminfo  write it down for late use.

b. If you haven't done so, download the remote control app into your Android or IOS smartphone.  XBMC remote, Yatse and the likes.  

c. While downloading and installing, go back to your PC and get the firewall to allow access to ports 8080 (for the interface) and 9777 (for remote function)  To do this open a terminal and paste the commands below:

sudo ufw allow 8080
sudo ufw allow 9777

e. Then setup the remote control app on your smartphone, make sure Wifi is turn on, then enter setup,  the IP address is the IP that you got that you got from XBMC systeminfo  and then using 8080 as port.

f. If you do all of the above, you should be able to access the files/library and control your XBMC running in Ubuntu with your smartphone.

I strongly suggest that you only use Wifi only to control XBMC, don't use the internet for remote function for security reasons.

Hope this helps. 

TTFN
Arvin

---

