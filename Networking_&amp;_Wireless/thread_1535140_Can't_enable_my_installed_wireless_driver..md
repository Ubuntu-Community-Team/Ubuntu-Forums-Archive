---
title: "Can't enable my installed wireless driver."
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by edgar_eacg on 2010-07-20
Hello. I've read  a lot about wireless network cards but I haven't found something similiar to my problem. I've a belkin wireless card F5D7000tt and its driver bcmwl5.inf. I think I've correctly installed it because when I use "ndiswrapper -l" i get:
     WARNING: all config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future realease.
     bcmlw5.inf: driver installed
                           device (14E4:4320) present (alternate driver : ssb)

But when I go to Hardware Drivers I see that "Broadcom B43 wireless driver" is not enabled, and when a try to enable it I get an error message:
"We are sorry, but the installation of this driver failed. Check the register archive to see more details: /var/log/jockey.log"

Please, someone to help me.

---

### Post by mikewhatever on 2010-07-20
Let's put things in order here. Ndiswrapper is the utility to run Windows wireless drivers on Linux. B43 is a native Linux driver that works natively on Linux. You can not use the two, Ndiswrapper and a native Linux driver, together.
So, in case you want to use Ndiswrapper with the Windows driver, forget about b43 and Hardware Drivers menu. In case you want to use b43, remove Ndiswrapper first, reboot, and then enable the driver via Hardware Drivers menu.

---

### Post by edgar_eacg on 2010-07-20
then how can I enable with ndiswrapper my wireless network card? I've already done all steps and I'm not able to get conectivity

---

### Post by mikewhatever on 2010-07-20
I don't know. What howto did you follow?

---

### Post by edgar_eacg on 2010-07-20
1. I installed ndiswrapper and ndisgtk from my Ubuntu CD (10.04).
2. Administration > windows wireless drivers
3. I select my windows driver...

and after that nothing. 

Looking for help in ubuntu forums I read that to see if the controller is correctly installed I needed to use this command "ndiswrapper -l"
And as I wrote the only I get is:
************************
WARNING: all config files need .conf: /etc/modprobe.d/ndiswrapper, it  will be ignored in a future realease.
     bcmlw5.inf: driver installed
                           device (14E4:4320) present (alternate driver :  ssb)
***********************
But I can't still have a connection to internet

---

### Post by mikewhatever on 2010-07-21
I've no experience with Ndisrapper. Hope someone else, more knowledgeable, will help you shortly.

---

### Post by smarty420 on 2010-10-25
I have similar Issue . i am using same wireless card .. did  you resolve the issue  and how?

---

