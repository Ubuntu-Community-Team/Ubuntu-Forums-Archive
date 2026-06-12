---
title: "Acer Aspire 4315, AR5BXB63 (AR5007?) doesn't connected"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by HuuThanh Nguyen on 2009-11-06
I upgrade (and after that) install fresh Ubuntu 9.10. Both cases Wifi worked but have not connected. Always ask WEP password. How can I do now, please help.

---

### Post by arjuntank on 2009-11-06
well, its a wireless connection with a WEP. so you need to enter the passphrase first to get connected. that would solve the problem.

---

### Post by HuuThanh Nguyen on 2009-11-06
Yes, I know. I typed exactly password on my laptop. But it did not connect.
Before now I run Ubuntu 8.04 with Madwifi as [here]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform-2.html")

---

### Post by arjuntank on 2009-11-06
> **HuuThanh Nguyen said:**
> Yes, I know. I typed exactly password on my laptop. But it did not connect.
Before now I run Ubuntu 8.04 with Madwifi as [here]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform-2.html")

okay, so you can see the wireless connection in the network manager but could not connect to it. try to see what type of error message it gives, like authn failed something like that.
select your wireless connection and click properties and then change the IP assignment. These settings should be exactly how the wireless router is configured to. if the properties dialog box shows automatic ip assignment enabled, then you might want to enter specific ip default gateway and subnet by disable auto ip assignment. that is no dhcp.

---

### Post by HuuThanh Nguyen on 2009-11-06
I tryed. But didn't success.

---

### Post by arjuntank on 2009-11-07
did you tried to install wicd instead of the default network manager?

---

### Post by HuuThanh Nguyen on 2009-11-07
I don't know about wicd. As your word, I see it by Synaptic. If I install wicd, what can I do with default Network Manager?

---

### Post by arjuntank on 2009-11-07
> **HuuThanh Nguyen said:**
> I don't know about wicd. As your word, I see it by Synaptic. If I install wicd, what can I do with default Network Manager?

uninstall the network manager from synaptic and install wicd and reboot.

---

### Post by HuuThanh Nguyen on 2009-11-07
I did as Mark Rijckenberg said in the link
[https://answers.launchpad.net/ubuntu/+question/74211](https://answers.launchpad.net/ubuntu/+question/74211)
Now it work well.
Thanks all for help.

---

