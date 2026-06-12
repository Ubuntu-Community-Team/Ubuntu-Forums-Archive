---
title: "Wireless Authentication"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by pybus on 2011-03-21
At the risk of posting an issue that I'm certain has been asked several times before...

I am new to Linux, and after installing 10.10 on my desktop, I have struggled with installing my Netgear WG111T Wireless adapter.

After following several tutorials I have finally managed to get the thing up and running, it can detect my local network, however constantly asks for Authentication (WPA).

I have tried un-securing my network, but the adapter still fails to connect.

I'm sure this has been asked before, with Ubuntu getting caught up on connecting, but none of the workarounds I have found have helped. So I thought I'd try here.

I'm not sure what information you need to assist, but I'd be happy to post it, (I'm just not sure which commands I'd need to input to get it running. ^^

Thanks a bunch.

P

---

### Post by bobpress on 2011-03-21
Don't know if this is your problem, but you may need to make your network "Connect automatically" on the Connection Editing page for your wireless network.

Right click on the tray icon, choose "properties", then "configure", select Wireless and then your network (use edit).  If your network is not there yet, Add a network and enter the name of your network and password under wireless security settings.  Select "connect automatically" and also select "available to all users", if you don't want to be asked for your admin password each time you start your computer.

---

### Post by pybus on 2011-03-21
Thanks for the help. But that doesn't solve the authentication problems, I can post ifconfig or iwconfig etc. if needed?

---

### Post by PCNetSpec on 2011-03-30
How did you install the drivers for your WG111T... ndiswrapper?

if so, see here:
[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572)

---

