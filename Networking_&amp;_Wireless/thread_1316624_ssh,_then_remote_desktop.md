---
title: "ssh, then remote desktop"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by 80aless on 2009-11-06
Hi, 
I would like to ssh and use a remote desktop from my office to my home. I am afraid the network/ports/address are blocked. Here below some info's. ssh from home to office works fine with a 
The IP address at home is: 82.xxx.xx.xx, but in my notes I also see a 192.xxx.x.xx one. I suppose I have to try with the  the out-ward facing public Internet addresses, ie the 82.xxx.xx.xx?
```

ssh -X home@192.xxx.x.xx
ssh: connect to host 192.xxx.x.xx port 22: Network is unreachable
ssh -X home@82.xxx.xx.xx7
ssh: connect to host 82.xxx.xx.xx port 22: Connection timed out

```

Do I have to put this at autostart? ```
sudo /etc/init.d/ssh start
```
This one works in OFFICE (I do not know what it means though), at home I still have to try ```
ssh localhost
```

I scanned the home address with:
```
 OFFICE$ nmap -sT 82.xxx.xx.xx

Starting Nmap 4.53 ( http://insecure.org ) at 2009-11-06 09:50 CET
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.033 seconds
OFFICE$ nmap -PN 82.xxx.x.xx

Starting Nmap 4.53 ( http://insecure.org ) at 2009-11-06 09:50 CET
All 1714 scanned ports on 82-xxx-xx-xx.ip. [..] are filtered

Nmap done: 1 IP address (1 host up) scanned in 345.320 seconds
```

At home I went to System>Preferences>Remote desktop and I got:
[PHP]Your desktop is only reachable over the local network. Others can access your computer using the address 192.xxx.x.xx computername.local.[/PHP]
In the office I see [PHP]"Users can view your desktop using this command: vncviewer computername:0"[/PHP]

At home: 
```
netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN 
```
In the office:
```
netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:1025          0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:1026          0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:1027          0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      
```
In the office:
```
 sudo iptables -L -n 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Thanks, and please be patient

---

### Post by dvlchd3 on 2009-11-06
Ok, I'm a bit confused.  Are all of the outputs shown from your computer you are using to attempt to connect to your home server?

If so, can you run iptables -L on your home server.  If you have the OpenSSH server running on your home server, but iptables blocking the port to the outside world (which is usually smart) this would be the culprit.

---

### Post by 80aless on 2009-11-06
Thanks for your reply. Please note that I indicate before each output whether it was taken "In the office:" or "At home:". This evening I will try iptables -L at home. How can I see if iptables is "blocking the port to the outside world"? 
Open ssh is: ```
sudo /etc/init.d/ssh start
``` ? And do i have to add it at start up?
Cheers

---

### Post by dvlchd3 on 2009-11-06
My mistake.  I retract my previous post!

Check your sshd config file.

Us your favorite editor to edit /etc/ssh/sshd_config as sudo.

```

sudo vi /etc/ssh/sshd_config

```

Look for the line that starts with "ListenAddress"

Change this line to listen on *:22

Restart sshd

```

sudo /etc/init.d/ssh restart

```

This will allow you to connect from your work computer.

Didn't realize this value defaults to only listen on your local network!

---

### Post by 80aless on 2009-11-06
My /etc/ssh/sshd_config AT WORK is:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
[B]#ListenAddress ::
#ListenAddress 0.0.0.0[/B]
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes
...

```
I changed it to 
```
ListenAddress ::**22**
ListenAddress 0.0.0.0
```, is it ok? 
Still, after restarting sshd ssh cannot correct from work, neither with 192.* nor with the 82.* IP address.

---

### Post by 80aless on 2009-11-08
After changing both /etc/ssh/sshd_config files (in office and at home) to: 
```
ListenAddress ::22
ListenAddress 0.0.0.0
Protocol 2

```I get 
```
sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source 
```
At home:
```
netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::9666                 :::*                    LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 127.0.1.1:45114         :::*                    LISTEN 
``` In the office:
```
netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:1025          0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:1026          0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:1027          0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN 
```
```
ssh localhost 
```works with both computers.
I do not know what this information means. Any idea? Thanks.

---

### Post by dvlchd3 on 2009-11-08
Are you sure your company allows outgoing SSH connections?  Many network admins will not allow this for security reasons.  (My company does not allow it).  It appears your server is listening on 0.0.0.0:22.  Which I believe means it is listening for a connection from any ip on port 22.

You can try running a traceroute from work to your home server through port 22.  If you do not have traceroute installed, you will need to install it through your favorite method (i.e. - sudo apt-get install traceroute)

```

tcptraceroute -p 22 HOME_IP

```

If you notice it fails before it gets out the the Internet, it is how your office's network is configured.  If it fails once it reaches your home server, it is something we missed in your sshd configuration.

---

### Post by 80aless on 2009-11-09
Hi, 
I don't know if the company allows ssh (how can I find out?). I can tell you that it is possible to do ssh & remote desktop to my computer in the office and viceversa (I used to do it when I lived somewhere else).
I tried:
```
OFFICE:~$ sudo tcptraceroute -p 22 82.xxx.xx.xx
Sorry, requested local port is already in use.  Use -P, instead of -p, to override.
OFFICE:~$ sudo tcptraceroute -P 22 82.xxx.xx.xx
Selected device eth0, address 130.37.17.46, port 22 for outgoing packets
Tracing the path to 82.170.33.37 on TCP port 80 (www), 30 hops max
 1  router-staff1.few.vu.nl (130.37.16.1)  0.402 ms  0.269 ms  0.242 ms
 2  hkae16-2-d02.backbone.vu.nl (130.37.5.54)  0.256 ms  0.235 ms  0.228 ms
 3  GE5-1-1.2090.JNR01.Asd002A.surf.net (145.145.20.57)  0.586 ms  0.571 ms  0.569 ms
 4  AE0.500.JNR02.Asd002A.surf.net (145.145.80.65)  0.622 ms  0.630 ms  0.611 ms
 5  bcsw1.asd-tc2.tiscali.nl (195.69.144.78)  0.682 ms  0.671 ms  0.627 ms
 6  * * *
 7  * * *
...
30  * * *
Destination not reached

OFFICE:~$ sudo tcptraceroute -p 22 192.xxx.x.xx
Sorry, requested local port is already in use.  Use -P, instead of -p, to override.
OFFICE:~$ sudo tcptraceroute -P 22 192.xxx.x.xx
Selected device eth0, address 130.37.17.46, port 22 for outgoing packets
Tracing the path to 192.168.1.35 on TCP port 80 (www), 30 hops max
 1  router-staff1.few.vu.nl (130.37.16.1)  0.409 ms  0.363 ms  0.247 ms
 2  hkae16-2-d02.backbone.vu.nl (130.37.5.54)  0.249 ms  0.244 ms  0.230 ms
 3  GE5-1-1.2090.JNR01.Asd002A.surf.net (145.145.20.57)  0.572 ms !N  0.624 ms !N  0.566 ms !N
```

1)Still I do not know which IP address I must use, the 192 or the 82.
2)do I have to add the following at startup? 
```
sudo /etc/init.d/ssh start
```

---

### Post by fargle on 2009-11-10
Assuming the 192 address starts with 192.168, you definitely cannot use that address - 192.168 addresses are nonroutables that will not travel over the Internet, so use the other address.  If you want to be sure, visit "whatismyip.com" from the computer you're trying to get to.

---

