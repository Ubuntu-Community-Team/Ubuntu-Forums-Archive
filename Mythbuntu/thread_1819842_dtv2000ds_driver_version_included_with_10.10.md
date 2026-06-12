---
title: "dtv2000ds driver version included with 10.10 ?"
date: 2011-08-06
forum: Mythbuntu
---

### Post by declanmullen on 2011-08-06
How would I find out what version of the drivers are included for a Leadtek Winfast dvt2000ds with mythbuntu 10.10 x86 32bit (its got the latest system updates installed) ?

I want to find this out because I want to know if I'm already using the most stable drivers. Currently for some recordings Mythtv fails to record anything and tells me the file is missing when I try to view the recording. I'm hoping that there is a more recent driver version that will solve that problem.

```
$ uname -a
Linux pvr 2.6.35-30-generic-pae #56-Ubuntu SMP Mon Jul 11 21:51:12 UTC 2011 i686 GNU/Linux
```

I'm using the drivers that come with that OS.
I using version 4.95 of the dtv2000ds firmware that comes with that OS.

I believe the driver's kernel modules are called tda18271 and af9013.

BTW, I tried mythbuntu 11.04 but it's nvidia proprietary drivers are very flakey (with my gt430 atleast) and I couldn't get the dtv2000ds's remote control to work.
 
Thanks,
Declan

---

### Post by rileyp on 2011-08-09
If you want to use this tuner save yourself the pain and use Natty. Forget about the remote.You can get a mceusb for $20
 [http://www.ebay.com.au/itm/Microsoft-MCE-Remote-Control-USB-IR-Receiver-Win7-Vista-/220734659912?pt=AU_Electronics_Accessories_Remote_Controls&hash=item3364cf9d48](http://www.ebay.com.au/itm/Microsoft-MCE-Remote-Control-USB-IR-Receiver-Win7-Vista-/220734659912?pt=AU_Electronics_Accessories_Remote_Controls&hash=item3364cf9d48)

---

