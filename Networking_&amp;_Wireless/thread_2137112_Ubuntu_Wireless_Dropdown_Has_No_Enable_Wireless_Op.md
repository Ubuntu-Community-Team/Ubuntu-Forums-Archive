---
title: "Ubuntu Wireless Dropdown Has No Enable Wireless Option"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by masterkrang on 2013-04-19
I have installed Ubuntu 12.10 on my Acer Aspire mini desktop, and now I'm having trouble with my wireless connection. I turned off the wireless, by disabling it in the dropdown menu, but now I can't turn it back on. If I click Enable Wireless, nothing happens, the icon remains the same, without bars. I wish I new some way to enable the wireless again from the command line but I don't. This seems like a bug to me. Any help? Thanks!

---

### Post by praseodym on 2013-04-20
Try
```

sudo service network-manager restart
```

---

