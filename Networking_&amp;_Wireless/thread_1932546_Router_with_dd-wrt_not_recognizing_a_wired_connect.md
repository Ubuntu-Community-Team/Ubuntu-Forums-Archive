---
title: "Router with dd-wrt not recognizing a wired connection"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by 39er on 2012-02-27
Hello community,
I am attempting, with a PC running Ubuntu LTS10.04, to connect to the Buffalo WZR-HP-AG300H router but the router refuses a simple wired ethernet connection.

However, without changing any of the parameters required at initial installation, I **can connect** with the PC via ethernet to a Lynksys 3000 running their firmware and I am **able to connect** with a Windows O/S to the WZR... router.

The router comes of the shelf with their latest dd-wrt build 15940. I am stumped and at this time would not know what other information I should supply for expert advise for a solution from the community.
Thank you very much for any help.
-39er

---

### Post by 39er on 2012-03-01
The solution is quite simple. I am listing it here just in case others are using routers with DD-WRT firmware. 
_Solution:_ "**DNSMasq for DNS**" needs to be **un**checked (tick mark) in the basic setup menu. DNSMasq is a specific feature of the DD-WRT firmware.

Now Ubuntu Linux is able to be used with routers flashed with DD-WRT.
-39er


> **39er said:**
> Hello community,
I am attempting, with a PC running Ubuntu LTS10.04, to connect to the Buffalo WZR-HP-AG300H router but the router refuses a simple wired ethernet connection.

However, without changing any of the parameters required at initial installation, I **can connect** with the PC via ethernet to a Lynksys 3000 running their firmware and I am **able to connect** with a Windows O/S to the WZR... router.

The router comes of the shelf with their latest dd-wrt build 15940. I am stumped and at this time would not know what other information I should supply for expert advise for a solution from the community.
Thank you very much for any help.
-39er

---

