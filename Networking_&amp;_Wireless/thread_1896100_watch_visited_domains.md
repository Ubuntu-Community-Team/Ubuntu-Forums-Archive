---
title: "watch visited domains"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by koszta on 2011-12-16
Hi,

I have some M$ certification but still kinda new to Linux (3 years or so). I have a kinda tricky question about iptables. 

I have a Linux server as the main router between our business and Internet. Now my boss asked me if it was possible to take logs of the web pages users (our workers) visited. They signed the agreement that their work on computer might be watched over. Could I somehow get a log of iptables so that it might something like this:

iptables -A FORWARD -s OUR_LOCAL_NETWORK -o INTERNET_INTERFACE -j LOG --file visited_pages

Can I make this work? And how can I push these msgs from this command to go to a special file?

---

