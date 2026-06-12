---
title: "Slow DNS"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by sowelie on 2010-06-30
I'm having a very strange problem.  Randomly, DNS lookups are extremely slow.  This seems to have started when I upgraded to Lucid.  It is not isolated just to my browser (firefox).  Also, it's not the usual ipv6 or mdns problem.  I've tried Open DNS, I've tried my ISPs DNS servers...nothing seems to work.  I have searched around a lot and have found nothing that has worked for me.  How can I troubleshoot this issue??

---

### Post by jonobr on 2010-07-01
Maybe a stupiod test, but maybe try modifying your hosts file and add an entry for a website you had trouble with.
When you start to experience trouble with regular DNS, go to the website defined in your hosts file, that lookup should be immediate, and get you to the website.
If you have the same trouble, then the issue would not be DNS related,. however, if you get to the website immediately, then maybe we could do more tracing to see whats going on at a packet level...

Just to add, be careful when adding entries to your hosts file and if poss make a backup of it before starting.

---

### Post by sowelie on 2010-07-02
The problem is it is so random.  For instance, it just happened again and it was en.wikipedia.org.  Now, I can go back there and everything is fine.  So it's very hard to troubleshoot because it's not consistent.

---

### Post by jonobr on 2010-07-02
Hello,

How long does it go on for?

If it happens for about 30 seconds, then placing an entry in the hosts file will tell you if its a problem inside or outside your machine.

So if you go to google and it does not work, and you have an entry in your hosts file for wikipedia, and you still see the issues, chances are its you machine thats at fault not a networking or ISP issue,

You could also put an IP address of a website directly into your browser and see also if that is slow.

Putting in the IP address will mean it wont use resolution to DNS. If it works ok, then its definately a dns issue.

---

### Post by Iowan on 2010-07-02
I'll point out [this]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") help page, but it sounds like you've narrowed the problem somewhat...

---

