---
title: "Access firefox on desktop via tablet?"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by victoriastuart on 2012-04-27
I want to use access a web browser (Firefox; ...) that is running on my Ubuntu 10.04 desktop, using an Android tablet, via my home wi-fi connection.

The reason is that I want to be able to access/control Rhythmbox remotely using my tablet.  I installed Rhythmweb, that enables me to do access/control Rhythmbox in Firefox (http://192.168.0.101:8000) -- on my desktop -- but I cannot access this address using my tablet (using the Dolphin browser, on my tablet).

I tried adding port forward for port 8000, (my D-Link DIR-615 router), but this did not help.

My firewall (System > Administration > Firewall configuration; or, gufw) is off (not Enabled).

Suggestions?  Thanks, appreciated.  :-)

---

### Post by newbie-user on 2012-04-27
All ports on Ubuntu that are not being used are turned off by default. You have to open port 8000 on your Ubuntu box. Even if your ufw is off, you still have to open port 8000.

On your D-link router, port forwarding is for incoming from the Internet, not your local lan.

You'll have to either set up ufw or use iptables, then allow port 8000 to your ubuntu box.

---

### Post by lovinglinux on 2012-04-27
Please open a terminal, paste the following and hit Enter.

```
sudo iptables -L
```

Select the terminal output, right-click on it, select "Copy" option an then paste here.

---

### Post by victoriastuart on 2012-04-27
Hi: I disabled port forwarding (not need, per the reply above) and enabled ufw (incoming/outgoing both set to Deny) with the following rule,

victoria@VICTORIA:~/temp$ sudo ufw status
Status: active
To                         Action      From
--                         ------      ----
8000/tcp                   ALLOW OUT   Anywhere

This did not help: I still cannot access Firefox on my Ubuntu box with my Android tablet.

The "sudo iptables -L" command dumps a lot of information, most of which appears to be unrelated (hence not posted here), bt I appreciate that suggestion.

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> Hi: I disabled port forwarding (not need, per the reply above) and enabled ufw (incoming/outgoing both set to Deny) with the following rule,

victoria@VICTORIA:~/temp$ sudo ufw status
Status: active
To                         Action      From
--                         ------      ----
8000/tcp                   ALLOW OUT   Anywhere

This did not help: I still cannot access Firefox on my Ubuntu box with my Android tablet.

The "sudo iptables -L" command dumps a lot of information, most of which appears to be unrelated (hence not posted here), bt I appreciate that suggestion.

The "sudo iptables -L" was suggested before you decided to enable UFW. It was intended to verify that you didn't have any firewall rules that could prevent the tablet from reaching the Rhythmweb application. But now that you have enabled UFW, it will result in a lot of entries.

Since you enabled UFW, you need to create a rule that will allow connection from the Tablet. The rule you have created is an OUTGOING rule, which won't make any good.

So you need to create a rule in UFW to allow incoming connections on port 8000.

Keep in mind you are not accessing Firefox and never will. What you are actually trying to do is to connect to a web server provided by Rhythmweb application, that allows you to control Rythmbox using any browser remotely, including Firefox.

There are ways of controlling Firefox itself remotely using ssh, but is not what you really need.

---

### Post by victoriastuart on 2012-04-27
Ah!  Thank you for that information.  I re-enabled port forwarding (screenshot) and replaced my ufw rule with the one you suggested (screenshot), but I am still having the same problem, accessing port 8000 from my tablet.

---

### Post by victoriastuart on 2012-04-27
oops .. here are those screenshots

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> Ah!  Thank you for that information.  I re-enabled port forwarding (screenshot) and replaced my ufw rule with the one you suggested (screenshot), but I am still having the same problem, accessing port 8000 from my tablet.

About the port forwarding, I didn't notice you were actually trying to reach the machine through local lan. So, there isn't the need for it like *newbie-user* mentioned. I have corrected my post immediatelty, but I guess I wasn't fast enough. Sorry fort that.

Do you have connectivity to web on the Tablet? Are all machines connected via wireless? If they are, then your router might be configured to prevent direct communication between two wireless machines. I am not sure the correct name of this feature, because my router is in Portuguese, but should be something like "Access Point Isolation". You need to turn that off, so you can actually have communication between two wireless machines in your local network.

---

