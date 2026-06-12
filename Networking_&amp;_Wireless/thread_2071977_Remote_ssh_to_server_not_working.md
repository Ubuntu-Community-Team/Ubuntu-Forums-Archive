---
title: "Remote ssh to server not working"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by MortenSJ on 2012-10-16
Hi

I just setup ddclient so i can get in contact with my server from the outsite. It all works fine, but i can't seem to ssh into my server.

When i type in ssh [email]username@url.serverurl.com[/email] i get this error.

ssh: connect to host url.serverurl.com port 22: Connection refused

I tjecked my port forwarding and port 22 is open.

---

### Post by ahallubuntu on 2012-10-16
First of all, does ssh access work from the INSIDE if you try accessing it via its local IP address on your internal network?

If so, then does it work using your external IP address (not a DNS name)?  If not, then port isn't being forwarded correctly.  If it works with the IP not the name, then the name isn't being resolved correctly.

---

