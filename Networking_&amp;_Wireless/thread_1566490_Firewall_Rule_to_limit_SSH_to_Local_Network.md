---
title: "Firewall Rule to limit SSH to Local Network"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by rowbird on 2010-09-02
Hi All, I would like to create a  rule to block ssh from the internet, but allow it from my local network only. I have static local IP address on my machines.Thanks in advance.

---

### Post by CharlesA on 2010-09-02
```
sudo iptables -A INPUT -p tcp -m tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp --dport 22 -j DROP
```

---

### Post by rowbird on 2010-09-02
Thanks, that's awesome, but how can I test it?

---

### Post by Skaperen on 2010-09-02
Running SSH on an alternate port can be useful, too.  If your issue with leaving it open to the net is not about the risk of people getting it, but just that they are using network bandwidth and eating logging space by trying, then move your SSH to another port number.  Do avoid the various port numbers that are typical targets of other attacks.

In /etc/ssh/sshd_config find "Port 22" and change to something like "Port 345" (for example).  Just remember where you move it to if you want to get in from remote.  SSH will still do the usual key and/or password checks and keep your session secure.

---

### Post by Skaperen on 2010-09-02
> **rowbird said:**
> Thanks, that's awesome, but how can I test it?
Try logging in to it from a nearby college campus or internet cafe.  That or see when all the breakin attempts from hackers ends.

---

### Post by CharlesA on 2010-09-02
> **rowbird said:**
> Thanks, that's awesome, but how can I test it?

You can try logging in from outside the network. Is there a reason you need to specifically block SSH from the internet?

If you don't want it to be accessible from the internet, you can normally just not forward port 22 on the router.

---

