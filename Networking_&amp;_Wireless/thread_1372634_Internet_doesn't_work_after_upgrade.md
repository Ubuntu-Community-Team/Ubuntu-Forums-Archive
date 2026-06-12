---
title: "Internet doesn't work after upgrade"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by ThePickleMan on 2010-01-04
Hi,
I just upgraded from 9.04 to 9.10.
When I restarted, I admired the new login menu, then went to Firefox. I noticed that my wireless didn't work (it did in 9.04) Thinking I'd just need to reinstall the drivers, I plugged in the computer to a working Ethernet outlet with a working cord. I noticed that Ubuntu didn't tell me that Auto eth0 was connected. It didn't tell me anything. And then I went to Google and realized that the wired connection didn't work either. Then I came here on an iPod Touch and you know the rest. Please help!


Edit: And other devices work too on the network. 


Thanks in advance!

---

### Post by sylvester_0 on 2010-01-04
Verify the content of your /etc/network/interfaces file:

```
$ sudo gedit /etc/network/interfaces
```

It should look like this:

```
auto lo
iface lo inet loopback

```

Also, verify that network manager is running:

```
$ pidof NetworkManager
```

If it's not, try running it in a terminal and looking at the output.

---

### Post by ThePickleMan on 2010-01-04
It's the same, and yes, it's running.

---