### Post by victoriastuart on 2012-04-27
Ok, thanks (port forwarding)!  My router and computer are hard-wired (ethernet cable), with my computer connected directly to the internet.  I access my home LAN wirelessly though my tablet, that thus has internet access at home (e.g. facebook; gmail; web browser).

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> Ok, thanks (port forwarding)!  My router and computer are hard-wired (ethernet cable), with my computer connected directly to the internet.  I access my home LAN wirelessly though my tablet, that thus has internet access at home (e.g. facebook; gmail; web browser).

Turn off the firewall, then open a terminal in the Tablet and run this:

```
ping 192.168.0.101
```

Check if you get any errors or package loss.

---

### Post by victoriastuart on 2012-04-27
victoria@VICTORIA:~/temp$ ping 192.168.0.101

PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.

64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from 192.168.0.101: icmp_seq=2 ttl=64 time=0.032 ms

[snip: continuously updates, output similar to above]

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> victoria@VICTORIA:~/temp$ ping 192.168.0.101

PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.

64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.043 ms
64 bytes from 192.168.0.101: icmp_seq=2 ttl=64 time=0.032 ms

[snip: continuously updates, output similar to above]

That's good. It means you are reaching the desktop from the tablet.

Try the connection with Rhythmweb again.

---

### Post by victoriastuart on 2012-04-27
I apologize: I typed that in my terminal on my computer.

From the android terminal, the output is (essentially)

From 192.168.0.103 icmp_seq=1 Destination Host Unreachable

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> I apologize: I typed that in my terminal on my computer.

From the android terminal, the output is (essentially)

From 192.168.0.103 icmp_seq=1 Destination Host Unreachable

The desktop internal IP is 192.168.0.103 and the tablet is 192.168.0.101?

---

### Post by victoriastuart on 2012-04-27
The reverse (desktop is 192.160.0.1; tablet is 192.168.0.3)  :-)

---

### Post by lovinglinux on 2012-04-27
> **victoriastuart said:**
> The reverse (desktop is 192.160.0.1; tablet is 192.168.0.3)  :-)

But accordiong to your previous post you was trying to ping the tablet from the tablet.

Additionally, the numbers you posted above don't match other posts. Are you sure you are using the correct IP address?

---

### Post by lovinglinux on 2012-04-27
> **lovinglinux said:**
> But accordiong to your previous post you was trying to ping the tablet from the tablet.

Additionally, the numbers you posted above don't match other posts. Are you sure you are using the correct IP address?

Check if you can ping the tablet from the desktop as well.

---

### Post by victoriastuart on 2012-04-28
Sorry - - my bad! -- I meant to say (above) that 

my desktop is 192.168.0.101, and that my tablet (apparently) is 192.168.0.103

Here is the latest result:

[from my desktop:]

victoria@VICTORIA:~$ ping 192.168.0.103

PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data.

64 bytes from 192.168.0.103: icmp_seq=1 ttl=64 time=2067 ms
64 bytes from 192.168.0.103: icmp_seq=2 ttl=64 time=1059 ms
etc.

When I ping my desktop (192.168.0.101) from my tablet (192.168.0.103), this is the result (now; I'm typing it longhand, as I cannot copy/paste, here):

64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=93.3 ms

etc. (similar replies, varying times: 11.5 ms; 38/2 ms; ...)

---

### Post by lovinglinux on 2012-04-28
> **victoriastuart said:**
> Sorry - - my bad! -- I meant to say (above) that 

my desktop is 192.168.0.101, and that my tablet (apparently) is 192.168.0.103

Here is the latest result:

[from my desktop:]

victoria@VICTORIA:~$ ping 192.168.0.103

PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data.

64 bytes from 192.168.0.103: icmp_seq=1 ttl=64 time=2067 ms
64 bytes from 192.168.0.103: icmp_seq=2 ttl=64 time=1059 ms
etc.

When I ping my desktop (192.168.0.101) from my tablet (192.168.0.103), this is the result (now; I'm typing it longhand, as I cannot copy/paste, here):

64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=93.3 ms

etc. (similar replies, varying times: 11.5 ms; 38/2 ms; ...)

Okay, so it's good to know both machines are reachable. So now, try to connect to Rhythmweb using Firefox and the address [http://192.168.0.101:8000](http://192.168.0.101:8000). Assuming the firewall is still off, you should be able to control Rhythmbox.

---

### Post by victoriastuart on 2012-04-28
Hi: I've been able to access Rhythmbox using Rhythmweb with Firefox on my desktop computer, but never with my tablet.  Anyway, I do v. much appreciate the replies, but I'll pass on my of Rhythmweb / this issue.  Thanks!  V.  :-)

---

