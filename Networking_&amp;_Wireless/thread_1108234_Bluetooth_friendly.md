---
title: "Bluetooth friendly"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by Aqualung on 2009-03-27
Is there such a thing like a Bluetooth-friendly Linux distribution? Last time I checked (I think it was about a year or so ago), no such thing existed.

Concretly, will the latest Ubuntu release (8.10?) see my Broadcom 2045-based Bluetooth dongle(s) out of the box?

---

### Post by Aqualung on 2009-04-04
> **Aqualung said:**
> Concretly, will the latest Ubuntu release (8.10?) see my Broadcom 2045-based Bluetooth dongle(s) out of the box?Okay, I see Jackalope does. How about A2DP? Or is that still a luxury reserved for the Windows crowd?

---

### Post by Gus_T_Reer on 2009-04-07
Hi Aqualung,

I've been using a2dp since 8.04 Hardy. It seems to me (and to a number of other people I think) that getting a2dp to work in 8.10 Intrepid was/is harder than in the previous version, 8.04.
In both cases I'm afraid I've found it NOT to be plug-n-play seeing that you end up having to run bash scripts to route the sound to the bluetooth hardware.
If you're still interested I can post how I achieve it in Intrepid, or you may want to wait to see what Jackalope offers later this month (at the time of writing).

Regards

GTR

---

### Post by Aqualung on 2009-04-07
> **Gus_T_Reer said:**
> I've been using a2dp since 8.04 Hardy. It seems to me (and to a number of other people I think) that getting a2dp to work in 8.10 Intrepid was/is harder than in the previous version, 8.04.
In both cases I'm afraid I've found it NOT to be plug-n-play seeing that you end up having to run bash scripts to route the sound to the bluetooth hardware.
If you're still interested I can post how I achieve it in Intrepid, or you may want to wait to see what Jackalope offers later this month (at the time of writing).

Many thanks for the reply. I am actually using Jackalope, and it does seem that you *still *have to run scripts to route audio to wherever you need it :mad:. At any rate, I'd appreciate if you could post your algorithm nonetheless.

---

### Post by Gus_T_Reer on 2009-04-07
Hi Aqualung,

I'm afraid I have no algorithm of my own but rely on the kind sharing of others with more skill than I, and I'll warrent that if you've got a2dp working in Jackalope then you've probably gone through the same machinations as me.

Anyway here goes: Firstly I followed the instructions over at [Fosswire]("http://fosswire.com/2008/10/25/better-bluetooth-audio/")
Then I rebooted the system to ensure all had installed correctly (I used the ~/.asoundrc as in the instructions).
When I came to issue the pactl command I got a timeout message but I noticed that if my headphones (Motorola S805) had been paired before the current session then the timeout occurred. If the headphones were deleted and re-paired (or just paired if not already paired) in the current session just prior to issuing the pactl command then the pactl command worked fine. All other instructions were as per Fosswire including getting avrcp working.
I would have liked to see the a2dp mess resolved sometime during the Intrepid period but it was not to be and I suppose it's not a high priority. Got to say though that I'm a bit disappointed Jackalope hasn't resolved this issue either.

Regards

GTR

---

