---
title: "3 tuners showing when only 2 installed"
date: 2009-02-10
forum: Mythbuntu
---

### Post by chrisblue on 2009-02-10
Have an issue with a new install of Mythbuntu on 8.10. I have two DVB tuners and somehow myth thinks I have 3 and has called them 3, 4 and 5.

It maybe an issue when recording is scheduled on all three cards at the same time.

I have checked in the set up and only two tuners are configured (I think).

Can someone assist to try to eliminate the ghost one?

Thanks

---

### Post by Archmage on 2009-02-10
Kindly keep in mind that you can set up to five turners for each turner you have installed (this is set up in the turner configration). This had the benifit that you can record more than on program at once with only one turner.

---

### Post by newlinux on 2009-02-10
You probably have multi-record setup on one of the tuners. 
[http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex)

Also, your tuner numbering will only restart when you delete all tuners. So if they start at three, that means you have deleted and recreated some tuners without deleting them all at once. This is not a problem for myth - it knows 1 and 2 don't exist. But if you want it to start at 1 you have to delete all tuners and then recreate them,

---

### Post by chrisblue on 2009-02-11
Thanks for the help guys. I will delete both my tuners and start again.

---

