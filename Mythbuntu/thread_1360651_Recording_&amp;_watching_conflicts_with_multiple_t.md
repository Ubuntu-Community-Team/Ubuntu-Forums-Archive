---
title: "Recording &amp; watching conflicts with multiple tuners"
date: 2009-12-21
forum: Mythbuntu
---

### Post by peely on 2009-12-21
Hi,

Could somebody please help, I'm tearing my hair out here!

I have three tuners, serviced from one dual DVB-T tuner card and one DVB-S tuner card. The two DVT-T tuners are in a Terrestrial source and the SVB-S card is in a Satellite source, all have channel names which match.

They all work perfectly and I can confirm I can watch any channel through any card by using multiple front-ends. I have labelled each tuner card with an ID so I can see which tuner card is being used. I have set unique priorities for each tuner.

If I schedule a programme to record, then the highest priority card is shown as scheduled to record the programme, and indeed will record it successfully.

If I am watching a programme on a different mux to the scheduled programme however, then as soon as the programme is due to be recorded I am booted off of the live TV, when there are perfectly good tuners available to service the recording!

I have tried various options, such as setting each card in a different input group 1, setting them is different input groups 1 and 2, and setting them in the same input group, all to no avail.

Could somebody please tell me how I can get scheduled recordings to use any tuner if the preferred tuner is already servicing?

I'm using 9.10 with Myth 0.22+ fixes.



Thanks in advance,




Neil.

---

### Post by SiHa on 2009-12-21
I think the option you are looking for is "Allow LiveTV to move Scheduled Shows".

It's in TV Settings -> General (I think).

As I understand it, this will allow Myth to move the scheduled recording onto a different tuner, if available.

---

