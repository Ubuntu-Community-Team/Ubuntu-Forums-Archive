---
title: "Popcorn hour A100 with Ubuntu 8.10 and NFS"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by n4h0j on 2009-04-18
Hi.

I am trying to set up my Popcorn hour with my computer so I can play all my movies. But it wont work. No way. After 4 hours of trying every single guide on the web (at least it feels that way) I give up.

Can anyone here who got a working setup post their /etc/exports ?

Please help me!

/Johan

---

### Post by peakshysteria on 2009-04-18
A bit more info would help us help you. I had some issues in the beginning right after I got it. But after some back and forth struggling it worked like a charm in Intrepid. After upgrading to Jaunty (Beta) it still runs smooth. Mainly streaming now. But I have put a HDD in it to make it easier for the kids.

---

### Post by n4h0j on 2009-04-19
Well, I am trying to set ut a NFS-server on my computer so that I can share my movies on the network. And I am not getting it right.

So, I would need someone who got it working to share their /etc/exports, so that I can try their version of settings.

---

### Post by n4h0j on 2009-04-19
I solved this issue now. I added the following line in my /etc/exports
```
/path_to_folder 192.168.0.0/24(rw,async,subtree_check)
```

Where path_to_folder is replaced with the actual path. =)

---

