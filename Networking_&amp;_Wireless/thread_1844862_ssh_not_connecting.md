---
title: "ssh not connecting"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by dansang on 2011-09-15
Hi i have two ubuntu machines desktop 10.04 and laptop 11.04. On the  desktop that i have set up openssh- server and on the laptop openssh-client. when ever i try the 

```
ssh ipaddress
```

or

```
ssh user@ipaddress
```

from the laptop i get a port 22 connection refused error.

i have followed how-to's from the ubuntu forums with out any luck.

I have a t-mobile broadband account on the desktop so no router's! On the laptop i have a btopenzone connection.

i doubt the isp thing matters as i had teamviewer working on this ubuntu to ubuntu set up before.

My friend said it maybe an SElinux problem or a firewall problem.

I attempted the firewall problem and installed firestarter on each machine and allowed ports 22 on the firestarter settings, which i think i did correctly.


Could anyone please give me some advice as i will be needing to set up ssh for a ubuntu server in the near future.

So far i have failed badly.:confused:

---

### Post by SeijiSensei on 2011-09-16
Are you sure SSH is actually running on the desktop?  Try "sudo server ssh restart" to make sure. Another simple test is to try "ssh localhost" on the desktop to make sure you can connect to the machine from itself.

---

