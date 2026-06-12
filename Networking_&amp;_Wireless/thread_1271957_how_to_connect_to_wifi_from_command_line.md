---
title: "how to connect to wifi from command line?"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by Pitt Stains on 2009-09-21
Hi,

I'd like my laptop to connect to any wireless available network before I log in, but I'm not quite sure how to achieve this.

Why would I do this, you ask?  I'm modifying a script someone else wrote to phone home every time the laptop is turned on, even if the person in possession of the laptop (aka thief) can't log in.  It's not a great anti-theft system, I know, but I just had a laptop stolen, and I'm kicking myself for not having taken more measures to protect my machine and my data.  Plus, I'm a geek and this kind of thing gives me satisfaction.

I've read that I should be able to connect to any unencrypted wifi connection by issuing these commands from the command line, but I've had no success.  The first command gives no output, and the second eventually times out (No DHCPOFFERS received).

```

iwconfig <interface> essid any
dhclient <interface>

```

I've added my shell script to /etc/rc.local, but to test things out, I'm logging into the shell instead of the GUI and running my commands from there.  Any thoughts?

Thanks,
-Pitt

---

### Post by Pitt Stains on 2009-09-25
Can anyone lend some insight?  Thanks!

---

