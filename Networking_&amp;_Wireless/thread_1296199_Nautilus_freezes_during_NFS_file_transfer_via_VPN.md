---
title: "Nautilus freezes during NFS file transfer via VPN"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by YesWeCan on 2009-10-20
Hi, I am new to linux and have been using ubuntu for about 4 weeks. I will never buy a Microsoft product again.

I have set up a VPN routed link between my ubuntu 9.04 PC and a SuSE 11 PC 3000 miles away. The SuSE is an NSF server and I have mounted its filesystem on ubuntu.

When I use Nautilus GUI to copy a large file (20MB) from SuSE to ubuntu it works fine and a progress bar updates continually. However, when I transfer the same file the other way, from ubuntu to SuSE, the progress bar freezes and Nautilus hangs. The file transfer happens, however. This condition persists until the file finishes being transfered and then Nautilus defrosts and works fine again. This is a problem because I cannot use the filemanager nor can I do 'ls' from a terminal while the transfer is occuring. I can stop the transfer by trying to close the Nautilus progress window but it takes several minutes to close.

I have tried 2 files. On a 700MB file the progress bar reaches about 60MB before it hangs. On the 20MB file the progress bar immediately shows 20MB of progress (even though there has been no progress) and hangs.

I don't know whether this is related to the VPN or not. The VPN appears to work fine.

Any ideas?

---

### Post by YesWeCan on 2009-11-04
This also happens when ubuntu 9.04 64-but desktop is the client and ubuntu 9.04 server is the host.

---

### Post by fbarcenas on 2010-05-17
This is not related to the VPN. I'm not using a VPN and it happens to me as well. But for me it began when I upgraded to Lucid. I was using 9.10-64 without a problem.

It's really annoying to have to wait for the computer to transfer to do anything.

---

