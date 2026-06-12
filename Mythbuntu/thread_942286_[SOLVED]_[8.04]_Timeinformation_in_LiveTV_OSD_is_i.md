---
title: "[SOLVED] [8.04] Timeinformation in LiveTV OSD is incorrect"
date: 2008-10-09
forum: Mythbuntu
---

### Post by Verzweifler on 2008-10-09
Whenever I start watching LiveTV, the time information received in the OSD when trying to forward or rewind is wrong.

It seems like something adds a "magic" two minutes offset, i.e. immediately after start the OSD will show an information of "0:01 of 2:01". This two extra minutes remain throughout the complete LiveTV session, so at the forwardmost point of the LiveTV recording I get infos like "15:54 of 17:54" and so on. Rewinding by the way works as designed and forwarding as well but only within the mentioned limits, i.e. the "inaccesible" 2 extra minutes at the end that of course do not contain any LiveTV.

What puzzles me the most is that it's _exactly_ 2 minutes, which looks like a "somewhere configured" rather than a "random" value. 

Well, it does not impact usability at all (if you know about it) but it affects the woman-acceptance-factor of LiveTV a lot ("Why can't I skip the commercial? There are two more minutes ahead!")

Any ideas?

---

### Post by Verzweifler on 2008-10-09
I verified with other Frontends connected to my Backend that the effect described above is limited to my **Mythbuntu Diskless Client** only.

On all other non-Mythbuntu Frontends, the time information is as expected, i.e. you'll see "00:14 of 00:16"...

So it looks to me as if there is something wrong with the Diskless; however, I do not know where to look for more infos.

---

### Post by Verzweifler on 2008-10-12
*bump*

No one experiencing that behaviour on a Mythbuntu Diskless Client?

---

### Post by anonymousdog on 2008-10-12
Is system time synched between the diskless and the backend?

---

### Post by Verzweifler on 2008-10-13
Thanks anonymousdog !

The Frontend time in fact was off by 2 minutes and after performing a ```
ntpdate server
```, which I also added to my /etc/rc.local to counter future time drifts, the offset in the OSD was gone!

Shouldn't such time synch not already been included in the Diskless Frontend? Since it runs from the very same physical machine, synching time should be a piece of cake...

---

### Post by mrand on 2008-10-13
> **Verzweifler said:**
> Thanks anonymousdog !

The Frontend time in fact was off by 2 minutes and after performing a ```
ntpdate server
```, which I also added to my /etc/rc.local to counter future time drifts, the offset in the OSD was gone!

Shouldn't such time synch not already been included in the Diskless Frontend? Since it runs from the very same physical machine, synching time should be a piece of cake...Probably so.  If this still occurs with 8.10, please file a bug report!

Regards,

[INDENT]Marc[/INDENT]

---

