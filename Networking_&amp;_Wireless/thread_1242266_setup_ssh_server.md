---
title: "setup ssh server"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-08-17
Hi,
I set up a SSH server on my Ubuntu on my laptop by OpenSSH. While ssh localhost is okay, I try to first ssh to another computer from, and then from there ssh back to my laptop with its external IP address but it fails with "connect to host xxx port xxx: Connection timed out".
My laptop is connected to the internet through a router with Comcast as the provider. 
What is the correct way for setup or connection?
Thanks and regards!

---

### Post by slakkie on 2009-08-17
You need to enable portforwarding on port 22 for ssh to work.

---

### Post by flylehe on 2009-08-17
Thanks!
How to enable portforwarding on port 22?

---

### Post by slakkie on 2009-08-17
See your router manual or this page: [http://portforward.com/](http://portforward.com/)

---

