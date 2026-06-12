---
title: "Remmina can't connect to MS Server 2003 machine"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by jamesd3rd on 2013-05-08
I recently installed 13.04 on an oldlaptop and for the most part it does what it's supposed to do .  Onesnag I ran into was using the RDP client Remmina to connect to a MSServer 2003 machine. No matter what I do, I keep getting the messagesaying 'could not connect to rdp server______'.  One thread I foundsaid change the security setting in advanced to RDP.  That didn't doanything.  I tried the other options but that didn't do anythingeither.  Another said to delete the problematic server from theknownhosts file in the /freerdp directory.  But I have no such fileanywhere.


I opened port 3389 (the Windows remotedesktop port) on my router and that did nothing,  I uninstalledRemmina and installed it again and still no change.  I turned off thefirewall on the server; no change.


I'm new to Linux and I thought thingsjust worked.  Since I'm unfamiliar with it, it will certainly keep mybrain busy.


Any help the gurus or anyone else canprovide would be great.


Thanks,


James

---

### Post by steeldriver on 2013-05-08
Can you confirm you are able to connect from a Windows remote desktop client?

You can install nmap or telnet on the Ubuntu box and probe for the RDP port on the remote server e.g.

```
$ nmap -p 3389 192.168.1.4
    
    Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-05-08 09:13 EDT
    Nmap scan report for 192.168.1.4
    Host is up (0.092s latency).
    PORT     STATE SERVICE
    3389/tcp open  ms-term-serv
    
    Nmap done: 1 IP address (1 host up) scanned in 1.69 seconds

```

or

```
$ telnet 192.168.1.4 3389
    Trying 192.168.1.4...
    Connected to 192.168.1.4.
    Escape character is '^]'.
```
(it will time out if the port is not open)

If both machines are on the same LAN, then it shouldn't be necessary to open 3389 on the router - however it may be necessary to open it on the Windows firewall. I don't know about Server 2003 but if it's anything like Win7 then it can be tricky to get things right - for example I found I needed to open the port for 'Public' networks as well even though both machines are on the same private 192.168.1.0/24 LAN IP. 

On Win7 it is also necessary to add the connecting user to a whitelist ('Select Users')

---

### Post by jamesd3rd on 2013-05-08
> **steeldriver said:**
> Can you confirm you are able to connect from a Windows remote desktop client?

You can install nmap or telnet on the Ubuntu box and probe for the RDP port on the remote server e.g.

```
$ nmap -p 3389 192.168.1.4
    
    Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-05-08 09:13 EDT
    Nmap scan report for 192.168.1.4
    Host is up (0.092s latency).
    PORT     STATE SERVICE
    3389/tcp open  ms-term-serv
    
    Nmap done: 1 IP address (1 host up) scanned in 1.69 seconds

```

or

```
$ telnet 192.168.1.4 3389
    Trying 192.168.1.4...
    Connected to 192.168.1.4.
    Escape character is '^]'.
```
(it will time out if the port is not open)

If both machines are on the same LAN, then it shouldn't be necessary to open 3389 on the router - however it may be necessary to open it on the Windows firewall. I don't know about Server 2003 but if it's anything like Win7 then it can be tricky to get things right - for example I found I needed to open the port for 'Public' networks as well even though both machines are on the same private 192.168.1.0/24 LAN IP. 

On Win7 it is also necessary to add the connecting user to a whitelist ('Select Users')

I can connect from my XP computers with no problems.  Opening the port on the router while unnecessary was me just grasping at straws.  With Server 2003, just enabling Remote Desktop creates an exception in the firewall for port 3389.  But I even turned off the Windows Firewall.

Should I get no results when I try your suggestions, what should I look for next?

---

### Post by jamesd3rd on 2013-05-08
Just an update.  Nmap reveals the host is up and the port is open.  I wonder if there is something funky about the Remote Desktop service itself?

---

### Post by QIII on 2013-05-08
As a *temporary *check, try setting the account you are using to log in to an administrator and try that.

Remember to set it back to its current state!

---

### Post by jamesd3rd on 2013-05-08
> **QIII said:**
> As a *temporary *check, try setting the account you are using to log in to an administrator and try that.

Remember to set it back to its current state!

It is an admin account.  Since I'm the only user and it's my home network, that's not a problem.  What I might do is see if I can connect to one of my other XP units.  If I can, then I know it's Server 2003 that has the problem.  If I can't then there's something else going on.  If I had another Linux distro to try, that might narrow things down more.

---

### Post by jamesd3rd on 2013-05-09
I think I solved it.  For now anyway.  I replaced the WINS name with the IP address of the server in Remmina and the connection went right through.  I can either stick with this or edit the Ubuntu equivalent of the Windows lmhosts file or set up a WINS/Netbios server.

---

