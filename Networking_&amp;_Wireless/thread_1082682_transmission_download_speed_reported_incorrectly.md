---
title: "transmission download speed reported incorrectly?"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by lordharsha on 2009-02-28
I've got a doubt concerning Transmission (the bittorrent client):

If the download speed in Transmission is, say, 30 KB/s, then conky reports that network usage is around 40 KB/s. There's nothing else using the network, and if I close Transmission, the speed goes down to 0 KB/s

Is this to be expected from a BT client, or is there something wrong with transmission?

---

### Post by NoReflex on 2009-02-28
Hello!

I haven't used Transmission that much - in my opinion Deluge is a far better client. Anyway in deluge status bar it reports the following : upload speed, download speend and "Protocol traffic Upload / Download" which is around a few KB/s each; so this could be a cause for the reported speeds difference. 
If you want to verify this you could try using iftop (it's in the repos).
I recommend Deluge though...

Best wishes,
NoReflex

---

### Post by lordharsha on 2009-02-28
I started using deluge soon after I posted this. Seems to reduce the extra bandwidth used if the number of peers is small. Goes up again if there are a lot (50+). I can understand an increase in upload speed, as it needs to acknowledge the packets received. Still doesn't explain the increase in download speed.

Also, the version in hardy doesn't display protocol traffic. This might sound like a stupid question, but does hardy still get updates (not security updates) for regular packages like deluge. I noticed that v1.1.3 is only available for jaunty.

Thanks.

---

