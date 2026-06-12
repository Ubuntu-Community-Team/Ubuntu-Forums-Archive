---
title: "Network connections shows red x but can ping"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by keevill on 2009-11-02
I have a machine running Ubuntu 9.0.4 which is hardwired to the lan.
The network connection manager icon shows a red x.
I open it and it doesn't show any etho connections.
I can open ifconfig and it correctly shows the 192.168.0.114 ip address.
ip route show default also shows the correct local DG.
I can ping all the internal ip addresses but I cannot access the Internet.
Is there a way to reset the network connections ?
Clearly something is hosed here and I am struggling to solve it.

---

### Post by keevill on 2009-11-02
update....
I installed another network card and rebooted.
Lo and behold the network icon showed all ok.
Since this machine needs to be a fixed ip, I went in to edit the connections and tried to give manual ip and dg etc.
When I tried to save it I got an error something like ' Message Bus Timeout'
Now I am back with a red x on the icon.
I can still ping locally and dg seems ok but it's very strange.No Internet access of course.
Seems I need to totally clear the network settings and start again.
I know how to do in Win but not Linux.
Can someone run thru the procedure for me ??
Thx,

---

### Post by keevill on 2009-11-03
Solved !
I went into etc/networks/interfaces and deleted it.
Then when the machine rebooted it had restored the interfaces file and all is now well.
-keevill-

---

### Post by shredder12 on 2009-11-03
May be I am a bit confused but it seems rather weird to me that on changing network settings through network manager /etc/network/interfaces files gets modified. 
This is because Network manager doesn't save the settings in /etc/network/interfaces anymore it saves the settings somewhere in .gconf/system/
I don't know how your /etc/network/interfaces file got changed.

---

