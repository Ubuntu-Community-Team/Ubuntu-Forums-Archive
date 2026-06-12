---
title: "Can't Upload"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by broken tibula on 2009-05-19
I can't upload anything from my computer.  I know that it's my computer, because my mother's works fine using the same internet.  I can download everything just fine, but when I go to upload, nothing happens.  A test on [www.speakeasy.net/speedtest](www.speakeasy.net/speedtest) shows the download speed as normal, but when it goes to test the upload speed, it says that it has "Upload test returned an error while trying to read upload file." 

Google hasn't given my anything, except talk of firewalls, which it obviously isn't.  Any suggestions?

(I'm on Jaunty, on a Dell laptop, if this helps)

---

### Post by broken tibula on 2009-05-21
Bump.  Anyone?

---

### Post by superprash2003 on 2009-05-21
post output of sudo iptables -L from the terminal , you could try changing MTU values [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by broken tibula on 2009-05-21
Here's the output--I have to run off to take a final now, but I'll check out the MTU when I get back.  Thanks so much!

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

---

### Post by broken tibula on 2009-05-30
I tried changing my MTU values, but it didn't work.  Any other suggestions?

---

