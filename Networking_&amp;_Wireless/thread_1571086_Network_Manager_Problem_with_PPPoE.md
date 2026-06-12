---
title: "Network Manager Problem with PPPoE"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by pbrthemaster on 2010-09-09
I'm able to configure PPPoE in NetworkManager but https sites are not working. http sites work fine.

If I configure using pppoeconf command I can browse both http and https sites.

Why it's not working with NetworkManager? How can I fix that?

I use Ubuntu 10.04.

---

### Post by pbrthemaster on 2010-10-31
The problem was missing NetworkManager.conf in /etc/NetworkManager

It works fine now.

---

### Post by Sef on 2010-10-31
Thank you for posting how you resolved the problem.

---

### Post by Em Eitch on 2010-11-24
pbrthemaster, I have run into similar problems with my PPPoE connection as you did. I don't know what to put in the NetworkManager.conf file. Could you please post some details?

Any help is much appreciated.

Thanks.

---

### Post by pbrthemaster on 2010-11-25
Hi,

I've the following contents in my NetworkManager.conf file. You can use the same,

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

--
Bharathiraja

---

### Post by Em Eitch on 2010-11-26
> **pbrthemaster said:**
> Hi,

I've the following contents in my NetworkManager.conf file. You can use the same,

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

--
Bharathiraja

Thanks a lot. However, I had already tried creating a bare bones .conf file and placing it there, to no avail. Then someone suggested limiting the MTU to that specific to my network, and that finally solved the problem.

---

### Post by imrahul1819 on 2011-06-09
I know its too late now..but i m have the same problem right now..I cant access some Websites in my Kubuntu but in windows7 ( like Facebook.com, etc). Need help !!!
Thanks !!!

---

### Post by foundrysmith on 2011-12-17
The post helped me with some weird connections problems after moving up to Ubuntu 10.10 from 10.4.  Following the advice of Em Eitch, I checked the nm-system-settings.conf file in etc/NetworkManager, and commented out a line (as sudo) that appeared under plugins (I see in the post below it is kept empty).   After applying,  I was then able to connect and reconnect to the Internet without a problem.

The line I commented out was:

no-auto-default=00:15:c5:ad:6b:96,

I do move this laptop around from location to location, and typically plug in to the Internet, which may be why this is happening.

---

