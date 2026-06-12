---
title: "ssh/ping time out"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by Vanish00 on 2011-01-16
I have two computers I want to interchangeably use SSH.  I have one Desktop and one laptop.  Both are using ubuntu 10.10 and openssh-server installed.

Desktop: wired to router
Laptop  : wireless to router

My Desktop can ssh/ping my laptop without problems however my laptop on the other hand cannot do either one.  The error I always get when I attempt to use ssh is "Connection timed out".  When I try to ping I get a 100% packet loss.  I've checked /etc/ssh/sshd_config and it's listening on port 22.  I feel like my Desktop is somewhere blocking or not allowing anything in.
Any Suggestions?

---

### Post by cipherboy_loc on 2011-01-16
Install nmap (`sudo apt-get install nmap`) and run:

```

nmap localhost

```

and see if it shows port 22 as being open. Also what is the output of:

```

/etc/init.d/sshd status

```



Thanks,
Cipherboy

---

### Post by Vanish00 on 2011-01-16
```
nmap localhost
```
Output:
Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-01-16 20:08 PST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00076s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.08 seconds

```
/etc/init.d/ssh status
```
Output:
*sshd is running

To me seems like everything is what it should be.  What do you think?

---

### Post by cipherboy_loc on 2011-01-17
Just for clarification, this was run on the laptop right?

There are a couple of things I am thinking about as possible ideas:

1) On the desktop, SSH is not configured properly.
         Ideas on how to diagnose: Run nmap from the desktop on localhost and see if ssh is running. Also run it on the ip address of the desktop proper (rather than on localhost, run it on 192.168.1.42 for example). When you run it, you will want to remove the MAC address from the result before posting. The MAC address is in the following format:
00:11:22:33:AA:BB

2) On the desktop, iptables (or what ever firewall you use) is set to block the laptop. 
         Ideas on how to diagnose: If you know your laptop's private IP Address:
```
sudo iptables -L | grep -i 'lap\.top\.prv\.IP'
```
 where 'lap\.top\.prv\.IP' is the private IP Address for the laptop.

3) The laptop isn't really connected to the network:
Ideas on how to diagnose: From the laptop, can you ping the router? 

How many computers do you have on your network? Is your network just a router (+modem?), laptop, and desktop? Or is it more complex (with a couple of Windows computers, 3 Macs, a NAS, etc? ;) ). If it is more complex, you might want to make sure you are trying to SSH into the right box. 

Another thing to think about trying is from the desktop, SSH into the laptop, and from there try SSHing into the desktop again.


Cipherboy

---

### Post by Vanish00 on 2011-01-19
too many posts

---

### Post by Vanish00 on 2011-01-19
too many posts

---

### Post by Vanish00 on 2011-01-19
too many posts

---

### Post by Vanish00 on 2011-01-19
First off, appreciate all the ideas on resolving my problem :D

> **cipherboy_loc said:**
> 
1) On the desktop, SSH is not configured properly.
         Ideas on how to diagnose: Run nmap from the desktop on localhost and see if ssh is running. Also run it on the ip address of the desktop proper (rather than on localhost, run it on 192.168.1.42 for example). When you run it, you will want to remove the MAC address from the result before posting. The MAC address is in the following format:
00:11:22:33:AA:BB

From what I can see from the results below, it seems that my desktop SSH is configured properly.  What do you think?


:~$ nmap localhost //Below is the results of command
```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-01-19 12:12 PST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00049s latency).
Hostname localhost resolves to 2 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

```

:~$  nmap 192.168.1.106 //Below is the results of command
```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-01-19 12:16 PST
Nmap scan report for LinuxToy (192.168.1.106)
Host is up (0.00033s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

```


> **cipherboy_loc said:**
> 
2) On the desktop, iptables (or what ever firewall you use) is set to block the laptop. 
         Ideas on how to diagnose: If you know your laptop's private IP Address:
```
sudo iptables -L | grep -i 'lap\.top\.prv\.IP'
```
 where 'lap\.top\.prv\.IP' is the private IP Address for the laptop.

I haven't installed any specific firewall other than what was pre-packaged and it seems that I got iptables also.  


:~$ sudo iptables -L  //this is the output of first cmd and I did use the pipe "| grep -i 192.168.1.102" just wanted concrete to provide
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

> **cipherboy_loc said:**
> 
3) The laptop isn't really connected to the network:
Ideas on how to diagnose: From the laptop, can you ping the router? 

How many computers do you have on your network? Is your network just a router (+modem?), laptop, and desktop? Or is it more complex (with a couple of Windows computers, 3 Macs, a NAS, etc? ;) ). If it is more complex, you might want to make sure you are trying to SSH into the right box. 

Another thing to think about trying is from the desktop, SSH into the laptop, and from there try SSHing into the desktop again.

Finally, I have 3 desktops and 2 laptops that all connect to my network through the wire/wireless router.  The desktops are connect by wire & laptops wireless connection.

Desktop: 2 windows, 1 ubuntu
Laptop : 1 windows, 1 ubuntu

Now about the suggestion to connect to my laptop from my desktop.  When I posted my problem that was working just fine but in only one direction.  I attempted that again but now I get the msg of: "ssh: connect to host 192.168.1.102 port 22: No route to host"

So now it doesn't work in either direction.  of course did this with laptop to desktop SSH connection and got same msg: "ssh: connect to host 192.168.1.106 port 22: No route to host"

Before I had an error saying "Connection timed out" but now its changed to "No route to host".  So I need to define these route to the host, any ideas how to do that?

---

### Post by cipherboy_loc on 2011-01-19
Sorry, the first idea should have been for the laptop.
> echo $quote | sed 's/desktop/laptop/g'I agree that the desktop is configured properly, as far as the nmap results go.

What are the IP addresses for the laptop/desktop? 192.168.1.102 for the laptop and 192.168.1.106 for the desktop? 

The error about no route to host makes me want to thing the router is mis-configured. 
I would test that theory by turning off all your computers (desktops + laptops), turn on only the two Ubuntu boxes, and try to ssh into one. If that works (where success is defined by it NOT returning the "No route to host" error), then it was just your connection to the router. If that does not work, turn off the laptop and the desktop, and then the router. Wait the "magic" 10 seconds, and turn on the router. Wait until the router has stabilized (about a minute on mine), and then turn on only the Ubuntu computers and try again. Else, I don't know what else would be incorrect.


Hope that makes sense,
Cipherboy

---

### Post by Vanish00 on 2011-01-19
I used the nmap on laptop which looked to me that ssh was open just as the desktop was.  I restarted everything like you said and what do you know it works now.  I am able to use SSH to connect to either laptop or desktop, thanks for all the help!  \\:D/

---

