---
title: "nmap general question."
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by bullet311 on 2010-02-23
Quick question here.

I was learning how to use nmap with all its different flags and commands. I scanned a random site using the -sS flag and then the -O flag. After getting this I scanned one of the specific ports. The scan failed. I next did another -sS scan in which the results showed that all ports were then closed. Before 12 had been open. Why did they all of a sudden close? Is it because my scans were detected? Hope this isn't a dumb question but I was confused. 

Thanks

---

### Post by bullet311 on 2010-02-23
Tried it again, and it seems after I scan the ports they all lock down. From playing around with it one port opened up again which I believe hosted the site. After scanning that port every single port was locked up. Am I exciting myself over something silly? What's causing this?

---

### Post by bullet311 on 2010-02-24
bump

---

### Post by Iowan on 2010-02-24
> **bullet311 said:**
>  Why did they all of a sudden close? Is it because my scans were detected? Hope this isn't a dumb question but I was confused. 

ThanksIt's possible, I suppose. Seems like some of the Intrusion Detection software I read about (a few years ago) had the ability to respond to the type of "threat" you generated (I'm sure the site appreciated your attention ;) ).

---

### Post by bullet311 on 2010-02-24
Oh, well don't think of it as a threat :smile: I just was learning how to use it and I didn't know if it was me that was doing it or something else. I am going to try it again because there was some info that was in the terminal but I didn't take the time to record it. Ill edit.


EDIT: After enjoying my new found tool I recorded some things that are new to me. Not that anyone cares, but I wanted to post it anyways. After a Stealthy Scan I produced some open ports that under the respective services had: (FTP, ssh, smtp, http, pop3, imap, https, smtps, imaps, and pop3s.) I don't know what those are but I am going to google them. 

After running an Operating system scan the ports closed but I recorded this. 

Device type: General Purpose|switch|WAP|Media Device|Firewall|Broadband Router|

Running: Colbalt Linux 2.0, Hp, Linksys, Netgear, Watchgaurd, ZyXEE, ZyNOS 3.x (All of those embedded.

Than it said too many fingerprints. But I don't know what that means.

To Google.
This rocks!

Bull3t

---

### Post by Iowan on 2010-02-24
I realize you're just learning how to use it, but the sites you scan may (probably will) view it as a threat - especially if you try it multiple times.

---

### Post by d3v1150m471c on 2010-02-24
What command(s) are you using? The entire string please.

---

### Post by bullet311 on 2010-02-24
I added an edit above. but for the question above about the string used:

nmap -sS -vv (ip address of site)             this is for stealthy
nmap -O -vv (ip address)                          for Operating system
nmap -sT -p (port#) (ip address)                   for scanning specific port

-vv is to show extra information

---

### Post by d3v1150m471c on 2010-02-24
You're getting different responses back because you're setting different flags and commands. IE -sS isn't going to be the same as -sU. Also, syn isn't very stealth on most systems compared to -sF and sometimes xmas scanning. nmap itself actually isn't very stealth with all the lastest security upgrades on multiple platforms. However, zombie scanning is truly stealth or you can break the scan up to spoof your ipaddress among non-spoofed packets.
```

man nmap

```

---

### Post by bullet311 on 2010-02-24
Oh yeah, I knew that I would get different responses after using the different flags. The -sS was undetected until I used the -O flag. After that they shut down. Trying the -sS command again it didn't work and the ports were closed. 

Yeah, for my learning purposes this seems fine. But Ill definitely check out the tools you listed.

Thanks

---

