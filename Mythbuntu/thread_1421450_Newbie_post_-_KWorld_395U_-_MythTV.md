---
title: "Newbie post - KWorld 395U - MythTV"
date: 2010-03-04
forum: Mythbuntu
---

### Post by wheatpark on 2010-03-04
I have just bought 2 off Acer Revo units, one for a back end server with 2 x KWorld 395U DVB-T tuners (USB) and the other as a front end. They are connected via a Gigabit Switch.

Now, after fresh boot, all works well and the front end can watch live TV streamed from the back end. However, after a day or so of the back end being up and running, when I try to watch live TV, it says 'No Lock' (but does say signal strength is 90% or so).

I suspect I am doing something stupid but have tried possible solutions (including connecting tuners to server via a powered hub in case the power from the server was not enough to power the tuners via USB - made no difference though) :(

Any thoughts from anyone?

I love the MythTV implementation and am beginning to love Linux more as I use it more but still very much a novice.

Thanks

---

### Post by rileyp on 2010-04-12
how did you go with this tuner? I am thinking about getting one.
Are you in Australia? You might find the 4.65 firmware to work better as I have 2 leadtek gold usb tuners I use with mythtv and they have the same chipset but will not lock using the 4.95 firmware. The 4.65 firm locks almost instantly
cheers rileyp

---

### Post by My Name on 2010-04-12
I'm using a revo 3300 as a FE/BE and don't have that problem, so I would suspect it is the tuners you need to look at.

---

### Post by wheatpark on 2010-07-23
No, not in Australia (in UK). Seems to be a problem with the KWorld 395U tuner as I have since bought 1 off Hauppauge USB tuner and this does not have the same problem at all. The problem is reduced if I do not allow active EIT scanning on the KWorld tuners.

Bit of a pain though.

---

### Post by ian dobson on 2010-07-24
> **wheatpark said:**
> No, not in Australia (in UK). Seems to be a problem with the KWorld 395U tuner as I have since bought 1 off Hauppauge USB tuner and this does not have the same problem at all. The problem is reduced if I do not allow active EIT scanning on the KWorld tuners.

Bit of a pain though.

Maybe try increasing the EIT timeout. With EIT enabled mythtv tunes to each multiplex in turn looking for EPG data, and maybe your tuner just doesn't like retuning so often.

Regards
Ian Dobson

---

