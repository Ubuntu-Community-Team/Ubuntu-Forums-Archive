---
title: "Unexplained Internet Activity (DNS?)"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by revanb on 2009-12-14
System Details:
Intel Quad Core, Ubuntu Karmic 9.10 (64-bit), 4Gb RAM

Short Description:
I have unexplained internet activity which is using up my bandwidth. About 6 KiB/s receiving and 2.5 KiB/s Sending in about 10s - 30s continuous bursts. I don't have auto-updating. It seems to have started about a week or two ago, depleting about 950 Mb.

Can anyone help me solve the problem?

Long Description:
I have so far:
- Closed all ports on my router
- Installed Firestarter (Firewall)
- Installed EtherApe (Graphical Network Traffic Display)
- Installed Wireshark (Packet sniffer/analyser)

I have determined that the traffic seems to be originating from my computer and the only way I can stop it is to use the Lock firewall option on Firestarter, but then all traffic is blocked and I can't use any network.

With Wireshark I determined that it seems to be DNS requests for an address simply called "A" and then responses are received saying that name doesn't exist.

I created a new account on my pc to see if it happens there as well and it does.

Consequence:
I don't how to stop it and reinstalling is not so easy since I have lot's of software and limited bandwidth. I can't leave my PC running as I normally do otherwise my bandwidth is used up. I only have 2Gb / month currently.

---

### Post by revanb on 2009-12-14
Anybody have any ideas? I don't know where to look anymore?

---

### Post by scottuss on 2009-12-14
Paste some Wireshark trace here so we can take a look at what might be happening.

Do you have Conky running? I remember once I saw a machine where a Conky plugin was trying to do some DNS lookups for some functionality but the address was invalid.

---

### Post by revanb on 2009-12-14
I'm not running Conky that I know of (don't know if something depends on it)

I'll paste some wireshark results later as I'm not at home at the moment.

Basically to me it looks like DNS requests are sent out for "A" and then they are followed by responses saying that the name is not valid and this goes on and on and who knows what process is sending it?

I wanted to just block the source port, but it seems that the source port is different every time like its random, the destination port is always 53.

---

### Post by scottuss on 2009-12-14
So, in Wireshark, the Destination address of these packets is listed as "A"?

Looking for the A record gives the actual IP address for a hostname, so it must be accompanied with a hostname.

It sounds as if a DNS request is being made without a hostname, which could easily be a script / application that is not configured correctly and it's trying to do a lookup of a blank hostname.

If you have the Destination IP address, it might be easy to figure out what's doing it.

---

### Post by BkkBonanza on 2009-12-14
Next time it occurs try this command,

sudo netstat -nptu | grep :53

This will list connections involving port 53 and list the process responsible.

---

### Post by revanb on 2009-12-14
Thank you, I'm going to try that as well when I get home.

---

### Post by revanb on 2009-12-14
Attached is about 4 packets worth of wireshark output.



When I run netstat as below it report the process is smtp. See the third entry.

192.168.1.33 is my PC
192.168.1.254 is my router connected to the internet.

```
revan@macphisto:~$ sudo netstat -nptu
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.33:36368      74.125.95.102:80        ESTABLISHED 3067/firefox    
tcp        1      0 192.168.1.33:52708      140.90.128.70:80        CLOSE_WAIT  3397/gnome-panel
udp        0      0 192.168.1.33:35575      192.168.1.254:53        ESTABLISHED 7227/smtp   
```

---

### Post by BkkBonanza on 2009-12-14
Well that seems fairly clear.

An smtp program (server, maybe MTA) wants to send mail and is looking up an address that can't be found.

It's requesting the IP for the mail server for domain "mail" which obviously isn't a valid domain name.

I assume here that some mail has been quequed in your system (for whatever reason) and the MTA is doing what they do which trying to re-send it periodically until successful. That mail needs to be cancelled, deleted.

---

### Post by revanb on 2009-12-15
What you say does make sense. I just don't know what it could be trying to send, but I am going to check that out tonight. Hopefully I can delete the "message" and be rid of this problem.

If that doesn't work I'm going to try to add "mail" to my /etc/hosts file just to try to get it to keep the traffic on the LAN for now?

This is probably the wierdest problem I've had with Ubuntu. Normally thing work very smoothly.:D

---

### Post by revanb on 2009-12-15
I finally solved the problem! I'm so relieved.

The problem was caused by me running jobs with cron and I did not add 
```
>/dev/null 2>&1
```
at the end of each crontab entry. That bit at the end causes any output from the jobs to be discarded. Since I didn't have it in, the nullmailer-send program was trying to mail the output. This mailing of the job output is supposed to be a local issue, but...

To compound the issue, for some reason, by default, in the /etc/nullmailer/remotes file the only entry was "mail." So basically the nullmailer-send program checks the remotes file for remote addresses to send the mail to and because there was this unfinished entry it kept trying and this is the reason for the incessant DNS requests that depleted 950mb of my bandwidth.

I'm just relieved I didn't have to reinstall. I'll file a bug report now since this is bound to affect anyone else using cron jobs with output. I think the remotes file is supposed to be empty by default.

Thanks everyone for your assistance.

---

