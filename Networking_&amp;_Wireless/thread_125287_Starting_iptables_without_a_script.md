---
title: "Starting iptables without a script?"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by ubuntu123 on 2006-02-03
I'm trying to figure out how to start iptables directly from the command line. I don't need it running all the time and and don't need it to start when the computer boots. I don't believe there are any switches that will start it in daemon mode. All my searching has turned up nothing; everything I find mentions creating a script. I'm just looking for quick way to start it without putting a script in /etc/init.d. Is there any way to do this?

I posted this (under a different username) in the Ubuntu 4.10 section about a week ago, but go no replies.  I believe this question is applicable for any version of Ubunutu and will get more exposure in this forum.

---

### Post by christhemonkey on 2006-02-03
(i think this will work!) This allows all IP addresses:
> iptables -A INPUT -p tcp -i eth0 --dport 80 -j ACCEPT

Though firestart the GUI would be easier to configure i imagine!

---

### Post by hajk on 2006-02-04
If you have the iptables package installed, there is already a script installed in /etc/init.d/...  and it starts the firewall on boot. The default just lists the standard INPUT, OUTPUT and FORWARD tables, which acts as if there is no firewall at all. You can save it with the command

    sudo iptables-save > rules-off

where rules-off is full-path filename (you may have to touch it first).

Then you could input some simple rules by hand, and save them by the command

    sudo iptables-save > rules-on

Now you could switch between these with

    sudo iptables-restore < rules-on

and 

    sudo iptables-restore < rules-off

If this depends on the sort of LAN connection, then you could put pre-up lines with these commands in /etc/network/interfaces.

Just my €0.018 worth...

---

