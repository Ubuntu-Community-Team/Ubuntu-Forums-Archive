---
title: "Can I put Network Manager 8 on Hardy?"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by desconocido on 2010-05-27
Hello everyone,

I am running Ubuntu 8.04 (Hardy Heron), Kernel 2.6.24-24.
Because everything is working fine, I would be **very** reluctant to upgrade to 8.10 or later.

However I now have a need to use a Mobile Broadband USB connection to the Internet. I understand that this requires Network Manager 7.something or later.

I got the network-manager (0.8-1) binary from debian. Anyone got any experience of whether I should be able to install it succesfully? I thought I would ask before wrecking my system.

(Synaptic seems to only allow me version 0.6.6)

---

### Post by wilee-nilee on 2010-05-27
Take a look at this PPA you will have to do the research. WICD is a pretty good alternative if your having problems, and you can get WICD off the web rather then from a repo.
[https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)

---

### Post by desconocido on 2010-06-04
> **desconocido said:**
> 
I am running Ubuntu 8.04 (Hardy Heron), Kernel 2.6.24-24.
Because everything is working fine, I would be **very** reluctant to upgrade to 8.10 or later.

I thought I would ask before wrecking my system.


Ha! I decided try the synaptic upgrade path to 8.10. After the sixth hour, someone tweaked the power cable that was charging the battery, X vanished, I was dumped into what looked like a console terminal, with the message "anachron stopped" or started. Unplugging the power cable and reinserting it seemed to have the the effect of flipping anachron between stopped and started states. After leaving the machine alone for an hour in the hope that something was still going on invisibly, I turned it off.

On restart I found I had an unbootable system (kernel panic). I have split the disk in two, installed 9.10 on the new partition, and copied my home directory across. I now have to re-install all my software.

In spite of using Gpartd to mark the old half-way-between-8.04-and-8.10 partition as unbootable, on startup I am offered a choice between 9.10 and three different 8.10s to boot from, each with their own recovery mode option plus other odds and ends. Hey ho.

---

### Post by desconocido on 2010-08-14
After six weeks, I got 9.10 working properly. I never got to use that mobile broadband device. I suppose I can say this is solved now?

---

