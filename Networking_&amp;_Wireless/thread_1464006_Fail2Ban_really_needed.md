---
title: "Fail2Ban really needed?"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by robbied on 2010-04-27
I started playing with SSH mostly for fun then once I got the hang of it I was going to start actually using it.

I go it working I think so I went to security next.
I changed the default port (just to prevent bot attacks)
I disabled root login
I installed fail2ban

This is my problem.  Do I really need it?  I ask for this reason:

If I try to SSH into one of my machines I get connection refused (actually maybe a timeout message...forget) so I use firestarter to add an exception for my machines.  This lets me use SSH fine.  What's the point of fail2ban if the firewall disallows connections unless specifically allowed?

The other problem is I can't test the security.  When fail2ban "bans" the ip it actually doesn't because firestarter has added an exception for the ip address.

So do I need fail2ban and why?

---

### Post by rory526 on 2010-04-27
Perhaps it would be useful if an attacker had gained access to a trusted machine but did not know the password for the computer on which fail2ban is installed? It could ban that ip address until you would have time to sort the situation out. 

I'm unfamiliar with both firestarter and fail2ban. 

Does fail2ban change the firewall rules in /etc/iptables.rules and firestarter then use these rules?

If that is the case, then the bans should be added to this file above the exceptions allowing trusted ip addresses access, if that could be configured.

You might prefer using iptables firewall. It might offer more control than firestarter (but I don't know not having used firestarter).
[HTML]https://help.ubuntu.com/community/IptablesHowTo[/HTML]

---

### Post by robbied on 2010-04-27
*You might prefer using iptables firewall. It might offer more control than firestarter (but I don't know not having used firestarter*

FireStarter is a gui for iptables and fail2ban uses iptables to block specific ip addresses.

So if I am getting you right then;

*I don't need fail2ban really if my firewall is blocking all requests on the port I'm using. 
*I'm not worried about a trusted address brute forcing... my laptop isn't on that much nor is it always online.  I check logs often enough to probably catch an attack.
*iptables automatically blocks port#****** disabling ssh connections unless iptables (using firestarter) has an exception

Sorry but I would kick my own butt if I let some kid root my box... probably just healthy paranoia.

---

### Post by 2hot6ft2 on 2010-04-27
You should setup keys for logging into ssh instead of passwords.
Fail2ban blocks IP Addresses after they attempt to connect unsuccessfully 3 times in a given time frame for example. It does it by adding them to the deny.hosts file not the iptables. I installed it then removed it.
If an attacker wants in they will spoof another ip address and keep having at it until they get in.
I would suggest simply using keys it will take them years to crack it unless they're real good.
They will quickly move on to an easier target before wasting their time with yours.

Installing OpenSSH
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

I wanted stronger keys so I followed this for the keys
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

Port Lists
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html](http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html)

And set a non-standard port the higher the better somewhere in the 50,000-65,000 range.
And if you opened a port for ssh in firestart then it's open. Not blocked.

---

### Post by robbied on 2010-04-27
Interesting, what I read said it used iptables to block but you're right.  I looked into it and sure enough... Oh, it's not like I had to tell you that you are right, thinking with my fingers.

You are dead on about just spoofing new Ip's until they get it... Did not think of that.  Man, that makes fail2ban about useless if they just keep making new ip addresses.. :( Damn.

As for the key instead of passwords I had read about it and planned on getting to it, just taking it easy for starters.  Keys makes it damn hard to get access like you said.

For opening a port in firestarter, I only allowed 192.168.0.12 (my fake machine adress) to bypass the firewall on that port.  Only they get to access that port.  **Is that a security problem?**

I'm already using a really high port.

Thanks Everyone!!! for your super fast and clear support. Love the forums!

---

### Post by 2hot6ft2 on 2010-04-27
> **robbied said:**
> 
For opening a port in firestarter, I only allowed 192.168.0.12 (my fake machine adress) to bypass the firewall on that port.  Only they get to access that port.  **Is that a security problem?**

That's a lot safer than having it open to the world but a LAN IP can also be spoofed although it's rare since they would pretty much have to know it's there before they would go thru the trouble.

I connect to my desktop with my laptop when I'm away and keys are the wat to go. Use RSA and read the page for the keys I linked to before running the commands because it starts off telling you to run one command then later it increases the strength by running it with an option.

And you're welcome.

---

