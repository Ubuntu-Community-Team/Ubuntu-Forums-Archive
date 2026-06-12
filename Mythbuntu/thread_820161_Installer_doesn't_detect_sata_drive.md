---
title: "Installer doesn't detect sata drive"
date: 2008-06-06
forum: Mythbuntu
---

### Post by bdragos on 2008-06-06
I've just downloaded a fresh copy of the Mythbuntu 8.04 and I ran into problems installing it. It seems that the installer doesn't detect my sata drive. 

First it displays two times this error:

[Some big number] Buffer I/O error on drive fd0, logical block 0.

Then it continues with the installation and when I get to the partition step there is no hdd available. 

Hardware:
motherboard: Gigabyte GF8200 GA-M78SM-S2H
hdd: Seagate Barracuda 7200.11 3.5IN 500GB SATA2 8.5MS 7200RPM 32MB 

Any ideas on how can I get it working? Are there any known issues with this hardware?

Thanks,
Dragos

---

### Post by jbman on 2008-06-06
Change your bios to AHCI for the sata controller.

Then on the install screen press F6 and add the following.

pci=nomsi

The bug can be referred to in detail 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

---

### Post by bdragos on 2008-06-06
Thanks jbman, it did the trick. 
Dragos

---

### Post by fewjr on 2008-09-20
I was pointed to this thread, and it cured my woes. Thank you very much jbman.

                                          Regards,
                                           fewjr

---

### Post by Francewhoa on 2010-03-11
Same here. The following worked for me. Thanks to jbman :) 
[B]
STEPS[/B]

[LIST=1]
[*]**Go into your BIOS. Find the setting for the SATA controller. Change it from IDE to**** AHCI.**
[*]**Boot with Ubuntu intallation CD.**
[*]**Don't change anything into the Ubuntu install screen. Leave it to default normal.**
[/LIST]

Read more about this issue at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

---

