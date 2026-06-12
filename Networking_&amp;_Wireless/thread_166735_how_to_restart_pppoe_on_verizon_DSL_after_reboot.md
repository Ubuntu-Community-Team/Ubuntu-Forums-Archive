---
title: "how to restart pppoe on verizon DSL after reboot?"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by tommcd on 2006-04-27
Hi. I installed Ubuntu 5.10 on an old Emachines computer. The Realtek erthernet adapter is correctly identified. To get online with verizon dsl I had to use sudo pppoeconf in terminal. I answered a bunch of questions (gave default "yes" to all, including enable connection on boot up). The pppoeconfig said to enable connection you can use pon dsl-provider, and to stop connection use poff.
Problem is, everytime I boot up or restart the computer I have to do sudo pppoeconf all over again. Is there an easier way to enable the DSL connection on boot up? Or do you have to do pppoeconf each time?
Any advice appreciated thanks

---

### Post by tommcd on 2006-04-27
Bump for another shot.
Anybody use DSL with PPPoE? How do you enable the connection at bootup?

---

### Post by cjwworld on 2006-04-29
](*,) I also use dsl but I have the same problem.  This is the reason I stop tinkering with Ubuntu because it is an hassle.  I have not received any help.  Although many suggestions and I go thru it but doesn't help.

---

### Post by mips on 2006-05-02
Do a search here for Verizon.

You both probably have routers and don't know it. You can configure the router to do the PPPoE & authentication stuff. This way you don't even need it on the PC, just DHCP.

---

### Post by machas on 2006-06-07
So, can somebody say how? step bay step ....

---

