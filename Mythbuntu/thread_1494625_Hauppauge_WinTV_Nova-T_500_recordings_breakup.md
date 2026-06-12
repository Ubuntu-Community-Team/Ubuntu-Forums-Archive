---
title: "Hauppauge WinTV Nova-T 500 recordings breakup"
date: 2010-05-27
forum: Mythbuntu
---

### Post by byronmyth on 2010-05-27
Hi Folks. 

Since upgrading to 10.04 from 9.10, I'm finding that recordings from Five, Fiver, ITV2 are becoming mostly unwatchable. I get screen breakup and screeching noises. 

I've checked the LNA setting which is set on (=1). I used to get this before if several channels were recording together or the commflag job (now disabled)was running, but now it's happening even if one channel is recording. BBC seems to record fine, the problem channels show 80% signal strength as per usual.

The strange thing is that watching the channels live, there doesn't appear to be any issue. Plus I can record/view HD content without issue. 

I've ordered another NOVA-T to try in case the card is developing a fault. Any ideas, something I can check for?

Regards - BM

---

### Post by leafpaul on 2010-05-27
This happens to me both in live tv and on recordings with this tuner, but varies widely.  I have put it down to reception issues but my location is right on the edge of a few transmitter reception areas.  Currently the power is low on these transmitters (until full digital switchover), particularly, for the ITV channels and things like Quest.

Sometimes reception is improved by rescanning the channels and sometimes rescanning causes reception to become worse.  Weather conditions also seem to affect the reception.

---

### Post by byronmyth on 2010-05-28
I have pretty good reception, big antenna specifically tuned for Crystal Palace. I read others having issues with warm re-boots, so powered the system off last night and the issue seems to have gone away. Now just need to find the last two episodes of Flashforward before my other half realises the ones recorded are ruined!

---

### Post by PhilWig on 2010-06-01
OP:  Sorry if this is a naive posting, but you did power cycle your myth box after turning the LNA on?  ie unplug from the wall, leave several seconds then re-power.
That LNA setting seems to be held onboard and is not refreshed by a normal reboot.
Phil

---

### Post by byronmyth on 2010-06-08
After a power down of the system the issue went away thankfully.

---

### Post by zzztownsend on 2010-06-08
Hi guys I've got the same problem - please could you just confirm how you are setting LNA=1

In my previous install I had
options dvb_usb_dib0700 force_lna_activation=1
 in file /etc/modprobe.d/options.conf

which worked fine but now with 10.04 if I create this file, I can't detect the NOVA T 500 card in mythtv-setup. Please can you let me know what you are doing?
Thanks 
Matt

---

### Post by byronmyth on 2010-11-19
Do you sort this, annoyingly I've only just noticed you PM'ed me!

---

