---
title: "Getting kicked off of SSH session (No route to host)"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by shnomin on 2012-04-18
Hello,

I am having a problem while ssh-ed into a machine on a local wireless network.  Everything works normally until I have been working on the machine for about 2 hours or so, then I will get kicked off of my ssh session (Write failed).  When I try to reconnect, I get this error:

ssh: connect to host ***.***.**.* port 22: No route to host

Here's the tricky part;  When I physically go to the machine and plug in a monintor and keyboard, I can ping the outside world and other devices on the local network.  After I do this, everything else works again.  I am able to ssh into the machine.

The loss of connection is a big problem, however, as this machine is actually a robot and is generally roaming untethered.  It is very inconvenient and often impossible to have to hook it up to a monitor and keyboard.

Any help is greatly appreciated.  Thank you.

P.S.:
No entries in the iptables, so I don't think the firewall is an issue, and I don't think sshd is going down.

edit:  Also the machine is running 10.04

---

### Post by |{urse on 2012-04-18
In your sshd_config file, under the PAM section is 
 
> #TCPKeepAlive yes

 
enabled? (delete the # on that line and save it, if not) then issue a service sshd restart (or just reboot) and try it again.

---

### Post by shnomin on 2012-04-18
Thanks for the quick reply.  Unfortunately TCPKeepAlive was already enabled.  Also, it's not just ssh that fails when I get kicked off.  I can't ping the machine or communicate via any ports.  Once I hop on the machine physically and ping anything, everything is up again.

---

### Post by gradinaruvasile on 2012-04-18
What method is used to connect it to the rest of the network?
The issue you describe looks like the 3G connections dropping after some time of inactivity.
In your case you should check the dmesg output for wireless-relsted issues.

You can try putting a periodical ping command in a script or in cron, maybe it helps, but if you were working at that time, id check my wireless devices and drivers.

---

### Post by shnomin on 2012-04-18
It uses a wifi card.  The connection is handled by Network Manager.  It still shows a good connection when the error happens.  I'm not with the machine right now, but I'll try to reproduce the error and get dmesg output when I return to it.

---

### Post by shnomin on 2012-04-18
dmesg output shows nothing about any sort of network cards, wifi or otherwise.  Nor does the syslog.  I verified once more, that after the error occured: I started pinging with another machine.  Every ping attempt timed out with "host unreaachable", as expected.  On the machine in question, as soon as I pinged the router, the other machine's ping were succesful.  Is this a router problem?  One caveat about the wireless network:  The router is running a dhcp server with addresses starting at 192.168.10.100, but I have this machine set up manually using 192.168.10.1 as this particular router can't allot a static IP based on MAC address.  Could this possibly have anything to do with it?  Any help is appreciated, and thank you to the suggestions thus far.

---

### Post by strask on 2012-04-18
Just a random thought; could this be some sort of power management feature kicking in after a certain amount of inactivity on the keyboard or something? How consistent is the amount of time it works before failing?

---

### Post by shnomin on 2012-04-18
Very inconsistent.  Also, new data has arisen.  Ping from the affected machine was "solving" the problem before.  Now it is not.  Although the machine is connected the network properly and can access the internet, other machines on the network showed "no route to host".  Turning off/on wireless then "fixed" the issue.  Very odd.  I'm starting to think this may be a router issue.... I'm going to flash dd-wrt

---

