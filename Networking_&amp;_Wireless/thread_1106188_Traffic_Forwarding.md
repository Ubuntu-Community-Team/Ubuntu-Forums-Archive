---
title: "Traffic Forwarding"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by Razorg on 2009-03-25
Hello,

My university has an IMAP server to manage mails. You can read mail, from whichever PC you want, but Sending mails, is permitted only to pc's local to the server. My problem is i want to be able to send mail from my home, by using the IMAP server of my University.

I have ssh connection to the LOCAL PC's of the server, so i was thinking of doing a port forwarding, to the IMAP server.

At first i tried ssh tunneling, but failed, and then iptables, but it is allowed only to superuser, which i am not.

Do you have any idea how to solve it?

---

### Post by BkkBonanza on 2009-03-25
ssh tunneling should work but you may have got the forwarding wrong. The easiest way is to use ssh to do a socks proxy.

On your home machine you type,

ssh -D 8080 user@ip_or_name

That creates your proxy that can now be used for any purpose by any local program.
Now you change your mail program to use a SOCKS 5 proxy at: localhost port 8080.

Then you can use your mail program as normal. It should go through the proxy to your remote machine and open port 25 there to send mail just as if it were on that machine.

This method works great for doing other stuff from school like browsing or whatever.

Note that some programs like Thunderbird still do any DNS lookups locally. If you want to change that you have to do an advanced config setting to tell it to use remote dns when using proxy.

---

### Post by Razorg on 2009-03-25
yes, this will create a SOCKS connection between my home computer, and the local pc of the mailhost . but not the mailhost itself.

EG : mailhost is : mailhost.csd.uoc.gr
I can connect with ssh to syko.csd.uoc.gr which has the permission to send mail from IMAP.

So using those, is there a way to forward traffic from syko.csd.uoc.gr to mailhost.csd.uoc.gr?

---

### Post by BkkBonanza on 2009-03-25
Once you have the socsk proxy you can do anything you would do on that machine. That's the point. eg. If you use TBird on the uni lan to do your mail then with the socks proxy you can do that at home and it will appear as those it's happening on your uni lan. SSH will forward the connections dynamically from home to the uni server where it will issue them from there. So if you can do it at school then this allows you to do it at home. The socks proxy is like a dynamic relay. Your mailhost accepts them from the local server and isn't aware they came through the secure tunnel before that.

The only hitch in this is that your lan admin may have disabled socks proxies in ssh because they could be abused.

---

### Post by Razorg on 2009-03-25
Aw you are right. Thanks, really. It worked like a charm now, i got it wrong the first time :)

---

