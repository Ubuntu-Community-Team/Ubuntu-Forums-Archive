---
title: "Unstable internet connection (realtek)"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by akegalj on 2011-03-11
Hi all

Im new to linux (2 days only) so i have some driver problems. My internet connection is unstable. It reconnects every few minutes (5 min approximately). Im connected with wired dsl connection to routher. My network adapter is "Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller". I use Ubuntu 10.10 Maverick Meerkat release, kernel 2.6.35-27-generic.

Did someone had this problem? 

Please help,
Ante

---

### Post by dandnsmith on 2011-03-11
Have you established whether the link which is dropping is PC to router, or router to internet? (router should log this for you).

If it is router to internet, has that connection been used for any other purpose - if so, was that more stable?

---

### Post by akegalj on 2011-03-11
i was trying to find where can i get that log information, can somebody tell where is it stored?

---

### Post by dandnsmith on 2011-03-16
Sorry - been away for a while.

The log I refer to is kept on the router, but how you find it is up to the interface which the router provides to the user. Can't even guess short of some router particulars.

---

### Post by citrix on 2011-03-18
I have started observing the same problem from  past couple of days now. Does not look like the problem with my router since I am able to reconnect after repeated refresh from Firefox (I am able to connect from my XP machine through the same router on the same desktop - dual boot) . Following are the kernel and network card details (there is no wireless card). 

2.6.35-27-generic
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

Anyone please let me know whether I have to recompile the latest kernel or there is a patch available.


Thanks

---

### Post by dandnsmith on 2011-03-20
Citrix - that is the same designator as the ethernet card I'm using.
In my case I'm running 10.04, with no changes to the kernel, so perhaps it's something in the later version of kernel/drivers, since my setup exhibits no such symptoms.

HTH

---

