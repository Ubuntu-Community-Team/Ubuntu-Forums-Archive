---
title: "how to increase broadband speed"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by asif_1088119 on 2009-12-17
hi.i want to know if there is any code or something so that i can get more bandwidth than i m alloted by my internet service provider...i live in a third world country like bangladesh,,,i get 10 kBps for downlaod in an average...my ISP was supposed to give 12 kBps...if there is any way to get something like 100-200 kBps please let me know....thanx in advance

---

### Post by Linuxforall on 2009-12-17
> **asif_1088119 said:**
> hi.i want to know if there is any code or something so that i can get more bandwidth than i m alloted by my internet service provider...i live in a third world country like bangladesh,,,i get 10 kBps for downlaod in an average...my ISP was supposed to give 12 kBps...if there is any way to get something like 100-200 kBps please let me know....thanx in advance

You can't exceed your advertised broadband speed but make sure you selected the right MTU value in network manager for your connection. You can use the tools at dslr or speedguide.org to determine your MTU.

---

### Post by asif_1088119 on 2009-12-17
is there any hacking tools to exceed my advertised bandwidth???let me know please...it takes 24 hours for downloading a 700 mb movie

---

### Post by sliketymo on 2009-12-17
> **asif_1088119 said:**
> hi.i want to know if there is any code or something so that i can get more bandwidth than i m alloted by my internet service provider...i live in a third world country like bangladesh,,,i get 10 kBps for downlaod in an average...my ISP was supposed to give 12 kBps...if there is any way to get something like 100-200 kBps please let me know....thanx in advance

Find a service provider that supplies a larger bandwidth limit.For what it's worth,you are asking this members of this forum to provide you with information to assist you in an illegal activity.Not a good idea.

---

### Post by tigerdiva on 2011-03-15
Hi friend, first make sure that you Log on as Administrator, not as a user with Administrator privileges.
 * Start > Run > type gpedit.msc
* You will see [Local Computer Policy]
* Expand the [Administrative Templates] branch
* Expand the [Network] branch
* Highlight [QoS Packet Scheduler]
* Double-click [Limit Reservable Bandwidth]
* Check [Enabled]
* Change [Bandwidth limit %] to 0 %
* Click [Apply] [OK]
* Restart
 Effect is immediate.


You can also use this website **[http://www.ip-details.com/internet-speed-test/](http://www.ip-details.com/internet-speed-test/)** to check the current  speed of the broadband at free of cost......

---

### Post by slauper on 2011-08-23
Hi tigerdiva,
Your advice is a Windows media streaming reserved bandwidth remover and it doesn't work for Ubuntu.

---

