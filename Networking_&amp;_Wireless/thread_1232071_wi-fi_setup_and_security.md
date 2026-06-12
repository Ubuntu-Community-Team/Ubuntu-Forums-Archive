---
title: "wi-fi setup and security?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by hyperyoda on 2009-08-05
Got a new laptop and was wondering about wifi security. I've never used wifi before. I wanted to go to some of the local coffee shops that offer free wifi but I need to know:

1) How do I setup wifi in Linux?
1) How do I detect and connect to public free network(s)?
2) How do I make my laptop more secure so others on wifi network can't steal or sniff my packets?

I heard many people using free wifi get heir passwords sniffed, etc.

Running Ubuntu 9.04 and Debian 5.01 triple boot with Vista Home Premium.

Any Linux programs for detecting available wifi signals and connecting to them and any wifi security apps?

Also another problem is that when at home I want my laptop to be able to share my DSL connection, right now my desktop is connected directly (static IP, no PPoE just raw ethernet frames) to the DSL modem and I was hoping I can keep this setup and find a way to attack my laptop when I want to use it at home so what hardware would I need and how should I set it up?

So right now I have:
phone jack ----> UPS ----> DSL modem ----> desktop NIC

I setup the networking manually by editing the appropriate files. I want the laptop to automatically connect to the wired network at home when I connect it and to wireless networks also, not sure if this can be done.

Zach

---

### Post by superprash2003 on 2009-08-05
yes ubuntu should manage wired and wireless network settings automatically..post output of **lshw -C network** from the ubuntu terminal to know more about your wifi card

---

### Post by Hobgoblin on 2009-08-05
> **hyperyoda said:**
> 
2) How do I make my laptop more secure so others on wifi network can't steal or sniff my packets?

I heard many people using free wifi get heir passwords sniffed, etc.


That depends.

If it's a secure site (i.e. has a padlock on the notification area in the browser) then they can't sniff your passwords as they are sent encrypted.

Otherwise there isn't much you can do.

It's not just on wifi though, anyone with access to the network between you and the site you are visiting can see what you send and recieve.

---

