---
title: "Configuring BSNL broadband"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by SwatKat on 2009-10-31
Hi
I know this topic has been discussed before, but none of the suggested solutions seem to be working for me.

I have installed Ubuntu 9.10 using Wubi installer but I am unable to connect to the internet.

I tried sudo pppoeconf but got msg in Screenshot(Attachment)

I also tried sudo dhclient eth0 (screenshot3) but that doesn't seem to be working either.

I attempted setting up a static IP address, but I lose the Apply option as soon as i change the method to Manual in IPv4 settings(Screenshot 1)
Is the option not available in Ubuntu installed without a dedicated partition( Using Wubi) or did I miss something?
sudo ifconfig gave this output(Screenshot 2).

I can connect to the net by just switching on the modem in Windows.

I am a complete noob to linux, so clear step by step instructions
would be much appreciated.Thanks.

---

### Post by arnab_das on 2009-11-02
BSNL servers are down most of the time. try using the sane steps now.

---

### Post by SwatKat on 2009-11-02
I got it. My DHCP server was disabled. I realized it immediately after posting the question in this forum :o . My friend had the same problem and I could fix it (Much to her admiration) without any terminal commands by just enabling DHCP server.

---

### Post by GIRI MURALI on 2010-05-20
i think Ubuntu can automatically detect bsnl broadband.but if you need a dialer for connecting internet it will be difficult.So you need to avoid the the dialer
[http://www.beubuntu.co.cc/2010/03/connect-bsnl-broadband-in-ubuntu-hai.html](http://www.beubuntu.co.cc/2010/03/connect-bsnl-broadband-in-ubuntu-hai.html)

---

