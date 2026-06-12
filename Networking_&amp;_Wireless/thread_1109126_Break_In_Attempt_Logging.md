---
title: "Break In Attempt Logging"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by mocha on 2009-03-28
Where does Ubuntu/Linux log ping and IP scan attempts from the outside world?  I'm behind a NAT router, but I have to keep a few high numbered ports open for various reasons.  Will I see ping attempts to these open ports in /var/log/* somewhere?

---

### Post by lensman3 on 2009-03-28
I don't think you will unless you are running a local iptable's setup that has logging enabled.  The default setup is to just drop the pings.

Also if you have open ports then the only way I know to detect "pinging" is have setup some sort of "excess ping" rule that has to be tripped before it logs.  If somebody does a slow stealth look at the system and the open ports, I don't think it can be traced (or even noticed).

I would suggest that you decide which countries you want to "communicate" with and block the rest (of the world).  In reality, does your machine need to communicate with Nepal (my apologies to Nepal in this example), but would anybody from there be up to any good on your computer?  I currently block all of South America and Eastern Europe from connecting to my machine.  That doesn't mean that I don't contact them if I need to.  Remember that the connection is two way, just block one of the directions.

---

### Post by mocha on 2009-03-28
Thanks for the response.  I figured it had something to do with iptables.  Is there any easy way to setup iptables to only perform logging?  I don't want to block anything since I'm NAT'ed.  I just want to be able to log any pings, scans, or connection attempts to the ports I've explicitly opened in my router.  Note, my router isn't good enough to do logging.  Thanks.

---

### Post by shanix on 2009-03-28
Here is probably a good place to start looking:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

But, if you are behind router and the router is blocking all the ICMP traffic or if the port forwarding is not done from the router. I don't think you will be able to gather anything even if you have the iptables setup.

---

### Post by mocha on 2009-03-28
> **shanix said:**
> Here is probably a good place to start looking:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

But, if you are behind router and the router is blocking all the ICMP traffic or if the port forwarding is not done from the router. I don't think you will be able to gather anything even if you have the iptables setup.

I have some ports forwarded from the NAT router.  That's the point of my question.  My router doesn't do logging.  I wanted to know how to log (within ubuntu) connection attempts to those particular ports.

---

### Post by mocha on 2009-03-29
Thanks for the iptables documentation link.  I often forget how good the ubuntu documents are!

The example they have in that page to enable logging is almost perfect, however, since the log itself is the only rule I'm using, it logs ALL connection attempts.

Does anyone know how to force the iptables logging mechanism to only show attempts on specific ports?

---

### Post by mocha on 2009-03-30
Well, I figured out what I needed to do.  This is what I did to log conneciton attempts to specific ports.

Make the rules that you want for logging connection attempts, for example:

```
sudo iptables -I INPUT 1 -j LOG -p tcp --dport 57437 --log-prefix "IPTABLES LOG: " --log-level 7
```

That particular rule will log all tcp connection attempts to port 57437, syslog will contain the log record.  You could also choose "-p udp" to log udp connection attempts, and of course you can specify any destination port number.

When someone attempts to connect to one of the ports you specified in your rules, you'll see something like this in your syslog file:

```
Mar 29 23:42:32 xxxxxx kernel: [261737.573555] IPTABLES LOG: IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=xxx.xxx.xxx.xxx DST=xxx.xxx.xxx.xxx LEN=40 TOS=0x00 PREC=0x00 TTL=230 ID=29379 PROTO=TCP SPT=46957 DPT=57437 WINDOW=8192 RES=0x00 ACK RST URGP=0
```

You can setup any number of rules you want at the command line.  When you're done execute

```
sudo iptables -L
```

to list at all of the rules you applied.  Then execute

```
sudo iptables-save > ~/iptables.rules
```

to save all your rules to a file.  When you reboot your rules get flushed, so you can call a script to load the rules from your file.  In the script you would call the command:

```
sudo iptables-restore < ~/iptables.rules
```

Thanks for everyone's input!

---

