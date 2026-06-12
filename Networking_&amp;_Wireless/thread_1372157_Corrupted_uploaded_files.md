---
title: "Corrupted uploaded files"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Toufik on 2010-01-04
I've tried to upload some pictures on a server but the remote version of the files was corrupted (weird colours and ghost images). After further tests, it think something weird is going on during the transfer. I've computed the md5 sum of the local files and remote files, they are modified during the upload while kept identical during a download (i.e. compute md5 (A) of a file, upload it, compute the md5 on the server (B), download it and compute the md5 locally (B) ).

Local copy on different partition or external drive is ok, this only appears during a remote copy.

I have tried :
- different server
- different protocol (ssh, ftp, web uploader, msn)
- different files
- different computer (one running Ubuntu, another running Vista)

Well, the only remaining cause seems to be the modem but that sounds a bit weird. Does anyone knows another explanation? Or a way to test the modem (before buying a new one since I don't have any other one)?

---

