---
title: "Need Help Setting up iptable firewall"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by gulp35 on 2006-06-17
I'm in the process of setting up a computer for my brother by request of my parents.
They do not want him to be able to access the internet except for a select number of sites... I've been playing around with iptables and I thought I got it set up correctly but it is still letting everything through....

I have iptables set to drop any outgoing request except for the following:

192.168.2.2/24 -home network *want to include from 2 to 255*
64.82.100.151 -his school
207.142.131.200/28 -wikipedia  *want to include from 200 to 216*
171.64.0.0/255.252.0.0 -stanford *want to include from 171.64.*.* to 171.67.*.* 
82.211.81.0/24 -ubuntu *want to include from 0-255*
85.133.25.5/30 -ububtu  *include 5-7*

Does that look right? this is my first time messing around with net Masks.

To add these to iptables i first did:
```
sudo iptables -P OUTPUT DROP
```

then:
```
sudo iptables -a OUTPUT -s *an IP from the list* -j ACCEPT
```

After I set this up I don't have to mess with it again right? *i.e. it doesn't clear itself on reboot*

---

