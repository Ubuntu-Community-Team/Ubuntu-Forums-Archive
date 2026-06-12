---
title: "Network problems"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Nietzsche on 2006-06-02
Please excuse me being a total newbie and if the problem and solution seem totally obvious have pity on my utter technological inepcy...

Anyway I've just installed Dapper on a laptop and everything is working fine except for the network:
Dapper seems to recognise the wireless card and can properly interface with it.
I can actually ping both the wireless gateway and web addresses like google.com but anything else that would require internet connection just doesn't work. Firefox will be "connecting to google.com" eternally. Gaim also will refuse to sign in.

Interestingly enough the same exact thing happened in a desktop installation of Ubuntu 5.04 with an ASUS w-154 wireless card (this time however I had to go thorugh the pain of setuping ndiswrapper and whatever), I did not know about this forums  and as such I gave up and scrapped the ubuntu partition :(

---

### Post by mips on 2006-06-02
Disable IPv6 globally.

```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a
```

---

### Post by Nietzsche on 2006-06-02
Sorry but didn't work :(

got this error message in terminal:
mv: cannot stat `/lib/modules/2.6.15-23-386/kernel/net/ipv6/ipv6.ko': No such file or directory

---

### Post by mips on 2006-06-02
In the firefox address/URL space type    "about:config"    , scroll down to    **network.dns.disableIPV6 = false**    ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

**Save and reboot your PC**.

---

### Post by Nietzsche on 2006-06-02
Writing this line on Ubuntu and cannot thank you enough :)

---

### Post by kevindubrow on 2006-10-05
Hey I'm having the same problem, but those suggestions didnt fix it. Any other ideas? Thanks.

---

