---
title: "dansguardian/squid proxy firefox bypass"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by peterkp on 2011-07-23
Thanks in advance.
installed dansguardian and now working fine.I got a small problem.
People bypassing proxy settings in firefox, means they go to settings and changes proxy settings to no proxy.. how to prevent this? How can I force people to use proxy to connect Internet? I done some googling but,  unable to find a solution. 
Peter

---

### Post by peterkp on 2011-07-23
I use ubuntu 11.04 and firefox ver 4

---

### Post by HarriU11-04 on 2011-08-03
> **peterkp said:**
> Thanks in advance.
installed dansguardian and now working fine.I got a small problem.
People bypassing proxy settings in firefox, means they go to settings and changes proxy settings to no proxy.. how to prevent this? How can I force people to use proxy to connect Internet? I done some googling but,  unable to find a solution. 
Peter
You use iptables.

%sudo    iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-ports 8080
%sudo    iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner dansguardian --dport 3128 -j REDIRECT --to-ports 8080

After typing in those commands, dont forget to restart squid and/or dansguardian and firefox.

NOTE: You need to save those commands in a script that gets run every time the machine is booted. From my setup doc that I've written:

   %sudo bash -c "iptables-save > /etc/iptables.rules"

Create a script "iptablesload" and place script  in /etc/network/if-pre-up.d folder. In the script you should have the following lines:

  #!/bin/sh
  iptables-restore < /etc/iptables.rules
  exit 0

After setting up the script:

   %sudo chmod +x iptables-load

OPTIONAL: Set system wide proxy setting in Preferences. Doesn't matter if users play with firefox settings after you setup iptables. They're either going nowhere on the Internet or they will be be filtered

Have fun.

---

### Post by peterkp on 2011-08-04
Thank you sir, 
Great help.
I was going through IP tables. but I couldn't able to find a solution for my problem. Now I am very clear. Great help. Thank you.

---

