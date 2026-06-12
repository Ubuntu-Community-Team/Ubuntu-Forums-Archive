---
title: "Recording an input using no-grabber"
date: 2010-02-28
forum: Mythbuntu
---

### Post by gwagchunks on 2010-02-28
Hi

Just trying to get my head around recording from my satellite sky box using no grabber. I have a channel set up (channel 914) to record from the STB using the happauge PVR-150 card. I manually set the STB to the right channel. If go watch TV then goto the channel 914 I see the required channel. My problem is, if I press record, it seems to only record for about 5 mins, or sometimes 30, sometime 10. Can someone explain how pressing R with out a grabber is supposed to work? Setting up a manual schedule is fine, but sometimes when watching this channel it would be good to just hit record and then stop it when finished. Hope this makes sense.

Thanks

---

### Post by nickrout on 2010-02-28
> **gwagchunks said:**
> Hi

Just trying to get my head around recording from my satellite sky box using no grabber. I have a channel set up (channel 914) to record from the STB using the happauge PVR-150 card. I manually set the STB to the right channel. If go watch TV then goto the channel 914 I see the required channel. My problem is, if I press record, it seems to only record for about 5 mins, or sometimes 30, sometime 10. Can someone explain how pressing R with out a grabber is supposed to work? Setting up a manual schedule is fine, but sometimes when watching this channel it would be good to just hit record and then stop it when finished. Hope this makes sense.

Thanks

I think it might record to the next 30 minute boundary, ie the hour or half hour. Why not set it up rpoperly with a channel changing script, grabber etc?

---

### Post by SiHa on 2010-03-01
> **nickrout said:**
> I think it might record to the next 30 minute boundary, ie the hour or half hour. Why not set it up rpoperly with a channel changing script, grabber etc?
Yep, that's exactly what it does. Probably to stop you hitting 'R', answering the telephone, then forgetting that its' recording and filling the HDD.

---

### Post by gwagchunks on 2010-03-01
Thanks for the replies. That explains the record issue. I did look at channel changing some months ago but gave up as I couldn't get my head around it. I'd like to have another go at this now, but I'm not even sure if the ir blaster that comes with the PVR-150 works, and I'm not sure what grabber I could use? Do you have any links I could follow? Please bear in mind that even though I've been dabbling with myth for up to a year now, I still am very much a newbie!

Thanks again.

---

### Post by SiHa on 2010-03-01
If the blaster's no good, I guess you could still achieve properly timed recordings using a grabber for your EPG data.

The Radio Times grabber seems to have quite a lot of SKY channels listed:
[http://xmltv.radiotimes.com/xmltv/channels.dat](http://xmltv.radiotimes.com/xmltv/channels.dat)

But I gave up trying to use a grabber very quickly (out of laziness) and just settled for EIT data, so I can offer no advice on that front, I'm afraid.

---

### Post by nickrout on 2010-03-01
> **gwagchunks said:**
> Thanks for the replies. That explains the record issue. I did look at channel changing some months ago but gave up as I couldn't get my head around it. I'd like to have another go at this now, but I'm not even sure if the ir blaster that comes with the PVR-150 works, and I'm not sure what grabber I could use? Do you have any links I could follow? Please bear in mind that even though I've been dabbling with myth for up to a year now, I still am very much a newbie!

Thanks again.

Where are you and what TV service are you using?

---

### Post by gwagchunks on 2010-03-02
Hi

I'm in the UK, using the Pvr-150 to capture SKY channels from a SKY satellite box.

---

### Post by nickrout on 2010-03-02
> **gwagchunks said:**
> Hi

I'm in the UK, using the Pvr-150 to capture SKY channels from a SKY satellite box.

OK do radio times have data for sky?

---

### Post by SiHa on 2010-03-03
Check my link above, I counted 44. So that's not all of them I expect, but certainly the popular ones are there. Also all the usual freeview ones (Dave, GOLD, Virgin1 etc..)

---

### Post by gwagchunks on 2010-03-03
I've used the radio times grabber in the past for the DVB cards, and now just use EIT. I don't have a problem creating a grabber to use radiotimes data to use with the PVR-150 card, but how do you then map the channels from the grabber to get the ir-blaster to change channel on the satellite box? Thanks.

---

