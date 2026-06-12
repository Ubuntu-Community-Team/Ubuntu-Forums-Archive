---
title: "Problem joing Active Directory Domain with Likewise Open"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by jrusidoff on 2009-02-10
Hey geniuses!

Need a bit of help...

I am trying to join my Ubuntu 8.1 laptop to my work domain, which is a 2003 Server active directory domain.  I have downloaded and run Likewise Open, but I keep getting this message:
 Manual Configuration Required
The configuration stage 'open ports to DC'cannot be completed automatically.  Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted.  Please update your firewall settings to ensure that the following ports are open to 'my-domain-name.com':

88 UDP
389 UDP
464 UDP
88 TCP
389 TCP
445 TCP
464 TCP

The problem here is that all of these ports are open.  I only have one server on our small network, and the Windows firewall isn't even on;  The server isn't even the DHCP server.  The router is the DHCP server.  The Server itself is the primary DNS.

So...WHAT is it that I have to manually configure?  

Any help will be appreciated...the fate of the free (software) world depends on it!

Thanks, 

JimmyR

---

### Post by digitalbenji on 2009-02-10
Are you using the domainjoin gui or cli?  

The command you want is:
```
sudo domainjoin-cli join FQDN.DOMAIN.COM USER
```

Let me know what the output of that is

---

### Post by jrusidoff on 2009-02-10
Yes, I get the exact same message if I used either that command line or the GUI.

---

### Post by jrusidoff on 2009-02-11
:guitar::guitar::guitar:
Well...fixt!  Got to thinking just how my network is set up....the one server on here that I am trying to reach is the primary DNS server of the network...but it is not the DHCP server, on of my routers is.  I checked the DNS table and found the server address was not in there, so I edited my /etc/resolv.conf file...and the next thing you know, ol' Jed's a millionaire!

Still having some browsing problems, but think I can work that out.

Thanks to everyone here....found pieces of the answer all over the place.

---

### Post by filfish on 2009-03-05
Hi

I've got a bit of a problem with this too.

We're on a windows domain but we want to have a few Ubuntu desktops available, we can get the machine to register with the domain and users can then authenticate, but everytime the computer is restarted we have to log on with a local account and rejoin the domain again.

Is it possible to get the computer to rejoin at start up without having to log in every time?

Thanks

---

### Post by jrusidoff on 2009-03-05
My test machine "seems" to join the domain at every startup.  I say "seems" because when I go into System/Administration/Active Directory Membership it says I am joined to the domain.  BUT...to get to any files/folders on the Windows 2003 Server, I have to go to Places/Connect to Server and choose Windows share from the drop-down menu.  ONce I find my share, I'm in until I shut down the Ubuntu computer. 
One thing I think is related, but don't know why just yet, is when I log on to the Ubuntu machine, after I put in my password, I have a box that pops up saying "No Login Servers" I just click OK and my desktop starts.  
Hope this is helpful....

---

### Post by filfish on 2009-03-05
Hi jrusidoff

How have you got your machine thinking it joins?

I have to manually log in as as a local user and run domainjoin again before anyone with a domain account can log on

---

### Post by jrusidoff on 2009-03-05
Yes, it thinks it joins.  My problem was that I have my network set up with a router (which is my DHCP server) inside of a Cisco firewall.  My Server 2003 is not the DHCP.  Also, I have a weirdness where my primary DNS server is my 2003 and secondary is at my ISP.  Kind of thrown some 'stones in my passway' like Robert Johnson said, but now it works, but I still have to 'connect to server' to get connected to my shares with each session, even though I am 'permanently' logged onto the domain until I choose to leave.  Man, I don't think I have used so many quotes in one paragraph...'ever!' Ha!

---

### Post by filfish on 2009-03-06
My problem is more that the machines need to be rejoined every time they reboot.

We do not grant admin rights to users here so this is a big issue as we cannot go logging into these machines everytime they get restarted, they are used for teaching and are often switched off between lessons etc, and no, we won't be giving sudo privilidges to the teachers as they are worse than the students.  We somehow need to get the machines to either remember that they are part of a domain when they shutdown or to automatically join (with a script perhaps)

---

