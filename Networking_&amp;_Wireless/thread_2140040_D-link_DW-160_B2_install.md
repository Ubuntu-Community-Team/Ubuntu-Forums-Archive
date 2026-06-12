---
title: "D-link DW-160 B2 install"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by mjmclenn on 2013-04-28
Afternoon!

I was wondering if I could possibly get some advice on trying to install a D-Link DW-160 B2 wifi adapter.  I was trying to follow the instructions from [http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2) but at step 4.1 the author loses me.   I'm really not sure what it is that I'm supposed to do and I was wondering if anyone proficient with Ubuntu might be able to help me make sence of these instructions.  I'm not overwhelmingly technically savvy and I don't have a lot of experience using Ubuntu so any help you can offer would be greatly appreciated.

Cheers,
Maggie

---

### Post by praseodym on 2013-04-28
Hi,

the author means you need to edit the respective files by hand before compiling. Alternatively, here is another installation instruction. I strongly recommend the "dkms" installation "Installation über DKMS"

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=2001%3A3c1a#post-4365112](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=2001%3A3c1a#post-4365112)

---

### Post by mjmclenn on 2013-04-28
Thank you very much for the quick response!  I'll give it a try and keep you posted

---

### Post by mjmclenn on 2013-04-28
I completed the first installation method ([http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2)) and while the device seems to be basically working - a list of available newtorks shows up - the led light is off and I am not able to connect as my password is rejected.  I am able to connect using this password on other devices, also I have successfully installed and used this D-link device on other computers (actually, the same computer, different os...) so I'm at a loss as to what the problem is.  I guess the computers win this time :P

---

### Post by praseodym on 2013-04-28
Now check:
```

iwconfig
lsmod
lsusb
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
route -n
```

---

