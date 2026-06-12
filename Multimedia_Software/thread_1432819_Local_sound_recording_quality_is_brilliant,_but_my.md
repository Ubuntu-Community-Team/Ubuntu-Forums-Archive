---
title: "Local sound recording quality is brilliant, but my voice in Skype is awful. WTF?"
date: 2010-03-18
forum: Multimedia Software
---

### Post by DanielVartanov on 2010-03-18
Hi everyone,

When I record sound in Audacity, sound is clear and nice.
But in Skype my peer hears only low frequencies of my voice and as if it was slowed down significantly.

Settings in both applications are same:
```
Playback: HDA ATI SB, ALC888 Analog (hw:0,0)
Capture: HDA ATI SB, ALC888 Analog (hw:0,2)
```

How to fix this?

---

### Post by blakep2 on 2010-03-18
make sure your input jack is in all the way

---

### Post by DanielVartanov on 2010-03-18
> **blakep2 said:**
> make sure your input jack is in all the way
It is, thanks. And, I repeat, in local sound recorder speech quality is excellent

---

### Post by thundre on 2010-03-18
Could it be a bandwidth issue?  To keep up with real-time, Skype must compress your voice into the available bandwidth.  This would only be an issue if your connection is dial-up, I think.

There could potentially be a bottleneck on either end.  To eliminate his end, use the Skype test service which records a message from you and then plays it back.  

A second potential problem area is full-duplex sound.  In Audacity you're probably recording without something playing at the same time, but Skype does both when you're in a call.  

(Side question -- does anybody know if Audacity can do full-duplex operation, like play back one track while recording another?  That would be a good test for Daniel to run.)

---

### Post by DanielVartanov on 2010-03-18
**thundre**, thank you for a great reply! I'll try to answer:

> **thundre said:**
> Could it be a bandwidth issue?  To keep up with real-time, Skype must compress your voice into the available bandwidth.  This would only be an issue if your connection is dial-up, I think.
My bandwidth is 512kbps, it should be enough, shouldn't it?

> **thundre said:**
> There could potentially be a bottleneck on either end.  To eliminate his end, use the Skype test service which records a message from you and then plays it back.
Yes, I tested with both this service and a 'live' peer. There were described effects in both cases.

> (Side question -- does anybody know if Audacity can do full-duplex operation, like play back one track while recording another?  That would be a good test for Daniel to run.)
Actually Audacity has this feature out-of-the-box. If you press a 'Record' after recording a sample, you will start another recording while first sample is playing. And, it works brilliantly.

---

### Post by DanielVartanov on 2010-03-18
Just in case, here is the list of possible playback and capture devices (highlighted are chosen ones).

Capture: [IMG]http://img519.imageshack.us/img519/3824/micdevices.png[/IMG]

Playback:
[IMG]http://img717.imageshack.us/img717/4654/speakersdevices.png[/IMG]

---

### Post by DanielVartanov on 2010-03-18
It is the Skype issue. Here is the link to a ticket in their issue tracker: [https://developer.skype.com/jira/browse/SCL-601](https://developer.skype.com/jira/browse/SCL-601)

---

