---
title: "modprobe cx88-dvb fails for Dvico capture card"
date: 2009-08-30
forum: Mythbuntu
---

### Post by colinnwn on 2009-08-30
Hi,

I have a Dvico Fusion HDTV 5 Lite card that was marginally working about a year ago. After an update, it quit being recognized on the digital side. When I deleted the card and tried to re=add it as a DVB card, I got

could not get card info for card #0 subty...

The card is recognized on the analog side. I've spent about 4 hours googling on this card and troubleshooting, trying different things, and discovered it is usually a problem with cx88-dvb not being loaded. When I sudo modprobe cx88-dvb I get 

```
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device
```

That file does exist, but I know it is saying the device doesn't exist. It seems like the people who have run into this problem have about a 50% success rate resolving it. I've tried all the suggestions I could find on the net and nothing worked. I've found several launchpad bugs with no resolution.

Does anyone have suggestions on what to do to get this card working? I'm pretty much ready to ebay the card and stick with my analog PVR-150. Though in comparison to digital cable on my TV, its picture sucks and I am not sure how much longer I can take it. Really want an HDHomeRun, but I don't feel that rich right now.

Thanks.

---

### Post by novellahub on 2009-08-31
If you are looking for a cheap replacement card, you can get a ATI HDTV Wonder VE:

[http://www.compuvest.com/Desc.jsp?iid=1028911](http://www.compuvest.com/Desc.jsp?iid=1028911)

If you get the card, make sure you follow these steps:

Get the firmware:

[https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder](https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder)

Then force the tuner type:

[http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient](http://www.mythtv.org/wiki/ATI_HDTV_Wonder#VE_Varient)

---

### Post by colinnwn on 2009-08-31
Thanks for the suggestion, that is an awesome price. I need ClearQAM though. Doesn't look like that card does CQAM. 

I'm shocked the Divco card, which is known to work with Linux, has such a high rate of install failures. It is such an intractable problem and no one has figured out how to reliably solve it.

---

### Post by novellahub on 2009-08-31
> **colinnwn said:**
> Thanks for the suggestion, that is an awesome price. I need ClearQAM though. Doesn't look like that card does CQAM. 

I'm shocked the Divco card, which is known to work with Linux, has such a high rate of install failures. It is such an intractable problem and no one has figured out how to reliably solve it.

I am using them right now picking up Clear QAM. 

[http://ubuntuforums.org/showthread.php?t=1130930](http://ubuntuforums.org/showthread.php?t=1130930)

---

### Post by colinnwn on 2009-09-12
I bought this card excited to try it out. But it is 1/16" too tall to fit in my small Lian-Li computer case. It is noticeably taller than all my other full height PCI cards. I guess I will try selling it on eBay, since I would only get back about $10 of the $25 cost, and that doesn't include the shipping I'd have to pay.

If you are space constrained, I wouldn't suggest this card.

---

