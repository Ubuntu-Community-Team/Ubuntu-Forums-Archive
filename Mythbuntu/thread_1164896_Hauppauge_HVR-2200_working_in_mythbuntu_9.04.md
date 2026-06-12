---
title: "Hauppauge HVR-2200 working in mythbuntu 9.04"
date: 2009-05-20
forum: Mythbuntu
---

### Post by Caysho on 2009-05-20
I just got this card today - PCI-E, dual digital and dual analogue tuners :)
Using [these instructions]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200") I got it working in mythbuntu without further hassles (just checked it with live TV).

I gather this driver is very new, as in the last month (May).
What is the typical migration time to the repositories ?

---

### Post by Barky on 2009-05-21
> **Caysho said:**
> I just got this card today - PCI-E, dual digital and dual analogue tuners :)
Using [these instructions]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200") I got it working in mythbuntu without further hassles (just checked it with live TV).

I gather this driver is very new, as in the last month (May).
What is the typical migration time to the repositories ?

does this mean you can use 4 channels? like watch livetv and record three shows at the same time? I'm kind of confused about the tuner business.

---

### Post by epi 1:10,000 on 2009-05-21
woooHoooo   I gota try this.   Let us know how well this card tunes compared to your other cards.

---

### Post by Caysho on 2009-05-22
> **Barky said:**
> does this mean you can use 4 channels? like watch livetv and record three shows at the same time? I'm kind of confused about the tuner business.

That's why I got this card - two digital tuners on one card; I don't know why they bother with the analogue tuners.

[Multirec]("http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex") - If two channels are on the same multiplex (ABC1 and ABC2, for example), then one tuner can be used to handle both channels at the same time.  One physical tuner supports two logical tuners.

To handle the throughput, this machine has a 1 TB SATA drive.  For a few days I had my older AVerMedia tuners in it, and it was happy until the graphics started to die.

For the moment, it will likely remain an experimental box - re my original question, what is the typical migration time for tuner drivers to become part of the default install ?

---

### Post by squidboy on 2009-05-22
The driver only supports the digital tuners, there is no analog support.

As for the tuners you can only use 2 at a time not 4, each tuner can only be in one mode.  You would need 2 cards to record 4 channels at once.

---

### Post by rongweiss on 2009-05-22
According to Hauppauge, you can watch and record two shows at once. Either two digital, or two analog, or one of each. There are two tuners, and both are hybrid. Each will receive either a digital or analog signal. I think the Linux driver, at this time, will only support digital. I'm not sure if that includes both clear QAM (cable) and OTA digita, or just one. Analog is in the works.

---

### Post by Caysho on 2009-05-23
> **squidboy said:**
> The driver only supports the digital tuners, there is no analog support.

As for the tuners you can only use 2 at a time not 4, each tuner can only be in one mode.  You would need 2 cards to record 4 channels at once.

True, if they're on different multiplexes.
ABC1 and ABC2 share a multiplex, so one physical digital tuner will suffice if I want to record tv on both of these channels.  I would hope mythtv schedules the tuners correctly when multirec is enabled.

Note that analogue does not have any interest to me, so the driver is fine.

---

### Post by epi 1:10,000 on 2009-05-24
I just ordered 1 from newegg today. I hope it tunes on par w/ my HVR-1250's for OTA

---

