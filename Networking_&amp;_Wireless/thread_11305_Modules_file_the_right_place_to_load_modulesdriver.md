---
title: "Modules file the right place to load modules/drivers during boot?"
date: 2005-01-15
forum: Networking &amp; Wireless
---

### Post by Ubuntu_User on 2005-01-15
Hello all,

I have an SMC-Ultra network card that Ubuntu didn't automatically load after startup. Each time after booting I had to use 'modprobe smc-ultra' and 'ifup eth0' to get it going. To load the card automatically during the boot procedure, I modified the /etc/modules and added 'smc-ultra' and '8390'. Was this the 'correct' method to solve my problem? Most instructions I came across suggested adding an 'alias eth0 smc-ultra' to modules.conf, but that didn't help me at all.

I'm looking forward to your views on the subject.

Best regards.

---

### Post by feneks on 2005-01-16
It is correct to load needed modules by writing them into /etc/modules.

hopefully it works.

---

### Post by Ubuntu_User on 2005-01-16
Oh, it worked, I was just wondering if there is a different/better way of doing it. Thanks anyway!

---

### Post by feneks on 2005-01-16
Well, you could write a script which is started by init and contains the modprobe command. But this is dirty and totaly uneccessary.

---

### Post by KIAaze on 2008-06-15
But where do you put the .ko file so it can get loaded?

---

