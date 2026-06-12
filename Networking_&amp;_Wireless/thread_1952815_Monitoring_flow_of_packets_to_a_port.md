---
title: "Monitoring flow of packets to a port"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by Phoenix_Swelter on 2012-04-05
I have set up a script to capture streaming video. My script is currently monitoring my connection via netstat so that if the connection is reset, the script will recognize it and restart the capture.

But on several occasions the stream drops out without resetting the connection. I am looking for a way for the script to monitor whether packets are flowing in from a specific system or whether there's "dead air". What would nicely round out the utility I'm looking for would be if I could use it as a normal user without root privileges.

Any ideas?

---

### Post by Zorael on 2012-04-06
The only way I know of would be to set up an iptables rule, then periodically grep the output of **iptables -nvxL** for how many bytes have passed since rule was added or last zeroed.

You do need sudo for this though, but you can make a script and then edit your sudoers file to let you run it passwordlessly. There's likely some better and neater way to do this.

If the traffic is mainly coming from a remote source (as in your streaming case);
```
$ sudo iptables -A INPUT -s $SOURCE_IP --sport $SOURCE_PORT
```
You can limit it to a specific interface with **-i**, though I don't think that's necessary in this case. You can specify ip subnets [the usual way](https://en.wikipedia.org/wiki/IPv4_subnetting_reference) with **192.168.1.0/24**. In fact, there's just so much you can do that I'll just refer to its man page. :3

Concrete example counting traffic from ubuntuforums.org;
```
$ **sudo iptables -A [COLOR="RoyalBlue"]INPUT[/COLOR] -p tcp -s [COLOR="DarkOrange"]ubuntuforums.org[/COLOR] --sport 80**  *# hosts are only resolved once at rule creation*

$ **sudo iptables --line-numbers -nvxL [COLOR="RoyalBlue"]INPUT[/COLOR]**
Chain **[COLOR="RoyalBlue"]INPUT[/COLOR]** (policy ACCEPT 0 packets, 0 bytes)
num      pkts      bytes target     prot opt in     out     source               destination         
**[COLOR="Teal"]_1_[/COLOR]           [COLOR="Red"]0        0[/COLOR]**            tcp  --  *      *       [COLOR="DarkOrange"]**91.189.94.12**[/COLOR]         0.0.0.0/0            **tcp spt:80**

$ wget "**[COLOR="DarkOrange"]http://[COLOR="DarkOrange"]ubuntuforums.org[/COLOR][/COLOR]**" -o /dev/null *# wasting some bandwidth! we're rad like that.*

$ **sudo iptables --line-numbers -nvxL [COLOR="RoyalBlue"]INPUT[/COLOR]**
Chain [COLOR="RoyalBlue"]**INPUT**[/COLOR] (policy ACCEPT 155 packets, 81080 bytes)
num      pkts      bytes target     prot opt in     out     source               destination         
**[COLOR="Teal"]_1_[/COLOR]          [COLOR="Green"]31    37351[/COLOR]**            tcp  --  *      *       [COLOR="DarkOrange"]**91.189.94.12**[/COLOR]         0.0.0.0/0            **tcp spt:80**

*# or, if you know the [COLOR="teal"]**_rule number_**[/COLOR] (leftmost column);*

$ **sudo iptables --line-numbers -nvxL [COLOR="RoyalBlue"]INPUT[/COLOR] [COLOR="Teal"]_1_[/COLOR]**
**[COLOR="teal"]_1_[/COLOR]        [COLOR="Green"]2493  2663679[/COLOR]**            tcp  --  *      *       [COLOR="DarkOrange"]**91.189.94.12**[/COLOR]         0.0.0.0/0            **tcp spt:80**
```

I'd set up a loop that parses the output like that to get the amount of bytes transferred in periods of... 5-10 seconds? And then subtract the amount parsed from the last run from it. If the difference is less than a certain amount we treat the stream as dead, and do whatever it is you do to refresh it.

As a sidenote, iptables supports matching by transfer rate estimates (rateest), but it's apparently [broken in precise](https://bugs.launchpad.net/ubuntu/+source/iptables/+bug/957247) and I don't have an oneiric machine around to try it on. Having it monitor the speed like that would probably be a neater solution.

Anyway, please take a look at the attached example.

---

### Post by Phoenix_Swelter on 2012-04-06
:sigh:

I knew that sooner or later adding rules to the Universal Fire Wall wasn't going to be sufficient and I'd have to learn iptables. I guess now is as good a time as any.

Thanks for the input. I'll play with this stuff and see what I can learn.

---

