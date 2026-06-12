---
title: "video card driver issues after upgrade"
date: 2013-03-13
forum: Multimedia Software
---

### Post by iocane on 2013-03-13
Hello all, Here is my problem.  I had natty narwhale installed and when I updated to the 12.04 version my screen goes green and get lines across it.  The only way I can boot is to go into failsafe graphics mode.  But the only option it gives me is to boot one time only.  How do I set up my system to use this driver?   I am using an amd a4 processor with a built in radeon card.  Let me know if you have any more info you need from me.  I have a limited understanding of the os so I may need some direction on how to find the info you need from me.  Thank you.

---

### Post by iocane on 2013-03-13
Here is a little more information.  The processor has an AMD Radeon HD 6410D video card built in.  And when I look under system/ details / graphics the driver reads vesa:sumo

---

### Post by ManamiVixen on 2013-03-13
you need to put into terminal "sudo apt-get install fglrx-driver"

---

### Post by QIII on 2013-03-13
*Moved to **Multimedia & Video***


If you upgraded via the update manager (that is, if you did not do a fresh install) then you may have run into this issue if you did not first uninstall all third party drivers.  This is probably the number one reason for difficulties when doing an upgrade rather than a fresh install.

If that is the case, first uninstall the driver

```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot.  This should have you running the default open source Radeon driver.

Then

```
sudo apt-get install fglrx fglrx-amdcccle
```

followed by 

```
sudo amdconfig --initial
```

Reboot.

---

### Post by iocane on 2013-03-13
QIII I have done that and now I get the Ubuntu splash screen then an out of range message on my monitor and the failsafe graphics mode does the same .  lol  what did I do wrong

---

### Post by QIII on 2013-03-13
Does your system* only * have the ATI GPU, or do you by chance have an Intel/ATI hybrid?

---

### Post by iocane on 2013-03-14
ATI only

---

### Post by iocane on 2013-03-14
Ok so now I removed the last driver I installed and I can boot into fail safe graphics mode.  It still does not boot without green lines through the screen.  Can I make the same generic driver for fail safe mode my default?  And if so how do I find which driver that is?

---

