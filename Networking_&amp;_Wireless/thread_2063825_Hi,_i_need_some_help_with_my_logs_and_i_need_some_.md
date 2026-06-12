---
title: "Hi, i need some help with my logs and i need some usefull commands and more"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by sources on 2012-09-27
Hi,

I have problems with one or more hackers.. I try to read the log to find out how much access they have now, or if they really have any access anymore(I installed ubuntu again) But i have done it many times now, and after a day or two he is back again..

When i use VPN they/him(or here, i just refere to the hacker as "Geoffrey" from now on..

When i use the VPN "Geoffrey" send a DDOS attack or something so my network's go mad.. The same happens on different OS, different computers, and different routers! So it is not hardware or software that make the problem, it cant be..

The main reason i started using ubuntu again is because of "Geoffrey", because he used RDP and RCP, remote desktop to take full control over my computer.. And i have an idea of who it is, and he is not that good when it come to linux(And true enough i had "holiday" from "Geoffrey" a month or so, but then it started again.

I have reasons to be hacked as well, it is not just me getting paranoid.. Sure, it make me paranoid over time.. But i am pretty sure "Geoffrey" are kidding with my computer all the time..

But what should i do to really find out where all the data are getting sendt? (My computer suddenly start sending as much data that the network or the computer possibly can do without exploding..

So my question is: Can someone take a look at my log files? (It is logging at low leve, so it is not to much to see trough)

My other question is for hints, howto's ++

I need commands to how i can see what are happening when its happen, not just what i can see on the desktop.. (On the desktop i can see suddenly the screen get dark just for half a second, like someone are connecting to the computer with RemoteDesktop like in Windows,, other things is changing of password(Suddenly i cant login to users i know i have written down the password to) Its many many different things, ofcourse some of them is just bugs, but not everything, that i am 95% sure of.. And i where a hacker when Windows NT was the HIT ;) So im a bit rusty now, but "Geoffrey" seems like a pro..

I also have noticed nameservers getting changed.. But what worries me are the things i havent noticed, i cant read the log in ubuntu.. And i cant enough commands to do any useful things here..

So please help me even if i am paranoid(If i am you can confirm it:p )

Thanks for replies, help and commands&tricks, maybe some apps/programs i can use..

But after the time i know for sure i got hacked, everything has been unstable on every computer(very strange)

---

### Post by agillator on 2012-09-27
What are you using for a firewall?

---

### Post by uncaspi on 2012-09-27
See man tcpdump

sudo tcpdump -i wlan0

wlan0 is my card. Replace with yours logical card name.
At least with this command you should be able to determine the ip he use.
Such attacks will probably not shows up in the log files located
in /var/log dir.

---

### Post by sources on 2012-09-28
> **agillator said:**
> What are you using for a firewall?

Hi, iam using ufw. Is it any better out there?

---

### Post by sources on 2012-09-28
> **uncaspi said:**
> See man tcpdump

sudo tcpdump -i wlan0

wlan0 is my card. Replace with yours logical card name.
At least with this command you should be able to determine the ip he use.
Such attacks will probably not shows up in the log files located
in /var/log dir.


Ok i tried to command, but it is just comming a loot of data :) Is it a more specific command for this? I only use ethernet because i was sure it was my neighbour trough the wlan at first(He could still access me trough the router doh) Or maybe bluetooth(But i have turned it of in bios)

But regarding BIOS, i remember also suddenly my bios look different, is it possible that someone could flash my bios and gain full acces over my computer from before booting any OS ? (I know it is possible, but you have to be very good, but how the hell would i know if that happend, or how could i fix it?)

---

### Post by sources on 2012-09-28
00:21:23.590244 ARP, Request who-has 10.0.0.1 tell varn.local, length 28
00:21:23.590431 ARP, Reply 10.0.0.1 is-at 00:22:07:0c:47:ed (oui Unknown), length 46

What about this?

---

### Post by agillator on 2012-09-28
What that last message means is that the ip address you queried is a private ip address for the interface with the MAC address as listed (00:....). That is most likely your computer.

Have you made any changes to your firewall? For example are you running any servers such as a web server or do you allow ssh access to your computer from the internet? If not, the default setup for ufw should be to only allow input if it is a continuation of or related to a contact you initiated. A ping of your machine might be allowed, but not much else. 

If you run the command 'sudo iptables -L -v -n --line-numbers' you can see what is happening with your firewall. UFW also has a log you should be able to check by running ufw.

But the biggest question at this point is this: what makes you think you are being attacked or hacked? You mentioned a DDOS attack. What evidence do you have? That may help someone help you.

---

