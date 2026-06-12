---
title: "NovaT-500 Simultaneous record / viewing"
date: 2010-01-16
forum: Mythbuntu
---

### Post by 404wanderer on 2010-01-16
Hello all,

just on my third year of trying to get my PVR setup working :(

I have a Hauppage NovaT-500. Even though I have configured two tuners I cannot watch one channel while recording another. Can anybody enlighten me as to where I am going wrong.

Happy to post config files if somebosy can point me to where the relevant ones are.


wanderer

---

### Post by dibuntux on 2010-01-18
Hi, I just changed my Hauppauge HVR-1100 hybrid analog-digital, with a new Nova T-500 - no more analog here...

It worked a breeze on my existing config! This is what I did:

1) Physically removed the HVR-1100 and swapped in the Nova T-500
2) Exit frontend. In Mythbackend Setup I removed the old V4l and DVB-T adapters for the HVR-1100
3) Added a new DVB-T card, DiBcom 7000PC as DVB device: /dev/dvb/adapter1/frontend0 - Note that is 1 because adapter0 is a Skystar 2 DVB-S card.
4) In Recording Options set Max Recordings to 3; this is very important if you want to be able to record more (3 in this case) channels on the SAME multiplex at the same time.
5) In Input Connections (guess is that in English) I just coupled the newly created /dev/dvb/adapter1/frontend0 -> XMLTVita, the Video Source previously used for the old DVB-T adapter (with ALL channels already set).
6) Exit the setup, without even running Mythfilldatabase
7) ALL channels working, with better signal %!

OK, this is for ONE tuner; you've got two on the Nova-T 500...
Just repeat the procedure from point 2 to install ANOTHER adapter: in my case another DiBcom 7000PC as DVB device: /dev/dvb/adapter2/frontend0 - Note adapter2
So I have:
ST STV0299 DVB-S: /dev/dvb/adapter0/frontend0
DiBcom 7000PC DVB-T: /dev/dvb/adapter1/frontend0
DiBcom 7000PC DVB-T: /dev/dvb/adapter2/frontend0

each with 3 Max Recordings, for a total of 9 virtual tuners Myth can record from!

Hope it clarify the matter.

PS: my config

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by 404wanderer on 2010-01-20
Thanks for the reply. I set mine up with two tuners per card (I'll change it to three as you suggest).

This gives me four tuners listed, but still only lets me watch one channel or record one channel at once.

I'll try the change to three to see if that makes any difference.

Cheers,

wanderer

---

### Post by SiHa on 2010-01-20
Just a thought. I tried Multirec, but it caused exactly the problem you seem to have, I couldn't switch to a different tuner.
A bit of Googling found others with similar problems on the Mythtv mailing list, IIRC. I just settled for one 'tuner per tuner', and all is OK.

---

### Post by ReddogOne on 2010-01-20
You have set up two tuners rather then one tuner and configured it to record two streams (if possible)

I always found [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) to be helpful (and simple to follow).

---

### Post by 404wanderer on 2010-01-25
Thanks all,

changing to 3 tuners per card fixed the problem.

---

### Post by dibuntux on 2010-02-09
I am not able to watch LiveTV & record on 2 channels on different multiplex! The latest  upgrade of 0.22 broke something...

Still able to record on 2 different multiplex & to watch 1 Live TV show & record 2 more on same multiplex.
But if I'm recording on a multiplex, LiveTV seems blocked on channels of that multiplex only.

Any ideas? TIA

---

### Post by dibuntux on 2010-02-11
OK, solved: it seems that when you are recording from one of the DVB-T input and go LiveTV, MythTV sets you ON THAT input.

So you can only watch available channels on the multiplex that input is tuned on.

Then, from the menu, JUST CHANGE INPUT to the second DVB-T, and watch whatever you want. 

I love MythTV...

---

