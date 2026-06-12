---
title: "wvdial connects but no data"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by chanders on 2009-01-20
So a little history..

wvdial connects with no problem
Computer is assigned both a local and remote IP address
It is also assigned a primary and secondary DNS address
No other network cards are connected

When the connection is made and i try to visit a site, the first few connections go through because I can see part of the page opening up and then it all stops. The status bar for Firefox shows " connecting to ...... " but no more data appears.

Is there a way to determine if the connection is choking or a reason why no data is coming through after the first few connections??

---

### Post by dmizer on 2009-01-20
Are you sure it's making use of the DNS servers? Mine never did.

Try this: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)
(be sure to follow the directions under "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:")

---

### Post by chanders on 2009-01-21
DNS is being updated in resolv.conf properly. Is there somewhere else I need to check?

---

### Post by dmizer on 2009-01-21
Try this? [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

