---
title: "kworld Dual Tuner card - only one tuner working"
date: 2010-03-30
forum: Mythbuntu
---

### Post by rbeer on 2010-03-30
My kworld pc160 DVB-T tuner detects in the mythtv backend and I have added both adapter 0 and adapter 1. I am using the EIT for scheduling and have connected both adapters to this source. However when I scan for channels (or attempted to use adapter 1 in the frontend) it cannot receive any signal on adapter 1 and shows "no lock". I have deleted both tuners and video source and have added them separately with the same result: Adapter 0 receives all the channels while adapter 1 receives nothing. Do you think this means the second tuner is faulty? 
 
I am using the latest version of mythbuntu.

---

### Post by nickrout on 2010-04-01
does this have two aerial inputs? is it a cabling issue?

---

### Post by rbeer on 2010-04-01
Thank you for your reply but no. It simply has one coax input (it is this model: [http://www.novatech.co.uk/novatech/prods/Components/TVTunerCards/KWorld/PC1602T.html](http://www.novatech.co.uk/novatech/prods/Components/TVTunerCards/KWorld/PC1602T.html)).

I'm returning the card tomorrow and asking for a replacement. If it resolves the problem I'll repost here in case anyone else ever has the same problem.

---

### Post by rbeer on 2010-04-02
In case anyone else ever has this problem you have a faulty tuner. The good people at Novatech swapped it over without any of the awkward questions about how I could know it was faulty if the windows driver CD was still factory sealed.

---

### Post by geekyhawkes on 2010-04-03
i had the same problem a while ago with my kworld usb dual tuner (based on af9015).  I rebuilt the v4l libs using hg (guides available on the v4l website) and did a full power down of my system (power lead out etc).  

Deleted all the dvb-t cards in myth, another restart then started the myth tuning process from scratch and finally got both tuners back. 

I tried just the v4l build, just a restart and just a delete reinstall under myth but individually they didnt do anything for me.  Best of luck!

---

### Post by continuous on 2010-06-07
Hi Rbeer, how does the Kworld PC1602T perform with mythbuntu?
Here in OZ, they are really cheap (Compared to say the Nova 500T dual DTV PCI cards...), so I think many of us would like to know whether they support say two HDTV at the same time and if you have found any problems with it (apart from the issue you had with the faulty unit).

---

### Post by rbeer on 2010-06-18
I'm not in an area that supports HD so can't comment on that but after a bit of setting up it works well enough for my purposes (i.e. recording 2 SD channels simultaneously). Getting EPG updates over the air seems to work but eventually one or both of the tuners would get "no lock" and be stuck with the problem. Switching to XML source and I've not had a problem since with approximately 2 months uptime.

---

### Post by missingtale on 2011-10-05
I am running 2 individual kworld USB tuners on ubuntu 10.4, and have experienced all the same issues. 
I unchecked the use this tuner for EIT on both tuners with the intention of switching to XMLTV however at this point got distracted by child number 1. Myth has been running fine for about 3 days now, and picking up off air schedules fine, I am not sure if this is meant to be working but it is.

I also found that a soft re-start I would loose one tuner, which means when updates need a re-start I have to shutdown and go in the loft and turn it back on which is pain but I can live with it.

---

