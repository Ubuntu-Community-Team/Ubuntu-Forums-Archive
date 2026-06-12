---
title: "software to extract files from network trace"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by jmartrican on 2009-01-30
hello,

Anyone know of any software that can be used to extract files (html, gif, jpeg) from network traces (wireshark, libcap)?

I saw Network Miner but its for windows and I didn't want to mess with Wine just yet.

---

### Post by nixscripter on 2009-01-31
For HTTP (web browsing) transactions, Wireshark itself can do that. There are two ways:

First, if you open a capture file, under the menu File->Export Objects->HTTP (I think it is), you can save individual objects captured over HTTP transactions.

Second, you can filter http packets (the filter **http.content_type** should do), select them individually, and then right click the data and say Save Selected Bytes.

Hope this helps.

---

### Post by jmartrican on 2009-02-01
Thanks for the tip.  I'll give it a shot.

---

