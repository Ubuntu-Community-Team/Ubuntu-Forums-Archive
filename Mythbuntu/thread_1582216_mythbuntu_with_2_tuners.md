---
title: "mythbuntu with 2 tuners"
date: 2010-09-26
forum: Mythbuntu
---

### Post by tomer1976 on 2010-09-26
Hi,

i have an HTPC with 2 usb tuners:
1) TT-3600 S2 stellite card.
2) siano dvb-t usb card.

i already had a configuration that both cards worked together and mythtv could tune to channels from both of them

last week i had to format and reinstall mythbuntu from scratch and now i can watch only channels from one card.
if i tune to local channels (dvb-t) i dont see the satellite channels in the list of channels. and vise versa.

my wife wants to kill me when she exidently tune to a channel in Arabic from the satellite and not able to tune back into her favorite local dvb-t channels.

what can i do to fix it? i am sure there is something to do because it worked in the past.
i think it is related to the settings of each video source. maybe the recording group?

please help me. my marriage is in danger :)

---

### Post by ian dobson on 2010-09-26
Hi,

While watching live TV you need to manually change the tuner, I think if you go to the menu while watching liveTV (i on my remote) you can then chage the tuner used.

Regards
Ian Dobson

---

### Post by barbex on 2010-09-26
Did you assign channel numbers? I have two TV-cards and have my analog channels on 1 to 33 and all the digital channels on 34 to 48. When I go from 33 to 34 Mythtv changes the tuner automatically.

Does that work for you?

---

### Post by tomer1976 on 2010-09-26
> **barbex said:**
> Did you assign channel numbers? I have two TV-cards and have my analog channels on 1 to 33 and all the digital channels on 34 to 48. When I go from 33 to 34 Mythtv changes the tuner automatically.

Does that work for you?

the numbers are different for channels of both cards. no conflict on numbers.

i used to have a system that let me change channels transparently between the cards without the need to change the source in the settings button of the remote.
i put all the chanels in the "favorite" channels group and it worked. now it doesnt.

---

### Post by ian dobson on 2010-09-26
Hi,

OK there appears to be an option BrowseAllTuners in the settings database, so there must be an option somewhere in the Frontend Configuration to set this option.

I don't watch LiveTV due to too many adverts :)

Regards
Ian Dobson

---

