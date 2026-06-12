---
title: "the restricted broadcom sta driver always not in use when boot up"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by qubicllj on 2008-12-22
I installed broadcom sta driver in hardware drivers application,but every time i boot up the computer,the hardware drivers application show "the driver is activated but currently not in use".I have to "deactivate" & "activate" once to make the wireless driver work.Please help me!

---

### Post by qubicllj on 2008-12-22
I found a solution:
```

sudo gedit /etc/modules

```
insert "wl" to new line
then restart the computer,the wireless driver works.But why the hard drivers application doesn't make the operating system load the driver on boot up?

---

### Post by basilio on 2009-05-10
Thanks mate! Your experience helped me to fix the same problem as well. I'm using HP laptop as well with a broadcom STA wireless driver.
It started for me after i upgraded to the recent distro.:o
Cheers!

---

### Post by gregorthebigmac on 2010-02-26
i'm having the same problem on mine (running an intel-based mac with the broadcom wifi card) i tried what you said, but it's still not working. maybe i'm doing it wrong? this is what my /etc/modules file looks like:
________________________________________________________________________
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
_________________________________________________________________________

this is what it's supposed to look like, right?

---

### Post by naifnezar on 2010-04-18
it works for me!!! TQ Brother!!!! you are the man!!!!! solute you!!

---

### Post by GHX on 2010-06-22
Thank you Thank you Thank you :grin:
Just installed Linux Mint Isadora today and I almost gave up,  I'm new to linux and didn't expect this much trouble so early on, not with the wireless drivers anyways

---

### Post by tech7 on 2010-08-25
wow, I have to say thanks as well...  THANKKKKKKKKSSSSSSSSSS TO YOU my stuff finally works.  Despite two days of terror and frustration, it has quickly came to an end.  I was actually considering uninstalling my ubuntu and climbing back into the ms cage...  :KS  your the best, man!!!  my BFF whether you like it or not!!!

---

### Post by conjunctivitis on 2010-08-27
i have the same problem and this solution didn't work for me.  the problem started when i installed the linux-rt kernel for audio editing.  i alternate booting between the 2.6.32-24 generic and the current linux-rt (realtime kernel from ubuntu studio).  i currently have to deactivate and reactivate wireless in both kernels to get it working.  are there any other possible solutions?  thanks.

dan

---

### Post by lukaszeq on 2010-09-12
Yay, I was looking for that for about 3 weeks - and it works! Huge beer from me, thanks mate! \\:D/

---

