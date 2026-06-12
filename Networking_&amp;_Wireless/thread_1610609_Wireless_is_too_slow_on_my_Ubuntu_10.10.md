---
title: "Wireless is too slow on my Ubuntu 10.10"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by eluis.c on 2010-10-31
I almost can't open pages and the download is around 300B/s most of the time!!!

Any help here?

---

### Post by eluis.c on 2010-10-31
And im disconnecting from the internet very often.

---

### Post by vsh3r on 2010-10-31
What type of wireless card and drivers are you using?  Have you tried updating your system with the drivers from the manufacture?

V$H.

---

### Post by eluis.c on 2010-11-01
Right now its a lot better, thank you for ur time!!!

---

### Post by Winston888 on 2010-12-12
I think this ****ing thread should be removed as it serves no purpose other than coming up top of the google search for nothing.

---

### Post by togume on 2010-12-12
Please do not mark this thread as "Solved", since nothing was solved herein...

---

### Post by pmibal on 2010-12-16
I was having the same issue with my Thinkpad T61 and finally fixed the problem.  

My card: Intel Pro/Wireless 4965agn  (iwlagn driver) which was installed by default with ubuntu 10.10 (it's correct).  

However, it's also the same driver for the intel 5300.  That being said, it looks like there was a config file left behind that disables the wireless N access for the 5300.  I believe this file messes with anyones cards... 

Solution:

Remove the following file:  /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf 

This fixed the issue for me.  I am now back to 10mb/s DL compared to 0.6mb/s with the file.

Oh, and yes my router has wpa & wpa2 security on.

Hope this helps

---

### Post by teddfox on 2010-12-25
> **pmibal said:**
> I was having the same issue with my Thinkpad T61 and finally fixed the problem.  

My card: Intel Pro/Wireless 4965agn  (iwlagn driver) which was installed by default with ubuntu 10.10 (it's correct).  

However, it's also the same driver for the intel 5300.  That being said, it looks like there was a config file left behind that disables the wireless N access for the 5300.  I believe this file messes with anyones cards... 

Solution:

Remove the following file:  /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf 

This fixed the issue for me.  I am now back to 10mb/s DL compared to 0.6mb/s with the file.

Oh, and yes my router has wpa & wpa2 security on.

Hope this helps

Worked for me on an HP 5103  THANKS!!!

---

### Post by Yuk-Monkey on 2011-01-01
> **pmibal said:**
> I was having the same issue with my Thinkpad T61 and finally fixed the problem.  

My card: Intel Pro/Wireless 4965agn  (iwlagn driver) which was installed by default with ubuntu 10.10 (it's correct).  

However, it's also the same driver for the intel 5300.  That being said, it looks like there was a config file left behind that disables the wireless N access for the 5300.  I believe this file messes with anyones cards... 

Solution:

Remove the following file:  /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf 

This fixed the issue for me.  I am now back to 10mb/s DL compared to 0.6mb/s with the file.

Oh, and yes my router has wpa & wpa2 security on.

Hope this helps

I have an Intel 4965AGN and this fixed the issue for me in.  I'm running Ubuntu 10.10 on a Inspiron 1501.

open a terminal and type:

"gksudo nautilus"

and scroll to directory mentioned above and delete the file.

---

### Post by blujay on 2011-01-04
Better to edit the file and change "=1" to "=0" so that a future upgrade won't just put the file back and disable N again.

```
sed -i 's/11n_disable=1/11n_disable=0/' /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
```

Or at least add ".bak" to the filename so it will still be there if you need to disable it again.  Deleting configuration files is rarely a good idea.

---

### Post by teddfox on 2011-02-23
Still, my wireless takes over 60 seconds to associate and then I have to restart it on occasion.

---

### Post by bd83862 on 2011-02-23
Thanks a lot. It solved my problem too. But what does this conf file means? What it did to slow and sometimes disconnect my net?

---

### Post by AlanR8 on 2011-02-24
Was an interesting thread!

I have a Compaq Mini with the Intel chipset and a Sony Vaio that does not. If I load 10.10 on either machine, wireless/network becomes almost unusable. Downgrade to 10.04 and all is well.

Hmmmm

---

