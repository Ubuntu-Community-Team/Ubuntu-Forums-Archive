---
title: "DVB Adapter LiveTV OK, Zero Byte Recordings"
date: 2012-07-05
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-07-05
Well,

Woke up with a new issue today, and one that I hope is a fairly easy one for someone to suggest a fix for.  I have 3 digital tuners (2 ATi HDTV's and 1 pcHDTV 5500) in a master backend with 3 analog tuners in a slave backend.  LiveTV works just great on both the digital and analog tuners, but recordings are only working with the analog tuners.  With the digital tuners, there is an entry on the recordings menu where the recordings are listed, but they have zero byte file sizes listed.  

I looked in the backend log, and the only help it gives me is a single error at the time the recording is to begin that says something about EOF (assuming End Of File) detected.  But no other errors or help.  I will post the logs if someone thinks it is needed, but I would rather no clog up a post with that unless there is no clear cause or solution that anyone has to offer.

Hoping this one of those... "OK, well, you got this setting wrong", and I can just move right along.  Thanks to anyone with a suggestion.  Again, I am hopeful that someone has seen this and it is just another learning experience for me :-).

---

### Post by Lester_Burnham on 2012-07-06
Hi,

You could try extending tuner time outs in mythtv-setup > capture cards > for each card.
Have you messed with deleting tuners or adding virtual tuners at all?

My Dvico Dual Digital 2 v2 tuners used to go missing now and then, which caused 0b recordings.
Not familiar with your tuners.

Lester

---

### Post by jlp_engineer on 2012-07-06
Thanks Lester,

I will extend the timeouts on the tuners.   I have also heard that changing to Quick Tuning in the connections part of the backend setup can also affect this behavior.

Do you know if the tuning timeout AND the signal timeouts need to be extended or is it just one or the other?

---

### Post by jlp_engineer on 2012-07-06
Well,

I performed an experiment and had one of my ATi HDTV tuners record a few shows in the afternoon while I was at work.  To my surprise, they came out fine.  It seems that only the recordings late at night are resulting in zero byte recordings.  Makes me suspect that the signal is not present at the time the tuner is told to record the program.  

Does anyone know what the "normal" result of a recording that takes place when the digital signal is not present???  Is a zero byte file the normal result, or would something else happen instead?  For example, on my analog tuners, it would record 30 minutes of static...  :-)

---

### Post by klc5555 on 2012-07-07
> **jlp_engineer said:**
> Well,

I performed an experiment and had one of my ATi HDTV tuners record a few shows in the afternoon while I was at work.  To my surprise, they came out fine.  It seems that only the recordings late at night are resulting in zero byte recordings.  Makes me suspect that the signal is not present at the time the tuner is told to record the program.  

Does anyone know what the "normal" result of a recording that takes place when the digital signal is not present???  Is a zero byte file the normal result, or would something else happen instead?  For example, on my analog tuners, it would record 30 minutes of static...  :-)

Looks like you hit the answer. The digital tuner doesn't record background signal noise --if there's no actual mpeg file for it to record, usually the tuner just crashes out. It has happened to me sometimes when the local cable provider has moved a digital channel and I haven't rescanned Mythtv. Sometimes in the middle of a recording too, when the cable provider drops the signal.

I guess this would explain your "EOF detected" log entries.

---

### Post by jlp_engineer on 2012-07-08
Thank you for the confirmation.  Seems to make the most sense, but I will need to stay up one night and see if the signal is actually absent.  Guess I just need to complete my little experiment.  :biggrin:

---

