---
title: "Transmission port closed,"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by dehyde on 2009-04-04
Greetings...

I tried using Transmission but it keeps telling me that the port is closed. Ive tried several things:

1. Checked ifconfig for my ip, then redirected the port in my router to that ip adress. [COLOR="Gray"](Since port redirection worked fine on my other computer it doesn't seem to be a router problem)[/COLOR]
2. Checked that the port is open in my Ubuntu using port scan, and checked my private IP.
3. Checked ufw... not loaded.
4. tried this command: sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

Eveything i've tried so far didn't seem to help and I cant find the problem.
Any help would be greatly appriciated.

---

### Post by awfeucht on 2009-04-12
I'm having a similar problem, and I'm just not sure where to go from here. These are the steps I've taken so far:

1. Checked IP using ipaddr (.02)
2. Forwarded ports 40000-40010 to ip .02 on my router
3. Downloaded gufw and added port 40009 and transmission to it's allowed services.
4. Gone into System > Administration > Login Window and deselected "Dency TCP Connections to XServer"
5. Changed listening port on Transmission to 40009.

Testing the port still shows it closed, and my download speeds reflect that.
I have also tried:
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 40009 -j ACCEPT
```
and gotten nothing. Not sure where to go from here. It doesn't appear to be a Transmission-only problem, I've installed Deluge and gotten the same "Port is Closed" message using the same ports. Any help would be appreciated.

---

### Post by awfeucht on 2009-04-12
I have completely disabled ufw:

```
awfeucht@Radiohead:/usr/share/man$ sudo ufw status
[sudo] password for awfeucht: 
Status: inactive

```

and still get the same message on Transmission and on online port scanners saying that the port is closed or not responding. Nothing has changed in my router since yesterday, when I had openSUSE running and it recognized the port as open. Transmission's listening port is set to 40000. I have opened ports 40000-40009 on my router for ip's 192.168.1.1-.4, and have 192.168.1.2 assigned to the ubuntu box. UPnp is enabled on my router. I'm not sure what the next troubleshooting step is.

I'm not really sure how to interpret all of this, but..
This is what I get when I do iptables -L:

```
awfeucht@Radiohead:/usr/share/man$ sudo iptables --list
[sudo] password for awfeucht: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:40000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:40000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:40000 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination
```

Again, thank you for any help, hints, suggestions or references.

---

### Post by vik_2010 on 2010-01-12
I'm a newcomer to linux, but here's my take:

I downloaded Transmission recently and began downloading my first file yesterday. I was having slow download speeds and did a lot of reading on different ubuntu forums.

Apparently, older versions of the os were completely locked down but the new versions are completely open: all one needs is a a server app listening at a certain port for it to open.

This hasn't been my experience. I downloaded firestarter since it seems to have the easiest gui to work with, and was recommended by others on the forums. The firewall gui kept telling me that udp packets were repeatedly being blocked for port 56527. So I opened the port  and my download started picking up.

Today I began my second download, and once again, udp packets were repeatedly being blocked, but this time they were to port 62531. So I added a new rule to my firestarter list.

I have no idea why Transmission keeps switching ports on me, since in Edit--> Preferences -->Web I set my incoming port to 56527. Regardless, it seems that Transmission uses different ports each time and disregards the input I provide to use a specific port.

Maybe that will help, but I could be completely off the mark.

---

### Post by aaronhahn777 on 2010-01-20
I just figured this out a while ago...

do exactly what you did > forward port from router using your Internet address (use "ifconfig" in the terminal if you know your computer's internet address). Then install a firewall gui.  I used something called firestarter (get it from the synaptic manager if you are running Ubuntu... system > administration > synaptic manager > mark "firestarter")

Now simply open the gui and press the "stop" button. This will turn off the firewall and it will no longer block your port forwarding.  Check transmission > edit > preferences > network ... select a port inside the forwarded range (from your router)...  and bingo.  "port is open".

I can't remember how to permanently set it to off.  You'll have to search around cause I can't remember.  Hope this helps.

---

### Post by heian on 2010-01-23
Hi,

i also got a problem with transmission 1.06,running on ubuntu 8.04

i'm sure a certain port is forwarded in my modem. i'm very used to forward ports, as i'm running a server.

but the strange thing is, transmisson keeps telling me that the port is closed... i don't have a firewall installed in ubuntu.

Had tried several different ports numbers, with no luck. Running out of ideas at the moment...

---

### Post by Unhyper on 2010-06-02
I am not using a firewall either, but Aaronhahn's trick worked beautifully for me. Thanks for posting it, Aaron.

---

