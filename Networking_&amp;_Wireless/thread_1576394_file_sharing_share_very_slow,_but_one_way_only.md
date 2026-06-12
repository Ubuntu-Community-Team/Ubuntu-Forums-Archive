---
title: "file sharing share very slow, but one way only"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by gm_w on 2010-09-17
i have 2 PCs in my home network, one laptop running ubuntu 10.4 and the other desktop running windows 2008 server R2. 

If i am using my windows machine, I can upload and download files to ubuntu machine at around 2MB/sec. This is what I expect.

But If i am using my ubuntu machine, the upload speed to windows machine is 2MB/sec, but the download speed from windows to ubuntu drops to 140KB/sec. This is too slow.

Most of the time my ubuntu laptopis connected using wireless (54Mbps) and desktop is wired ethernet. I also tried to using ethernet on my ubuntu laptop and the transfer speed is the same 140KB/s from windows to ubuntu.

Can anyone help me to solve this?

---

### Post by DirtDart on 2010-09-17
Can you post the output of *ifconfig *and *iwconfig*?

It sounds like you might have an issue with errors and/or collisions.

---

