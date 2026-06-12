---
title: "Ubuntu 9.10 Firefox File Upload not Showing Network Shares"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by robinhood_x on 2009-11-27
Hi

We have an issue with Ubuntu 9.10, where firefox does not show network shares in the bookmarks when doing a file upload.

Although the shares exist and are visible elsewhere, Firefox file upload will not display them. This is causing some quite serious problems for us.

Does anyone else have this problem and a solution?

Thanks

---

### Post by larseko on 2009-11-27
I can confirm this problem here. We've had problems with network shares not being visible in some file selection dialogs since a 8.04 if I recall correctly. 

(Some of the reorganizing of network shares in GNOME/nautilus lately also has been a bit confusing for users here at the school I work. For instance not being able to have network shares on the desktop anymore, moving over to a bookmark model instead of folder-ish model.)

---

### Post by xyntek on 2009-12-18
I have beiong having this problem too since 8.04

---

### Post by xyntek on 2009-12-18
I fixed it. You need to change your MTU. MTU (Maximun transfer Unit) is the bigest size that can be one packed to be sent and received through the net. Normally MTU from routers are 1500. You can fix this by to ways:

Before doing the fix, first find you optimal MTU, for this type in console:

[FONT="Courier New"]ping -s 1442 -c1 google.com[/FONT]

you should receive something like this:

[FONT="Courier New"]PING google.com (***.***.***.***) 1442(1470) bytes of data.
1416 bytes from yo-in-f147.1e100.net (64.233.169.147): icmp_seq=1 ttl=242 (truncated)

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 130.348/130.348/130.348/0.000 ms

[/FONT]

When you have this, it means that the package sent and received was done good. Keep playing with the number (1442) until you find an optimal number. When you have in the results 0 received and 100% lost, lower down the number -1 (e.g. 1441) and write down that number or remeber it.

Now that you found that number, you need to change it in your connection. You can do this by two forms:

**Fix 1 (from Ubuntu):**

Open your network connections. Under the Wired tab mark Auto eth0 and click edit. In the MTU change for the number you found. Click Apply and close. Disconnect and connect again you network. Now you changed you MTU. To verify, go to your internet based wedmail (e.g. Gmail), try to write down an email and upload a file. Send it to your self and verify if you received everything. 

[B]Fix 2 (from router):
[/B]
Check you router company how to edit your MTU. Change it and try the test I mentioned in Fix 1.

Hope this works for you.

---

