---
title: "Forwarding network connections with Linux"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by nkae100 on 2011-03-11
How can I forward incoming connections on port 80 to another IP address? I think its done with 'iptables'?

---

### Post by Charlietje on 2011-03-11
It's done with iptables.
But first you need forwarding enabled:

```
echo "1" > /proc/sys/net/ipv4/ip_forward
```


And then you will need a forwarding rule to allow the packet to now traverse the forward chain:


```
iptables -A FORWARD -p tcp -i INTERNET --dport 80 -d 192.168.x.xx -j ACCEPT
```

---

### Post by nkae100 on 2011-03-11
Fantastic dude! Thanks for that!
Its really going to help because I am running a mail server in a Windows virtual machine and this will help making it reachable to the outside world.

> echo "1" > /proc/sys/net/ipv4/ip_forward

What does this code do exactly? Is it actually necessary?

---

### Post by Charlietje on 2011-03-12
This enables routing.
It is a kernel setting. Routing is disabled by default.

---

### Post by nkae100 on 2011-03-14
I see. I have iptables routing port 25 > 2525 and 80 > 8080. Would this mean its already enabled and I can just ignore the first line? Also, does the commands you stated have to be entered every time the system boots?.. If thats the case I shall add it to that "rc" file '/etc/'.

---

### Post by nkae100 on 2011-03-15
This is what I currently have in rc.local at the moment: 
 
>  iptables -t nat -A PREROUTING -p tcp --dport 25 -j REDIRECT --to 2525 
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to 8080 

I had been running my SMTP server with WINE, as the SMTP server is a Windows-based program (MERCURY), but I cracked the shits with WINE and removed it, so now I am going to run my SMTP server in a Windows virtual machine which has a different IP address than the host IP. 
The virtual machine is setup and ready, I can successfully telnet my mail server 192.168.56.101:25 from host. 
 
What I want though is for my computer (the host) to redirect traffic on port 25 to 192.168.56.101:2525. 
 
 
Based on what I can understand from what seems to be a thousand page, really, REALLY confusing iptables manual, I tried the following command, but it failed. 
 
>  iptables -t nat -A -p tcp -s 10.1.1.3 -j -d 192.168.56.101 

The problem I can see with the command above is that it fails to include instruction for ports. 
 
So, from an educated guess I tried this: 
 
>  iptables -t nat -A -p tcp -s 10.1.1.3 --dport 25 -j -d 192.168.56.101 --dport 2525 

... and this: 
 
>  iptables -t nat -A -p tcp -s 10.1.1.3:25 -j -d 192.168.56.101:2525 

... but these didn't work either. 
 
 
What I'm after is the magic iptables command. Could you please help me with it?

---

### Post by nkae100 on 2011-03-16
Can someone PLEASE help me with this issue!

---

### Post by HermanAB on 2011-03-16
Howdy,

Note that the rules are evaluated top down and -A will add a rule to the bottom of the list, while -I will insert a rule at the top of the list.

Since you were using -A, there may already be a rule above it that takes effect causing your new rule to not get evaluated.

Soooooo, maybe flush all rules with -F before you start.

---

### Post by nkae100 on 2011-03-16
Unfortunately I didn't understand you.

---

### Post by nkae100 on 2011-03-16
Look its a straight forward question. Can someone just answer it without critizing my ways to doing things... PLEASE!



Ok... I had been running my SMTP server with WINE, as the SMTP server is a Windows-based program (MERCURY), but I cracked the shits with WINE and removed it. Now I am running my server in a Windows virtual machine.
 
This virtual machine has a different IP address from my host machine, so what I need is for my computer (the host) to redirect incoming traffic on port 25 to the virtual machine at 192.168.56.101 on port 2525.
 
Can someone please help me with it? I think its done with iptables.

---

### Post by viperce on 2011-03-16
So the incoming traffic on port 25 is on your windows machine? and you want it to forward your traffic on port 25 to port 2525 which is on your virtual machine?
is that correct?

---

### Post by nkae100 on 2011-03-16
Nah, the incoming traffic is on my Linux machine ([10.1.1.3]) and I want it to be fowarded to my Windows machine [192.168.56.101].


Here is my network setup:

[WAN] > [MODEM] > [10.1.1.3] > [192.168.56.101]

---

### Post by dmizer on 2011-03-17
You seem to be going about this the extra hard way. If you're running Windows in a virtual machine:

1) Check your Modem (which is also a router) to see if it can assign permanent IP leases based on MAC address. If it can't, then your only option is to change to static IP isntead of DHCP.
2) Change your Windows virtual network adaptor to bridged instead of NAT. The virtual server's NAT can interfere with your attempts at routing.
3) Make sure that your virtual Windows is getting a 10.1.1.x IP address.
4) Configure your ISPs modem for port forwarding to your virtual Window's 10.1.1.x IP.

If you do not have access to the modem's config page, then you cannot host an email server on your network.

---

