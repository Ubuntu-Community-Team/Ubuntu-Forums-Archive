---
title: "unable to configure ufw"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by schalkefan on 2011-01-18
hello everyone,

i'm new to the forum and tried searching for answers to my prob, but didn't find the specifics. so any help will be apprechiated a lot.

i'm using ubuntu 10.10 and i made attempts to configure ufw firewall (by trial end error). I only added on rule. this is ufw output:

desktop:~$ sudo ufw status verbose 
Status: active
Logging: on (high)
Default: deny (incoming), deny (outgoing)
New profiles: deny
To                         Action      From
--                         ------      ----
Anywhere                   ALLOW OUT   Anywhere

this way everything works just fine. I then deleted that single rule and replaced it with "ufw allout out 80/tcp". I also did this for port 8080 and in both cases for tcp as well as udp. ufw status output then was exactly the same, exept for my new rules 
To                         Action      From
--                         ------      ----
80/tcp                     ALLOW OUT   Anywhere
80/udp                     ALLOW OUT   Anywhere
.
.
. etc..... as I said the same for port 8080.

problem now is, that webbrowsing is no longer possible. any browser I tried can't connect to any webpage. 

what really baffles me now is:
when I do not enter s.th. like "www.google.com" etc., but insteat type in the numeric host-adress (e.g. 72.173.20.15 etc.) it all works fine.

I presumed s.th. wrong with DNS resolving,
and checked etc/hosts, etc/host.conf, etc/nsswitch.conf, etc/resolv.conf. 
all these files have not been changed by me since installing ubuntu. they look like default-files I found on the net. in "resolv.conf" there are two of my ISP's DNS-servers. I don't know what else to try, so I registered to the forum that helped me MANY times before.

thanks everyone for reading thus far. I'd really be thankful for any hints and tips.

regards,
schalkefan

---

### Post by DrFolger on 2011-01-18
outgoing DNS queries use udp port 53. 
Allow that traffic and the IPs should be able to be resolved.

Edit: fixed an error.

---

### Post by schalkefan on 2011-01-18
thanks for the tip, DrFolger.

unfortunately not working this way either.

could someone who's using ufw as well, maybe post a quick glance at his/her configuration?

thx in advance

---

### Post by DrFolger on 2011-01-18
I realized I was in error, port 53 is for dns. and 68, iirc, is for dhcp. (fixed my prev. post)

I tested allowing out 53/udp and it worked.

---

### Post by zealibib slaughter on 2011-01-18
Try from a terminal ufw default.  That should load the default rules. If that doesn't work try ufw disable and see if you can browse. When you added the rules did you code in the terminal ufw allow  or change the config file?

---

### Post by schalkefan on 2011-01-19
hello zealibib slaughter and DrFolger,

thank you both for your help. I restartet ufw and set to default and added rule for port 53/udp. all works fine now.

thanks again, best regards,
schalkefan

---

