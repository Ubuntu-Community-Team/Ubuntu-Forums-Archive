---
title: "Ubuntu12.04 - Missing my wireless network - how to change cfg80211 setting"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by warti on 2012-04-28
Hello,

I miss my wireless network on channel 13. 

The CRDA/cfg80211 setting (checked with dmesg) is using "US". But I'm here in Germany. Everything in the system is set to "German". 

How to change the  CRDA/cfg80211 in Ubuntu 12.04  best to "German"

Thanks

---

### Post by jawilljr on 2012-04-28
Try this command:

```
sudo iw reg set DE
```

Jerry

---

### Post by warti on 2012-04-28
thanks.

Put how to get it persistent at start-up?

---

### Post by chili555 on 2012-04-28
You can try:```
sudo iw reg set DE
```If that does it, edit /etc/rc.local and put it in above *exit 0* but without sudo.

---

### Post by jawilljr on 2012-04-28
You can try to put it in '/etc/rc.local'.

Put the command before the 'exit 0'.

Jerry

---

### Post by warti on 2012-04-28
Thank You both very much - the first step is done. I see now my own network. ):P:p

(But I still can not connect to it - but this is another story. First I will try to sort this out on my own)

---

