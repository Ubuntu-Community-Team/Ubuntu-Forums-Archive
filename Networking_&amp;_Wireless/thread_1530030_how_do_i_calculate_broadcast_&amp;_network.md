---
title: "how do i calculate broadcast &amp; network"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by gabak on 2010-07-13
i m setting up a linux server and i have to setup ip , in static mode.
so i know everything except those two things.
how do i calculate them?
example ip:200.49.142.91
submask 255.255.255.248
gateway 200.49.142.89

thank you in advance

---

### Post by lisati on 2010-07-13
The answer depends on whether you're talking about your local network or your public i.p. address.

Making your publicly accessible ip address static, if needed, is something you'll need to arrange with your ISP. 

If, however, you are talking about your local ip address, i.e. on your local network, it's probably easiest if you do so on your router's configuration page. The exact details can vary depending on your router's make and model. I prefer using my router's settings over doing it within Ubuntu because it helps avoid i.p. address conflicts if I need to hook up my machine to someone else's local network for some reason.

---

### Post by gabak on 2010-07-13
thxs for ur quick answer i called my ISP and they told me the things i needed.

ps: do u know about email server citadel? or basic things to protect my email server with some iptables or firewall , something

---

### Post by lisati on 2010-07-13
I've never used Citadel. My home server uses [Postfix]("https://help.ubuntu.com/community/Postfix"), with [amavis/clamav/spamassin]("https://help.ubuntu.com/community/PostfixAmavisNew") to check for spam and malware, [Postgrey]("https://help.ubuntu.com/community/PostfixGreylisting") and a couple of other tweaks to help keep the spammers away.

---

### Post by gabak on 2010-07-13
are they easy to set them up? how long does it take?

---

### Post by lisati on 2010-07-13
Doing the basic setup and testing it shouldn't take much longer than an hour or two if all goes well.

I forgot to mention that if you want to use IMAP or POP3 access, something like [Dovecot]("https://help.ubuntu.com/community/Dovecot") might be useful.

I've found that looking for ways of limiting incoming spam can be a rewarding way of filling up time.

---

