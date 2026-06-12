---
title: "loading pppoe after all processes"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by expatCM on 2010-04-22
I just got lost. I have set up a server with two nics. eth0 for the lan and eth1 for the Internet. I have dhcp running on the server. I am using adsl and have run pppoeconf to set up my connection. I have turned off dhcp and nat on the router so the device works as a modem using bridge mode.

The problem I have is that the server keeps hanging when loading pppoe or at least when pppoe has completed getting the public DNS addresses.

What happens is that the Internet connection can be opened from the /network/interfaces file. This seems to work but it does not return control to the server - the process runs, the DNS addresses obtained but the rest of the processes following at start up never load (i.e. power on the server and the processes that load then).

So I thought that this must be in the wrong place. I commented out the items in the interface file and added a couple of entries to end of rc.local, my logic being that this will load after everything has finished. Nearly right but not. What happens is that all processes run and then the pppoe program runs and the DNS addresses obtained (seen from a screen connected to the server). But the system then stops. What should happen is that it continues to load and at the end return the login prompt.

From a client I can see that dhcp has loaded since a private IP has been allocated but I cannot login from that client since the server has not finished loading.

I am not sure what I have not done here since reading round I can see that what I have followed is the same as everyone else but I get a different result.

Has anyone experienced this before or know what to do to fix this?

---

### Post by expatCM on 2010-05-01
I have managed to solve this using a program called Monit.  Monit is in the repositories and really worth taking a look at.  There is even quality documentation ...  ok so you have to read it but it is well set out.

I added the following 
> 
# check pppd
check process pppd with pidfile /var/run/ppp0.pid
 start program = "/usr/bin/pon dsl-provider"
 stop  program = "/usr/bin/poff dsl-provider"

# internet test
check host internet with address [www.google.com](www.google.com)
    if failed icmp type echo count 5 with timeout 30 seconds
        then exec "/usr/bin/killall -9 pppoe pppd" 
to the monit configuration file and for me this has solved the problem very well.

---

