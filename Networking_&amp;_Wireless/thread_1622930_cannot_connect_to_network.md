---
title: "cannot connect to network"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by brothersamati on 2010-11-16
I reported recently that I have a problem connecting to a Windows network, and someone suggested upgrading to Ubuntu 10.4  I have done, and still have the problem.

The error message I get is:  "Unable to mount location.  Failed to retrieve share list from server".

---

### Post by deconstrained on 2010-11-16
What kind of service is it? Maybe you don't have the proper client utilities installed for it, in which case samba4-clients might be the pacakge you need.

---

### Post by linux-hack on 2010-11-16
If you are on windows networks you need to install samba. This allows you to connect or share files/folders with windows machines and much more.

---

### Post by brothersamati on 2010-11-17
I tried installing samba4 client (which involved uninstalling the previous samba installation) with the same result.

There have been more or less long periods when ubuntu has been able to access the network.  Then something happens and for a few months it goes wrong again, without my having done anything that I'm aware of.

---

