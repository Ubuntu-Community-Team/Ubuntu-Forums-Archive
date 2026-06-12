---
title: "VPN w/o NetworkManager?"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2011-08-05
I use wicd instead of NetworkManager because it doesn't work for my WPA2 for some reason.  So I tried using ethernet & NetworkManager, added a VPN connection  [bestfreevpn.com] and it always says it failed to connect, or failed to authenticate or something.  So I tried it with the same login on my iPod Touch and it works fine. 

I tried these instructions: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient) where it says "Manually configuring your connection"  I added /etc/ppp/peers/bestfreevpn, and put in the username, then added the password to /etc/ppp/chap-secrets.  Then I did ```
pon myvpn nodetach
``` as root:
```
root: /home/matt # pon bestfreevpn nodetach
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
local  IP address 10.80.2.86
remote IP address 10.80.1.1
primary   DNS address 8.8.8.8
secondary DNS address 8.8.4.4

^CTerminating on signal 2
Connect time 1.9 minutes.
Sent 0 bytes, received 7552 bytes.
MPPE disabled
Child process pptp bestfreevpn.com --nolaunchpppd  (pid 8491) terminated with signal 2
Modem hangup
Connection terminated.
You have new mail in /var/mail/root

```

While it was running, I checked my IP. It was the same as before.   What am I missing here?

---

