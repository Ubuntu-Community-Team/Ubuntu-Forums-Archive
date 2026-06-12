---
title: "How do I *really* delete TV programmes?"
date: 2009-08-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-15
I have recorded many TV programmes on my Mythbuntu machine. Almost always, when I watch a programme, I then delete it.

I do this by selecting the programme I've just watched in the same screen I use to select the programme for watching, pressing the right arrow, and then choosing "Delete recording" from the menu that appears.

This removes the programme from my list of programmes to watch, but it doesn't actually delete the programme. This is a problem for 2 reasons:

1. My disk space usage is growing at an alarming rate

2. I have a Zyxel media streamer in another room, which I use to watch TV programmes that are stored on the Mythbuntu box via Mythbuntu's UPnP capability, and it presents me with a huge list of all the programmes I've ever recorded, which is hard to navigate. I can watch "deleted" programmes from the list just as easily as ones that are not deleted.

I can see that not actually deleting things straight away is desirable behaviour, in case I change my mind about something. However, it would be good if after, say, a week, the programme were gone for ever.

Is there something I can do to genuinely get rid of my old recordings?

Many thanks
NM

Mythbuntu 8.10.

---

### Post by murchball on 2009-08-18
It sounds like you're doing it properly. I'm guessing that you have a permissions problem on your recording directory. Maybe the logs will have more info.

---

### Post by Archmage on 2009-08-18
The default is that MythTV will only mark is at deleted. Within the setting you can set how many discspace should be left. MythTV will than delete the oldest/with lowest priority. There is really no need to delete it manual.

However you can change the setting and even delete a recording over the information center.

---

### Post by NautiusMaximus on 2009-08-19
OK, thanks.

I've had a good look round in the settings, and in the frontend Settings/TV/General I found an option for setting the age at which to expire deleted recordings, which was set to zero. According to the on-screen instructions (although this option doesn't seem to be documented in the user manual) a non-zero value means that deleted recordings will be expired once they reach the specified age, and a zero value means they won't be expired.

I assume "expired" means that they are really deleted, as I'm hoping to achieve?

Anyway, I've set it to 7 days, so with a bit of luck all my elderly deleted recordings will soon disappear.

---

