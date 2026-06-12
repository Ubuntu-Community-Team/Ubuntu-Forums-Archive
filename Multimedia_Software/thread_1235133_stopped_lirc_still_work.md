---
title: "stopped lirc still work?"
date: 2009-08-08
forum: Multimedia Software
---

### Post by hphd-Blokkolnam on 2009-08-08
Hi!

I have a MSI Tv@Anywhere PLUS  tv tuner card. I installed lirc via synaptic, and I chose the TV@Anywhere Master option, becuase there is no config file for the PLUS card. Mainly my remote works, but some buttons are not, like channel up/down, Reset, and some others. 

I checked the config files in etc/lirc/, and I tried to modify them manually. The strange thing is that, after modification of the lircd.conf (or the file lircd.conf.tvanywhere what is included in it), and restarting lirc (sudo /etc/init.d/lirc restart), I cannot see any difference.... 
I even tried to stop lirc:  sudo /etc/init.d/lirc stop ,  it said OK, but my remote still working :)
What do I do wrong?
Thanks much for any help,
best wishes!

---

