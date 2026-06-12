---
title: "How to force eth0 to 10 Mbps Full Duplex"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-03-25
Hi,

I have a wired Cat5 network at home and I don't know why but it works OK only at 10 Mbps. Cable length, cable quality, router and switch should be OK (but I don't know how to check the hardware).

Some computers can auto-negotiate and set on 10 Mbps. But for some others, failed and end up in disconnected status in Ubuntu or "limited connectivity" in Windows.

Internet searches has pulled up a few posts & blogs where people advise about using mii-tool or ethtool. But it has to be done manually each time the computer boot.

I would like to set the network interface permanently to 10 Mbps Full Duplex. Can you please show me how to do that?

And BTW, what is the difference between mii-tool and ethtool?

Thank you very much in advance.

---

### Post by chili555 on 2009-03-25
You might try adding this to */etc/rc.local:*```
ethtool -s eth0 speed 10 duplex full autoneg on
```

---

### Post by UranUtan on 2009-03-25
Super, thanks for indicating the file to keep the setting permanent. Will try this tonight.

> **UranUtan said:**
> And BTW, what is the difference between mii-tool and ethtool?
Got the answer here: [http://ashterix.blogspot.com/2006/05/mii-tool-vs-ethtool.html](http://ashterix.blogspot.com/2006/05/mii-tool-vs-ethtool.html)

> mii-tool vs ethtool

Both commands are actually doing the same things. An useful tool to display or change ethernet cards settings, but bear in mind that mii-tool only for 10/100M NIC while ethtool can support all hardware. So in case you are using GB cards, you should use ethtool then.


And more importantly, mii-tool is obsolete [http://linux.die.net/man/8/mii-tool](http://linux.die.net/man/8/mii-tool)
> This program is obsolete. Valid media are only 100baseT4, 100baseTx-FD,100baseTx-HD, 10baseT-FD and 10baseT-HD ethernet cards. For replacement check ethtool.

---

