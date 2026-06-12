---
title: "open port TCP80 to use and VPN server"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by esbrinartot on 2013-02-26
I want to connect to an external VPN server but çI have problems with the firewall.

Without the firewall i can connect easily and works fine

But with the firewall doesn't works.

The tunnel is established by the port TCP80
I also try open the openvpn port 1194

I attach an image in order that you can check the configuration that I use for firestarter.

[IMG]http://img560.imageshack.us/img560/3871/firestarterb.png[/IMG]

What I'm doing wrong?

thks

---

### Post by esbrinartot on 2013-02-27
> **esbrinartot said:**
> I want to connect to an external VPN server but çI have problems with the firewall.

Without the firewall i can connect easily and works fine

But with the firewall doesn't works.

The tunnel is established by the port TCP80
I also try open the openvpn port 1194

I attach an image in order that you can check the configuration that I use for firestarter.

[IMG]http://img560.imageshack.us/img560/3871/firestarterb.png[/IMG]

What I'm doing wrong?

thks

Finally worked. What I've done is type:

sudo gedit /etc/firestarter/user-pre

And then copy:

$IPT -A INPUT -i tun+ -j ACCEPT
$IPT -A OUTPUT -o tun+ -j ACCEPT

My last question is know what this text do?

I want to understand the meaning and what I've done

thks

---

### Post by Grinage on 2013-02-27
I could be a little off base I'm not familiar with your particular version of of IPTables there are some slight variations across versions in other countries, but it looks like you've told the system to allow all ports through the system firewall in both directions.

---

### Post by esbrinartot on 2013-02-27
> **Grinage said:**
> I could be a little off base I'm not familiar with your particular version of of IPTables there are some slight variations across versions in other countries, but it looks like you've told the system to allow all ports through the system firewall in both directions.

Then What I should do to only allow the ports that I need. Which should be the correct syntax?

About the ports: 
I've used nmap and the results that nmap give me
command:
nmap 192.168.1.1/24
results:
Nmap scan report for 192.168.1.14
Host is up (0.000077s latency).
Not shown: 998 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind

I uderstand that this command give all the ports that you have opened in your computer.. Why I only can see the port 22 and 111?

When I type:
nmap -v -A -PN -T4 localhost

The result is

Scanning localhost (127.0.0.1) [1000 ports]
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 25/tcp on 127.0.0.1
Discovered open port 111/tcp on 127.0.0.1
Completed Connect Scan at 17:18, 0.04s elapsed (1000 total ports)
Initiating Service scan at 17:18
Scanning 3 services on localhost (127.0.0.1)
Completed Service scan at 17:18, 6.01s elapsed (3 services on 1 host)
Initiating RPCGrind Scan against localhost (127.0.0.1) at 17:18
Completed RPCGrind Scan against localhost (127.0.0.1) at 17:18, 0.00s elapsed (1 port)

So the ports seem closed.

---

### Post by Grinage on 2013-02-27
I can't locate the tun argument, but the A the INPUT and OUTPUT I'm familiar with, for me the A is append, so the command issued on my machine would append the iptables to accept traffic on a specified port both to and from the machine.  my command would look something like this

iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d x.x.x.x --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT

and would need to be entered with a series of additional commands to open the port for SMTP in this case, but these commands only need to run once, editing a file that is read at boot or login is something I've never had a reason to try for port related issues.

If nmap shows that the ports are closed, then they're closed, I wonder, now that the commands have run, if you remove them from the file does your VPN still work?

---

### Post by esbrinartot on 2013-02-27
When I remove the commands that allow all the traffic then doesn't work

I know that should be so simple to open the port 80. But I use firestarter and now seems to doesn't work.

Can I try to open the port 80 connecting to the router?

---

### Post by Grinage on 2013-02-27
```
iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d x.x.x.x --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp -s x.x.x.x --sport 80 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp -s x.x.x.x --sport 1024:65535 -d 0/0 --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A INPUT -p tcp -s 0/0 --sport 80 -d x.x.x.x --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

```

replace the x.x.x.x with the IP address of your machine, that will permanently open port 80 still trying to track down what exactly your original commands told the system to do.

---

### Post by Grinage on 2013-02-27
> **esbrinartot said:**
> 

I know that should be so simple to open the port 80. But I use firestarter and now seems to doesn't work.
?

If you enjoyed simple you'd still be a windows user

---

