---
title: "Mixed encoders"
date: 2014-01-26
forum: Mythbuntu
---

### Post by water0101 on 2014-01-26
I have 2 standard Hauppauge encoders and 1 HD Hauppauge encoder. Is there a way that I can force the HD encoder to be used for Freeview HD programs and the others for normal Freeview programs?

---

### Post by Gillingham on 2014-01-26
Yes - at least under 0.25 and 12.04.03.

I have 2 cards one Hauppauge one that can do only standard definition (lets call this one SD) and one from TBS that can do HD (let call this one HD).

In the backend set up I have two input connections one for the SD card  and one for the HD card.  One of the options here is called schedule priority this determines which card is preferred the lower number input is preferred so I have SD set to 1 and HD set to 2.  

Then to give the HD programs a chance to record, we need to increase the weighting for HD programs in the recording profile accessible from the frontend.

This combination means that card SD will be used in preference unless the program is also being shown in HD, however, a SD program may still be recorded on HD card if too many SD programs are being recorded at the same time.  If this is not acceptable - may be you should also delete the non-HD channels on the HD card.

David

---

### Post by water0101 on 2014-01-26
Thank you for your reply David, I will give that a try.

David (also!!).

---

### Post by water0101 on 2014-01-27
Further question if I may David.

In the Input Connections in the MythBackend I found Input Priority and Schedule Order and I wasn't sure which one you meant me to set as the help seems to infer you ought to use Schedule Order.

Also in the MythFrontEnd  as I was setting the priorities as you said I found in Set Recording Priorities / Scheduler Options / HDTV Recording Priority which seemed to infer that was the way to ensure that HD programs were scheduled on the correct recorder.

---

