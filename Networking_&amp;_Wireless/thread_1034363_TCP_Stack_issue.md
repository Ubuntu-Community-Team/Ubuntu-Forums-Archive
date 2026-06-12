---
title: "TCP Stack issue?"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by gschwim on 2009-01-08
I've been troubleshooting a problem with two Ubuntu systems, both running Hardy.

The problem is specific to an SMTP system that I relay mail through.  Small emails go through find, but large ones nearly die around 200 packets into the transfer. 

A packet capture yields at around 200 packets, the client system begins retransmitting some packets that I already see ACKs for, plus the client literally freezes just after 200 packets, regardless of receiving proper ACKs, and stops sending data save for a single packet on a very regular scale - 10 seconds, 20 seconds, 40 seconds, 80 seconds, then 160 seconds. At 160 seconds the email client times out.

I've used evolution, mailx, and postfix to send mail through this upstream relay, on two different systems and I get the same result in both cases.  I even tried piping a large email through netcat and received the same result.  When I try it from Windows, the transfer flies and completes properly.

I did some research, turned of TCP window scaling, and adjusted wmem and rmem as suggested in several articles, but there was no change in behavior.

Any ideas?

I have about a dozen packet captures of this if anyone is interested in seeing them.

---

### Post by gschwim on 2009-01-09
Still working this one...

I tried a third PC, booted the install CD into live mode, and tried sending an email.  I get the exact same problem.

So, the problem is specific to Ubuntu or Linux itself.

Anyone have any ideas here?  This is beyond me.

---

### Post by gschwim on 2009-01-09
I figured it out.  The problem is being caused by the tcp_sack option in the kernel.  If I disable this option, the transfers fly faster than I've seen before.

Is this possibly a kernel bug?  What should I do with this info?

---

### Post by geforce123 on 2009-01-09
You could report it to Ubuntu in Launchpad

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

