---
title: "How do you view DNS Host File? 10.04"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by vailixi on 2013-02-14
I want to clear my DNS cache. I looked this up.

I found a page that told me I could use:

/etc/init.d/nscd restart

This didn't work at all. The machine I'm working on didn't have nscd installed for some reason so I installed it with apt-get. Went to restart no error or confirmation message.

I was like hmmm? 

another that said:

etc/init.d/dns-clean

Also got no confirmation message from this command. I'm assuming it did something. But I wasn't sure where to look for the actual DNS host file to confirm my DNS cache had been cleared.

**My Question:**
On a typical ubuntu 10.04 installation, where is the DNS host file located. Or does DNS default to a public DNS server?

I know how to do this on a windows machine
C/windows/system32/drivers/etc/host pretty easy then I can view it with a text editor.

---

### Post by SeijiSensei on 2013-02-15
There is a static hosts file in /etc/hosts which you can edit manually as root with sudo.  However Ubuntu Linux before 12.04 does not routinely cache DNS queries as Windows unfortunately does.  (It makes fixing DNS errors really annoying, especially if you are working with ordinary users who have never typed a command like "ipconfig /flushdns" before in their lives.)  DNS servers do cache queries, but not clients.

(12.04 and later uses a different method of handling DNS requests.)

---

