---
title: "want to configure wlan0 interface with static ip"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by houserparker on 2010-05-19
I've looked everywhere and tried everything. All I want to do is set up a static ip with my wireless network interface wlan0.

Can someone direct me?

Thanks in advance.

---

### Post by dineshs on 2010-05-19
pl try if these links can help
[http://www.uluga.ubuntuforums.org/showpost.php?p=8975701&postcount=2](http://www.uluga.ubuntuforums.org/showpost.php?p=8975701&postcount=2)
(to remove NM)
[http://ubuntuforums.org/showpost.php?p=3901846&postcount=2](http://ubuntuforums.org/showpost.php?p=3901846&postcount=2)
(to configure /etc/network/interfaces)

---

### Post by houserparker on 2010-05-20
Hi Deneshs,

Thanks for the links.

They did look very promissing but no luck yet. I'll some how manage to get this configured.

Cheers,

---

### Post by houserparker on 2010-05-20
If anyone is willing to help me with this I will be happy to post a tutorial regarding this as there seems to be no specific documentation.

Thanks,

---

### Post by puppywhacker on 2010-05-20
Hi,

The official documentation is at 

[https://help.ubuntu.com/10.04/internet/C/connecting-wired.html#connecting-wired-manual](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html#connecting-wired-manual)

1. Right click the Network Manager icon in the system notification area and click Edit Connections.
2. Click the Wired tab, select the connection and click Edit.
3. Click the IPv4 Settings tab and choose Manual from the Method drop down list.
4. Click Add and enter your IP address and other details. Enter the address of your DNS server too.
5. Click Apply. The network should now connect if you entered the settings correctly.

But there are plenty of working alternatives like bypassing the network-manager and replacing it by wcid, or by configuring the /etc/network/interfaces file or temporarily set it on a commandline with "sudo ifconfig wlan0 inet 192.168.0.1"

P.S. Where it says "wired" that would also apply to wireless, just click the wireless tab in step 2.

---

### Post by houserparker on 2010-05-20
Thankyou puppywhacker

I had already tried this but overlooked the DNS field and now it works thankyou.

---

