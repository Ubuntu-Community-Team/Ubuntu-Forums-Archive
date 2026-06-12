---
title: "Connection loss"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by chkneater on 2011-03-11
Hi, I was a victim of the ubiquitous packet loss/connection drop problem that plagued 9.04 for quite a while until I believe compat-wireless-11-24-2010 fixed it temporarily.  I got much better connection with it, so much so that I was a able to make a complete upgrade before connection loss!!  Now with 9.10 I've come across a similar issue.

At start up wicd wants to accses dbus but I have to cancel it because NM is trying to connect right away and when wicd and nm are runinng things go haywire and it's hard to fix, so I have to cancel Wicd at startup, turn off wireless interface with the nm-applet, restart the wicD daemon with the terminal and before I even open the wicd gui I usually have already gotten a strong connection.  So I open wicd and of course I either have a signal or a choice of connections. In terminal I always run this to try to get better signal and transfer:

sudo iwconfig wlan0 txpower 0dBm
sudo iwconfig wlan0 bit 48M
sudo iwconfig wlan0 rate 48M

I was getting real good connection times but I'm still getting droppage and it's getting worse.  My question is are any of the newer compat-wireless packages worth trying?  I haven't heard anything about them because I cant keep connectino long enough lol!

---

