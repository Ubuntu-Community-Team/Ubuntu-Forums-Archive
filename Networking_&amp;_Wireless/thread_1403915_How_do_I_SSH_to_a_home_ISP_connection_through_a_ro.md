---
title: "How do I SSH to a home ISP connection through a router"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by cilbuper on 2010-02-10
Here is what I need to do. I want to be able to connect to it from a remote location with PuTTy, Cygwin or Linux.  

I have a server set up at my house, let's say the IP is: 192.168.2.123 and SSH is always running and I have connected to it from another machine on the network many times.  My DSL modem is 192.168.1.254.  I set up my router to forward everything from port 30000 to port 22 on my Linux Server (192.168.2.123).  Lets say that my DSL modem external IP is 75.35.66.144 (it is not pingable though, my ISP said that anonymous ping request is disabled).  


Here is what I have been doing to try to log in.

```
ssh username@75.35.66.144:30000
```
This is the error message I get: > ssh: Could not resolve hostname 72.25.44.115:30000: Name or service not known
What the code above says to me, is:  SSH with "Username" at the machine at IP address 75.35.66.144 on port 30000.  

Now since I have my router set to forward port 30000 to port 22 on my Linux server, why is this not working?

---

### Post by gombadi on 2010-02-10
> 
ssh username@75.35.66.144:30000


```

ssh -p 30000 username@75.35.66.144

```

ssh uses -p to specify the port and to make life really fun scp uses -P :-(

---

### Post by 2hot6ft2 on 2010-02-10
> **cilbuper said:**
> Here is what I need to do. I want to be able to connect to it from a remote location with PuTTy, Cygwin or Linux.  

I have a server set up at my house, let's say the IP is: 192.168.2.123 and SSH is always running and I have connected to it from another machine on the network many times.  My DSL modem is 192.168.1.254.  I set up my router to forward everything from port 30000 to port 22 on my Linux Server (192.168.2.123).  Lets say that my DSL modem external IP is 75.35.66.144 (it is not pingable though, my ISP said that anonymous ping request is disabled).  


Here is what I have been doing to try to log in.

```
ssh username@75.35.66.144:30000
```
This is the error message I get: 
What the code above says to me, is:  SSH with "Username" at the machine at IP address 75.35.66.144 on port 30000.  

Now since I have my router set to forward port 30000 to port 22 on my Linux server, why is this not working?
For SSH the port comes before the IP Address like this:
```
ssh -p 30000 username@75.35.66.144
```

---

### Post by cilbuper on 2010-02-10
> **gombadi said:**
> ```

ssh -p 30000 username@75.35.66.144

```

ssh uses -p to specify the port and to make life really fun scp uses -P :-(

Thank you.  I'm trying this now.  Would it look like this:

```
ssh -p 30000 username@ipaddress
``` ?

---

### Post by 2hot6ft2 on 2010-02-10
> **cilbuper said:**
> Thank you.  I'm trying this now.  Would it look like this:

```
ssh -p 30000 username@ipaddress
``` ?
Yes, check the link in my sig for how I setup SSH and FreeNX for remote desktop. You'll find some links there that will be useful.

---

### Post by cilbuper on 2010-02-10
When I do the -p, it just times out.  I have tried both:
ssh -p 30000 username@ipaddress
and
ssh -p30000 username@ipaddress 

And they both time out.

---

### Post by 2hot6ft2 on 2010-02-10
Did you open the port on the ssh servers firewall?
Did you set the firewall to only allow connections from your LAN or from anyone (which is what it would consider you if you're not on the LAN)?

---

### Post by cilbuper on 2010-02-10
To make things a little more clear, I just tried connecting to someone who has the same ISP and a similar IP address.  

I did a port forward from port 30000 to port 3389 and tried to connect via RDC from my Vista box to a remote XP box by entering
"Ipaddress:30000" and it times out like when I try to connect to my Linux server at my home location. 

Does this sound like there is an issue with the ISP blocking some things, or could it be that the modem is on a different network than my router (Modem is 192.168.1.254, Router is 192.168.2.1)

IDK.  

I will read that thread that your sig links to.  Thanks for your help!

---

### Post by cilbuper on 2010-02-10
> **2hot6ft2 said:**
> Did you open the port on the ssh servers firewall?
Did you set the firewall to only allow connections from your LAN or from anyone (which is what it would consider you if you're not on the LAN)?

I don't know.  It is set up as the default install on server 9.10.

I know that I can connect to the server from within my network from my windows box.  

I do think I did install Iptables, and it is set to the default standards.

---

### Post by cilbuper on 2010-02-10
I just tried to connect to my windows box via RDC (using GotoAssist) with the same port forwarding setup (different ports).

I think there is something wrong with the ISP.  My local phone company was just bought out by "WINDSTREAM" and it SUCKS!  THe service has gone downhill a lot.  My bandwidth is nothing like it was and now I can't connect through the same connection setups that I had up and running a few months ago. Since they were working before the migration, this leads me to believe that this isn't anything that can be fixed on my end.  I hate when large crappy companies buy good small companies.  

This ISP now charges me $5 if I pay my bill over the phone!  Can you believe that!  A phone company charging to pay the bill over the phone!  Never thought I would see that day.  

Now I'm sad.. er...

---

### Post by 2hot6ft2 on 2010-02-10
iptables is installed by default in ubuntu. You can configure them and the most common way it to use something like firestarter or gufw. I use firestarter even though it's not being maintained it's real easy to use and simple to configure.
If it's not under System > Administration > Firestarter
You can install it with
```
sudo apt-get install firestarter
```
I believe the firewall is what is stopping you.

---

### Post by 2hot6ft2 on 2010-02-10
Keep in mind the IP Addresses you mention starting with 192.168.?.? are internal to your LAN.
> **cilbuper said:**
> 
I have a server set up at my house, let's say the IP is: 192.168.2.123 and SSH is always running and I have connected to it from another machine on the network many times.  My DSL modem is 192.168.1.254.  I set up my router to forward everything from port 30000 to port 22 on my Linux Server (192.168.2.123).  Lets say that my DSL modem external IP is 75.35.66.144 (it is not pingable though, my ISP said that anonymous ping request is disabled).
The external IP Address is how you connect to your LAN from outside the LAN.
My router has settings to drop ping requests as yours probably does.
My firewall also drops ping requests (quietly).

---

### Post by 2hot6ft2 on 2010-02-10
Ok. Let's say you install firestarter on the server. Firestarter just like GUFW is just giving you a GUI for the iptables.
You start it up and go thru the setup which is very simple.
Then click on the Policy tab.
Left click in the bottom box.
Right click on it and ADD Rule, or click the Plus sign +
Choose SSH from the drop down
Add the port # you're using
Now you have the "When the source is" section
You can choose anyone (meaning local or not), LAN only, or a specific IP Address.
Click Add
Click the check mark at the top to apply the rule.
All done.

---

