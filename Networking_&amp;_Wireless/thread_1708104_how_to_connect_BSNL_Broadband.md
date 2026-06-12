---
title: "how to connect BSNL Broadband"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by pankajnere on 2011-03-16
please tell me how to connect BSNL Broadband(with type II modem) in ubuntu.

---

### Post by dineshs on 2011-03-17
Hope your modem is connected via ethernet port.
If your modem is in PPPoE mode (username and password stored in modem) the connection should work automatically(Assunming DHCP is enabled in the modem)
If the modem is in bridge mode try this
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)
If you have any difficulty pl post the result of the following command ```
sudo lshw -C network
```
Also can you tell us the modelname of your modem?

---

