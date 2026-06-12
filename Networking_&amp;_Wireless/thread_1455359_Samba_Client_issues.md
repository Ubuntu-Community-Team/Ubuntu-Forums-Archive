---
title: "Samba Client issues"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by The Titan on 2010-04-15
I have been using Ubuntu sense about 6.10 and never had to network with a Windows computer before. I have a decent understanding of Linux itself but I am having issues with this samba client.

I have a clean install of Ubuntu 9.10 and am trying to use samba to access my shares on a Windows XP(SP3) computer. I am on the network just fine, and all the computers on the network have static IP addresses.

When I go to Places->Network->Windows Network I see the "TITANNET" workgroup, (Even before I changed my workgroup to "TITANNET" in the smb.conf file.), but when I try to access it I get this error:
```

Unable to mount location

Failed to retrieve share list from server.
```P.S.[0] I tried using /etc/init.d/samba restart but it did not work, I am not sure I am even running the samba server. (Well, it is obvious I am not, what I really mean is what am I running to (not =D)access the shares on my Windows PC.)

P.S.[1] I know that this has probably been posted before. I have searched and searched, I am about 1.5 pots of coffee and 4 hours into this. I apologize for the inconvenience if this was just solved.



Thank You,
Daniel

---

### Post by Iowan on 2010-04-15
Maybe you've already seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To... otherwise, it's worth reading.

---

### Post by Roasted on 2010-04-16
I've never really relied on doing it through the main network thing like that. I always go to start - run - \\server\

---

