---
title: "Determining TCP/IP services available"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by Quick99 on 2012-11-28
This might be a bit of an unusual question, but it is for my homework.

"Determine the set of TCP/IP services available on <hostname>"

The hostname is an actual server that I have access to and it is running linux. I am not really sure how to go about this?

Thanks.

---

### Post by haqking on 2012-11-28
> **Quick99 said:**
> This might be a bit of an unusual question, but it is for my homework.

"Determine the set of TCP/IP services available on <hostname>"

The hostname is an actual server that I have access to and it is running linux. I am not really sure how to go about this?

Thanks.


do you mean what services are running that use TCP/IP (which will be anything that uses the network)

or do you mean a simple portscan ?

you can use

```
netstat -a
```or install nmap with

```
sudo apt-get install nmap
```then type

```
nmap -v -sT localhost
```This will list the ports and service names using them (-v means verbose so gives you the service name) such as 53 for DNS 139 for Samba etc etc

Is this what you mean ?

---

### Post by Quick99 on 2012-11-28
I tried nmap from my personal ubuntu machine because I can't install stuff on the target machine. nmap found a few ports, but it also failed to find a port that I know is open. I know that port 25 (SMTP email port) is open because I can connect to it with telnet. I ran nmap with the settings:
```
nmap -v -sT -NP <hostname>
```
-NP because nmap suggested that I do so.

nmap also says that 966 filtered ports are not shown. A quick google tells me that this means I am being blocked by some sort of firewall or something. I am not really sure what to do now. I guess I could keep on manually connecting to likely ports using telnet, but that takes awhile...

---

### Post by Quick99 on 2012-11-28
For anyone who stumbles upon this via a google search, I ended up going with this command:

```
head -400 /etc/services
```

It generates a very long list of all of the services and their ports. (TCP and UDP)

---

### Post by bab1 on 2012-11-28
> **Quick99 said:**
> For anyone who stumbles upon this via a google search, I ended up going with this command:

```
head -400 /etc/services
```

It generates a very long list of all of the services and their ports. (TCP and UDP)

That's a list of all services that *might* use those ports.  It does not tell you what is actually running on any particular host.


If want to see what services are actually being use you might try this at the host in question```
netstat -ntlpu
```

This is what I get```
sudo netstat -ntlpu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      940/smbd        
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      940/smbd        
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      1186/hddtemp    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      948/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1216/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      948/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1216/cupsd      
udp        0      0 0.0.0.0:35750           0.0.0.0:*                           987/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           987/avahi-daemon: r
udp        0      0 192.168.1.3:137         0.0.0.0:*                           953/nmbd        
udp        0      0 0.0.0.0:137             0.0.0.0:*                           953/nmbd        
udp        0      0 192.168.1.3:138         0.0.0.0:*                           953/nmbd        
udp        0      0 0.0.0.0:138             0.0.0.0:*                           953/nmbd        

```

Just to be clear here; you need to do this at that host's CLI (terminal).

---

### Post by JKyleOKC on 2012-11-29
And if you omit the "n" from the string of options, you'll get the service name instead of just the port number for each one, which is probably what the instructor wants to see...

---

