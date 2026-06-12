---
title: "IPTables Assistance Needed - Block Everything Except Port 21"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Deathray on 2009-03-14
I need a quick guide to block EVERYTHING except ftp. I will be running a FTP server and want it to be as secure as possible (:
I have a static IP configured, so DHCP is no problem.
Also, could you please include in your quick guide, how to flush ip tables of all previous configurations?
And a low priority question - how do I in fact see the current ip tables configuration?

---

### Post by puppywhacker on 2009-03-14
For FTP-DATA you would also need port 20

iptables -L
lists the rules

iptables -F
flushes the iptables rules

iptables -A INPUT -p TCP --dport 21 -j ACCEPT
iptables -A INPUT -p TCP --dport 20 -j ACCEPT
iptables -A INPUT -j DROP

---

### Post by Deathray on 2009-03-14
Embarrassing I never knew about port 20 :O, hehe. Oh well Thanks a lot for the help!! ;) Another question regarding OpenSSH. Shall I start a new thread?
I want to limit the access so that only the user "Deathray" can login through SSH. Now if I leave the default OpenSSH configuration - anyone can login.
If I do: 
DenyUsers *
AllowUsers Deathray
in the /etc/ssh/sshd_config, I can't login. What is the proper way of allowing only user Deathray to login through SSH? :) Is it true that the only way is to manually type in all the users to be denied access?

---

### Post by Deathray on 2009-03-14
Found the answer to my exact problem regarding SSH:[http://www.linuxquestions.org/questions/linux-security-4/howto-sshd-deny-all-users-except-for-one-368752/]("http://www.linuxquestions.org/questions/linux-security-4/howto-sshd-deny-all-users-except-for-one-368752/")
Thread solved.

---

### Post by puppywhacker on 2009-03-15
good job solving your issues and reporting back :)

just in addition, I use fail2ban-ssh to temporary block ip-address that fail to login to ssh 3 times. It got rid of annoying brute force trying attempts.

I also set NoRootLogin so root will not be allowed access directly.

---

### Post by Deathray on 2009-03-15
Nice information, and thanks for the comment! :) I was also googling a bit last night regarding prevention of bruteforce attacks. I found [this]("http://blog.andrew.net.au/2005/02/16#ipt_recent_and_ssh_attacks") which simply uses iptables to block an IP address for X amount of time. Pretty slick!

---

