---
title: "Network card recognized, but no connection"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Bonzai11 on 2009-08-30
This morning I got bored of Arch linux and decided to go back to Ubuntu.
After the install as always everything works, but my ip was dynamic and I want it set for port forwarding.
Well went to a few online guides did some changes to /etc/network/interfaces
namely telling eth0 to use ip x.x.x.99 setting up gateway etc.
Did etc/init.d/networking restart to enact the changes. reconnects and voila x.x.x.99.
But then I saw my updates had finished so shut everything down and restarted.
Then after boot I was greeted with a wireless bar on my panel. Which was odd because I don't have wireless it is wired from a extender, then I go to look at the connections only Auto eth1 is there.
Well I want to use eth0 I could switch it, but I want to fix the problem.
 
Its recognized by ifconfig, but oddly there is another item in ifconfig eth0:avahi.
May be I don't know how to properly set up a connection, but I need some help.
 
SOLVED: Can someone close this.
I Unplugged the ethernet plugged it back in and was able to restart networking and its going now but the tray applet say differently.
I dont need the applet anyway going to uninstall it and but network-admin-tool instead.

---

