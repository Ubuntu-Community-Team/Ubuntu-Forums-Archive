---
title: "Wireless greyed - hard blocked"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by isagarran on 2011-05-28
Hello,

I'm working on Ubuntu 10.04 on T410. Since an upgrade last week, I'm no longer able to connect to Wireless Network.
In NetworManager applet, wireless activation is greyed and i can't activate the wireless on my computer. I didn't change anything in my Network configuration (as i know).
/etc/network/interfaces is rathere basic :
     auto lo
     iface lo inet loopback
     auto wlan0
     iface wlan0 inet dhcp

I look on Ubuntu forum and google and i used several commands in order to solve this problem but I fails. It would be nice if someone could help me. 
I saw using rfkill that "hard switch" are always to Yes whatever the command I used (Fn+F5/rmmod/rfkill/...).
And i got a message "SIOCSIFFLAGS: Erreur inconnue 132"
I attached with this post a file with all commands related to this problem.
Let me know, if something new could help, because I'm totally stuck with this problem.
Regards.
isagarran:(

---

### Post by isagarran on 2011-05-28
Hello,
My wireless come back. At last, i found a very small switch on the rigth side of my computer in order to enable radio.
I can't believe that i spent one week on this problem.:P

Thanks a lot for your help.
regards.
isagarran

---

