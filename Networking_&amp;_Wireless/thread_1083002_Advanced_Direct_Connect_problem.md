---
title: "Advanced Direct Connect problem"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by abds on 2009-02-28
Hey

I have an advanced direct connect hub set up at my university. The hub is up and working fine, people can connect to it and everything. But I cant seem to connect to it. It seems to be a problem with my client (the same client worked with a previous direct connect hub but that was blocked by the network admins, so we had to move to advanced direct connect). I am using LinuxDC++. When I try to connect I get the following error:

*** Connect failed: SSL Error: error:00000006:lib(0):func(0):reason(6) (0, 6)

I thought that LinuxDC++ supports advanced direct connect. Does anyone have any idea as to y i am getting this error? or suggestions for another client i might be able to use?

---

### Post by bkaskar on 2009-03-12
I don't know what or how you use Linux DC+. But SSL error 6 is generally when you (or your app) don't accept the trust cert.

If your univ has its own CA then you may have to add the root cert to you app/new install as it might not be the standard 3rd party CA.

---

### Post by ouker on 2009-08-07
You can get into the "preferences" and change the default ip to your new ip or 0.0.0.0

---

### Post by roxywatson001 on 2011-09-27
Dear Firstly check out in Device manager any unknown device is found or not. If it found then install it manually.

---

