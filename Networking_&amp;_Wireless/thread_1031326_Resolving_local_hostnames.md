---
title: "Resolving local hostnames"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by dswo on 2009-01-05
My Intrepid box is trying to join a network of Win XP Pro boxes. They are in a workgroup, but not a domain. Samba is installed and running. I can ping the other boxes by IP number, but not by name. 

- DNS is provided by my router, which also assigns IPs. 

- Internet works fine. 

- Using the IP number, I can access shares on the Windows machines from Ubuntu

- If I append .local to the hostname I am trying to ping, it is successful. (E.g., "ping hostname.local" works but "ping hostname" does not.)

- Resolv.conf has only one line, defining nameserver as my router's IP address

- In nsswitch.conf, hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

- If I "ping hostname" Linux seems to bypass my local system altogether and refer the request to my ISP's IP address and search the world. Since my hostname does not exist in my ISP's DNS records, it doesn't find anything and times out.

- If I issue "smbtree," it finds itself, but when it starts querying the next local computer on the net (-- somehow it does know the correct name!), it refers the request to my ISP's IP address again, times out, and returns "Error NT_STATUS_ACCESS_DENIED." I know that sounds like a permissions problem on the Windows machine, but I don't think it actually is, since if I navigate to my shares using IP address or "hostname.local" I _can_ access them. Might need to provide a user name and password, but I can access them.

What am I missing?

ADDED: One more datum. The Intrepid machine that I am trying to connect dual boots with Windows XP. If I boot with Win XP, I can "ping localhost" with no trouble.

ADDED 2: The network is peer-to-peer.

---

### Post by aag_ubu on 2009-01-06
You need that your resolv.conf file contains not only the name servers but also the following line:

search local

This will make the name resolution add the domain "local" to each host name. 

There are several ways to achive this, depending on how you are connecting to the network. 

- If your network has a DHCP server, you should be able to configure the server to do it for you (e.g. in DD-WRT's dhcp server you can set the seach domain that the clients will get). 

- If you are using a DHCP server but you can't change the configuration, then you will have to add the line to resolv.conf yourself. I am not sure, but I think that you can add a script into the /etc/network/if-up.d folder that adds the line to resolv.conf.

- If you are setting the IP manually, you just have to add the search domain in the DNS tab of the network manager.

---

### Post by Iowan on 2009-01-06
Installing Winbind and editing nsswitch.conf *previously* helped fix hostname resolution (in [here]("http://ubuntuforums.org/showthread.php?t=288534") somewhere), but a couple of threads  suggested a Winbind update broke it and name resolution worked better after Winbind was disabled. [Another]("http://ubuntuforums.org/showthread.php?p=6116350") thread to check.

---

### Post by umaxtu on 2009-05-07
How could I have been so stupid? 
For three years I've been trying to get printing working  on Ubuntu and turns out that all I needed to do was add one line in a file and get my dad to make me a user account for the domain.

---

### Post by rick71 on 2009-05-10
> **umaxtu said:**
> How could I have been so stupid? 
For three years I've been trying to get printing working  on Ubuntu and turns out that all I needed to do was add one line in a file and get my dad to make me a user account for the domain.


which line?

---

