---
title: "pppd &amp; ip-up problem"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by hawkeye-ubu on 2010-01-12
Hi all - I am having problems making a local script initiate after my dial-up connection has been established.

In PCLos and earlier Ubus I just put the script into my etc/ppp/ip-up.d/ and make it executable
but for some reason - here in 9.04 - it won't work.

It says in* ip-up* > # This script is run by the pppd after the link is established.
                          # It uses run-parts to run scripts in /etc/ppp/ip-up.d, so to add routes,
                          # set IP address, run the mailq etc. you should create script(s) there. 

I know the script works because if I dial out then wait for the connect I can go and execute the script manually and everything works ??
But I should have it auto run for me every time a pppd connection has been implemented.

Anyone any ideas as to why this won't execute - it's driving me nuts.

Thanks in advance....

PS: the script is a simple port forward to enable both my dial-up inet connection and my local lan to remain operational at the same time. Else I can connect via pppd but aren't able to route any traffic -eg: surf etc.

---

