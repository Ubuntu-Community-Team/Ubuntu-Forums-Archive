---
title: "No automatic dsl-connection using pppoe after update to jaunty"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by NorthernForest on 2009-05-02
p, li { white-space: pre-wrap; }  Hello,
 
 After I updated to Ubuntu 9.04, the dsl - connection doesn't start automatically during boot-time, and i have to start it manually using sudo poff and sudo pon dsl-provider. I even reconfigured using pppoeconf several times, but it doesn't help. This is what plog says after succesful connecting:

May  2 13:15:26 micky-desktop pppd[3834]: Connected to 00:90:1a:a0:01:e6 via interface eth0
May  2 13:15:26 micky-desktop pppd[3834]: Using interface ppp0
May  2 13:15:26 micky-desktop pppd[3834]: Connect: ppp0 <--> eth0
May  2 13:15:27 micky-desktop pppd[3834]: PAP authentication succeeded
May  2 13:15:27 micky-desktop pppd[3834]: peer from calling number 00:90:1A:A0:01:E6 authorized
May  2 13:15:27 micky-desktop pppd[3834]: Cannot determine ethernet address forproxy ARP
May  2 13:15:27 micky-desktop pppd[3834]: local  IP address 84.142.55.118
May  2 13:15:27 micky-desktop pppd[3834]: remote IP address 217.0.116.100
May  2 13:15:27 micky-desktop pppd[3834]: primary   DNS address 217.0.43.193
May  2 13:15:27 micky-desktop pppd[3834]: secondary DNS address 217.0.43.1

I'm not sure which other informations may be useful. The internet provider is called "T-DSL", and the modem "teledat 302".

---

### Post by un1 on 2009-05-03
I can confirm the problem, and here the fix (or workaround):

1. Open a terminal or konsole

2. Type: sudo nano /etc/dhcp3/dhclient.conf
(or use any othe editor you want, e.g. "sudo kate /etc/dhcp3/dhclient.conf")

3. find the place whith "interface-mtu" (line 23 at the end) and remove it with the comma! The line should then look like:

netbios-name-servers, netbios-scope,

4. Save and exit the editor (in nano: "ctrl+x" and then "y")

5. reboot


EDIT: The problem is: internet connection is set up correctly but without a DNS-server so the name resolution does not work...

one more problem with jaunty and networking.... :(

---

### Post by un1 on 2009-05-03
I reported a bug here: [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/371218](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/371218)

please look there for more information and maybe confirm it or add additional infos yourself!

---

### Post by Jean-Luc Daviau on 2009-05-03
Thanks for the work-around and for posting the bug: I had it also. Note: Work-around required shut-down/power-off/reboot (restart did not work).

Unfortunately the work-around did not work for users on the same computers: only the administrator (me). 

After reboot I can use the internet automatically and the config file  shows the modifications suggested in the bug-fix. :confused:Perhaps the bug-fix wizards will find a solution.

---

### Post by ayonkhan on 2009-05-03
> **un1 said:**
> I can confirm the problem, and here the fix (or workaround):

1. Open a terminal or konsole

2. Type: sudo nano /etc/dhcp3/dhclient.conf
(or use any othe editor you want, e.g. "sudo kate /etc/dhcp3/dhclient.conf")

3. find the place whith "interface-mtu" (line 23 at the end) and remove it with the comma! The line should then look like:

netbios-name-servers, netbios-scope,

4. Save and exit the editor (in nano: "ctrl+x" and then "y")

5. reboot


EDIT: The problem is: internet connection is set up correctly but without a DNS-server so the name resolution does not work...

one more problem with jaunty and networking.... :(
Didn't work for me. :(

---

### Post by un1 on 2009-05-03
maybe it is not a DNS error for you? can you try to ping e.g. google.com and if it doesn't work ping 209.85.171.100 (it's google.com's IP).

Can you also try if "sudo ifdown dsl-provider" and after that "sudo ifup dsl-provider" is successful!

---

