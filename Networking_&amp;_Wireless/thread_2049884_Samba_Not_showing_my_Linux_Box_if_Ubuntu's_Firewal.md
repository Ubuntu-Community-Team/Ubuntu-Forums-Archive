---
title: "Samba Not showing my Linux Box if Ubuntu's Firewall is turned on."
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by 777funk on 2012-08-29
I just noticed this...

In my windows machine the shared folders don't show up if I have my Ubuntu Firewall ON.


by the way is the default after a new install that the firewall is off?


Should I have the firewall on?

---

### Post by Morbius1 on 2012-08-29
To allow samba to function properly:
```
sudo ufw allow Samba
```As for your other question it really is an exercise in semantics. Netfilter controls who has access or not depending on the rules provided by iptables. UFW is a command line front end that allows you to manipulate these rules and GUFW is a GUI front end to UFW.

Netfilter and iptables are running as soon as you install your system but it doesn't have much to do since in a base install you have no services running that allow anyone into your system. Install Samba and all of a sudden you have a service running that allows someone into your system ( samba permitting of course ). 

Installing Samba also automatically creates a packaged rule that you can use if you wish located here: > /etc/ufw/applications.d/samba"sudo ufw allow Samba" invokes that preset rule to allow Samba to function. You can make this far more complicated of couse but I won't be of much help with that.

All of my fixed assets ( i.e., desktops ) are behind the firewall in my router and all my portable assets ( laptops and whatever ) are running OSX or iOS and to be honest I have no idea how these apple products protect themselves - pixie dust I imagine. In any event I don't mess with a firewall on Linux and am not an expert on Linux firewalls. Someone else will no doubt have a far better explanation than the one I just gave.

---

### Post by wyliecoyoteuk on 2012-08-29
The firewall is off by default.
If you are in a home network behind a router with a firewall, there is little need for another firewall on each PC.

---

### Post by Morbius1 on 2012-08-29
>          The firewall is off by default.This is the semantic thing I talked about above. Probably not worth getting into an augment over but the "firewall" is not off be default. Netfilter and iptables are running the instant you boot. The issue is by default it has no rules.

In a base install there are no services running ( um ... with the exception of CUPS perhaps ) that are listening on any ports so there don't have to be any rules.

If you do a "sudo ufw default deny" followed by a "sudo ufw enable" ( or it's gufw equivalent ) then you just created a rule to block everything. Install Samba and now you have to open it up again - at least for the samba ports.

In any event, I haven’t set any rules or enabled ufw my desktop either since I'm behind a router.

---

### Post by wyliecoyoteuk on 2012-08-30
Whatever the semantics, a firewall with no rules is effectively off, as in the service may be running, but it is not doing anything, so is not actually functioning in the traditional sense of a firewall.
If it is down to semantics, Netfilter and IPtables are not a firewall, it is the sum of the services and rules that are deployed that create one.
So, no rules = no firewall.

---

### Post by Morbius1 on 2012-08-31
Let's try an experiment:

If I had ufw enabled I'd stop it:
```
sudo ufw disable
```Now I'm going to stop CUPS, Samba, and mDNS services all of which are designed to listen in on specific ports:
```
sudo service cups stop
sudo service smbd stop
sudo service nmbd stop
sudo service avahi-daemon stop
```Now I ran the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*192.168.0.100 is the ip address of my machine.*[/COLOR]
This is the output:
> Nmap scan report for 192.168.0.100
Host is up (0.0000030s latency).
[COLOR=Blue]Not shown: 1998 closed ports[/COLOR]
PORT   STATE         SERVICE
22/tcp open          ssh
68/udp open|filtered dhcpcPort 68 is the dhcp client and without it I wouldn't be able to make a nuisance of myself in this forum. Port 22 is open because I wasn't smart enough to remember that I have ssh server running.

All other ports are closed. Do you consider my "firewall" on or off?

---

### Post by wyliecoyoteuk on 2012-09-01
Off. It is not doing anything, in fact it is running but idling, I suppose.
You would get the same result if it was not running.
As far as a newbie is concerned, it is not performing any function, so it is "off".
Nit-picking over the true meaning of "off" is just a waste of time.

---

### Post by Morbius1 on 2012-09-01
> **wyliecoyoteuk said:**
> Nit-picking over the true meaning of "off" is just a waste of time.
Quite right. So for the purposes of the original question and for newbie's in general:

** The "firewall" is on by default since all ports are closed.

** If you enable a server ( CUPS, Samba, mDNS, SSH, etc.. ) specific ports are automatically opened to allow the server to listen for incoming requests.

[COLOR=Blue]The user can confirm this himself by using the nmap command as I have above. Run it first without using ufw or gufw. Then turn off a server service like cups or samba and run nmap again. Server service running - port is opened. Server service not running - port is closed.[/COLOR]

** You can bypass this process by creating a rule using ufw or gufw blocking all incoming traffic regardless of what the server tries to do but then you will have to set other rules to open specific ports corresponding to the ports required for that server.

In this way you could for example block all incoming requests for everything except Samba.

---

