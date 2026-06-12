---
title: "Broadcom sta crda problem"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by osmoTR on 2009-04-22
i use ubuntu 9.04 installed broadcom sta driver but wireless-crda didn't changed regulatory domain for europen extra channels 12-13

still 11 channels active

---

### Post by chili555 on 2009-04-22
This may be helpful to you: [http://wireless.kernel.org/en/developers/Regulatory/CRDA](http://wireless.kernel.org/en/developers/Regulatory/CRDA)

I suggest you try, from a terminal:```
sudo apt-get install iw
sudo iw reg set EU
```I haven't tried this, since I live in the US and 11 channels are all I can use. Post back so the searchers can see what worked or not.

---

### Post by osmoTR on 2009-04-23
> **chili555 said:**
> This may be helpful to you: [http://wireless.kernel.org/en/developers/Regulatory/CRDA](http://wireless.kernel.org/en/developers/Regulatory/CRDA)

I suggest you try, from a terminal:```
sudo apt-get install iw
sudo iw reg set EU
```I haven't tried this, since I live in the US and 11 channels are all I can use. Post back so the searchers can see what worked or not.

already i tried but didn't work

iw reg set command depends nl80211 but wl don't use it
manuel i modprobed cfg80211 after iw reg set command works fine i see changed new regulatory in dmesg

but after command "iwlist eth1 channel" 
still only 11 channels

but if i use b43 firmware cfg80211 works fine after 

iw reg set TR 
i can see 13 channels

i want to use wl because better than b43 firmware

---

### Post by krige on 2009-04-29
Any news on this problem?

I also have tried "iw reg set EU" but still see 11 channels only.

The wireless router at work uses channel 13 and I am not able to see it :(

---

### Post by johnlawrenceaspden on 2009-08-27
[LEFT]Hi, I have the same problem with both Ubuntu 9.04 and the original Dell version of Ubuntu on my mini 10v.

Again, the wl driver seems to ignore the crda mechanism, and iw reg set doesn't work either. 

However it's got a Broadcom BC4322 card, which the b43 drivers seem not to support.

Any ideas? Since it doesn't work with the original installation either I imagine Dell might be interested in fixing it, but how to let them know? I can't face hours talking to call-centre people in order to get to an engineer....

Cheers, John


uname -a for dell ubuntu version is:
Linux dell-mini 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
[/LEFT]

---

### Post by johnlawrenceaspden on 2009-08-27
ps I'd be more than happy to hack the driver... Is there source anywhere?

---

