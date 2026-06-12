---
title: "Strange SSH time-out"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by chah on 2011-01-10
Hi all, I've installed Ubuntu amd64 on a SUN server in our lab. That network has ip address range 192.168.4.? There are other servers in the same lab running Knoppix, with the same ip addr range connected to the same router.

When we come out of the lab initially I can ssh to and ping all machines in the lab, both the Knoppix and the Ubuntu machines. (Outside the lab, we are on network segment 10.217.248.?). The Ubuntu machine however, locks up to SSH sessions from outside the lab after several minutes and does not respond to pings. 

Machines on the same network segment (the Knoppix machines, on 192.168.4.?) can ping and ssh to the Ubuntu machine without problem. And I can ping all the Knoppix machines from outside the lab. The only problem seems to be that after a certain period, usually after the screen saver has activated, the Ubuntu machine becomes inaccessible to TCP/IP from outside the lab, while the Knoppix machines remain responsive. Sometimes waking up Ubuntu from the screen saver re-enables ssh'ing and pinging the server. I disabled the screen saver, however now it doesn't wake up at all and I seem to be permanently locked out from 10.217.248.

It isn't just ssh that locks up. It doesn't respond to pings either. There's something wrong with basic TCP/IP, I feel.

I feel a likely culprit is the router, or firewall between the network segments (which I do not have control of and it would be troublesome to access). But then why am I still able to access the Knoppix machines on the same network segment as the Ubuntu machine? (in fact, this server running Ubuntu now, used to run Knoppix. It had the same IP address and the same hostname as now. I believe the IP address is configured in the IT departments DHCP server to assign the same IP address to this NIC's MAC address, so I get the same IP address as when it was booting Knoppix)

I want to try copying configuration files from the Knoppix machines to the Ubuntu machines until it works. Can anyone advise which files I should try copying?

Thanks for any help or suggestions

---

### Post by chah on 2011-01-10
A quick update. If I don't login on the server (I leave ubuntu at the login screen), then ssh seems to work fine from the computers outside the lab.

(Incidentally, I installed ubuntu-10.04.1-desktop-amd64.iso rather than ubuntu-10.04.1-server-amd64.iso on the SUN server and it has a GUI. I couldn't get the second one to install)

---

### Post by PatchesTheCaveman on 2011-01-10
Go to System > Preferences > Power Management and make sure your computer isn't configured to suspend.

If that isn't the problem, try running *nmap* against the machine when it stops working and see if it's responding to anything at all.

---

### Post by chah on 2011-01-14
I think I've found the cause this problem of connecting to the servers from outside the subnet. Our servers have 2 NIC cards, one is the usual one, and the other is for the service processor. Both NIC's are plugged into the same LAN (subnet). This essentially consumes 2 IP addresses per server from the subnet. I think that sometimes, the server was responding to IP addresses from one NIC and sometimes from the other. I'm not sure how Ubuntu should respond when it has 2 NIC's connected to the same LAN. In our case it was making connections from outside the subnet unreliable. We disabled the NIC for the service processor via network manager. I still believe it is tied to the screen saver or power management in some strange way, but anyway, now it's working.

---

### Post by chah on 2011-01-14
I think I've found the cause this problem of connecting to the servers from outside the subnet. Our servers have 2 NIC cards, one is the usual one, and the other is for the service processor. Both NIC's are plugged into the same LAN (subnet). This essentially consumes 2 IP addresses per server from the subnet. I think that sometimes, the server was responding to IP addresses from one NIC and sometimes from the other. I'm not sure how Ubuntu should respond when it has 2 NIC's connected to the same LAN. In our case it was making connections from outside the subnet unreliable. We disabled the NIC for the service processor via network manager. I still believe it is tied to the screen saver or power management in some strange way, but anyway, now it's working.

---

