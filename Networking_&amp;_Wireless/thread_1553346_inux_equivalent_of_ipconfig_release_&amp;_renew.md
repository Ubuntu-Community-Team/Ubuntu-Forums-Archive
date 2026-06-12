---
title: "inux equivalent of ipconfig /release &amp; /renew?"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by conradin on 2010-08-14
Hi all,
Im looking for an equivalent to Linux equivalent of ipconfig /release & /renew (ms windows) for Ubuntu.

I have seen a thread under the same title from 2006, recommending 
```

sudo ifdown
sudo dhclient -r

```

for releasing my connection. However, I can still connect to the web, without any loss in connection that I can detect. Whats going on here?
How can I release my IP? Why am I still connected?

---

### Post by sgosnell on 2010-08-14
Read the man page for ifconfig, specifically up and down.  That should help you.

---

### Post by conradin on 2010-08-15
Ok Thanks! 
I got it now. ifup / down seem to do nothing for me, but 
# ifconfig [cenection] down 
works to disable the connection. At what level disabling the driver acts to release the IP address I do not know, on site we have static IP addys based on MAC addy. Still I would like to flush any cache for the device  which I do not see in the man page for ifconfig.

---

