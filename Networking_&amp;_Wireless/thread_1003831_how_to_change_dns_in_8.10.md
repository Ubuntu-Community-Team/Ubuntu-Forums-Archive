---
title: "how to change dns in 8.10?"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by HarmonicaGoldfish on 2008-12-06
I just upgraded to 8.10 from 8.04. During the upgrade my dns settings were lost. I like to use open dns but can not seem to figure out how to change the settings!

Can anyone help me?

Is there a network manager function like in 8.04?

thanks!
Tracy

---

### Post by superprash2003 on 2008-12-07
this should help [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Dr Small on 2008-12-07
Just edit /etc/resolv.conf and add your DNS entries back in.
For openDNS, use:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Dr Small

---

### Post by HarmonicaGoldfish on 2008-12-07
Thanks for the help. It's working now.

Question - in /etc/resolv.conf I have the openDNS name servers as well as what is probably my ISPs name server (Rogers) 

nameserver 192.168.2.1

Should I delete that one or just leave it there?

---

### Post by superprash2003 on 2008-12-08
as long as 192.168.2.1 is below your opendns servers its fine..

---

### Post by etlpkby on 2008-12-12
I tried adding to /etc/resolv.conf but on next reboot my openDNS settings are gone.

I've recently upgraded from 8.04 to 8.10 and noticed the admin GUI to alter DNS settings isn't present? (network manager). Weird. Anyway, in 8.04 I updated /etc/dhcp3/dhclient.conf and appended this line:-

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

Will do that now with 8.10 me thinks ;)

---

