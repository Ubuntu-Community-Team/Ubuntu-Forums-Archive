---
title: "Reducing live buffer in 8.10"
date: 2008-12-30
forum: Mythbuntu
---

### Post by Greymonkey on 2008-12-30
Hi, first post, and apologies if this is covered somewhere else.  I tried searching but can't see a similar question.

When I select a channel from the guide it takes about 3 seconds to get to the channel.  I think this is to do with the buffering configuration, where 3 seconds are being recorded in case you want to record, rewind etc.  I'd like to reduce this to 1 second or so, so that I can get to the channel quicker.

I appreciate its recommended to use the guide to select a program instead of channel hopping, however I still get this 3 second delay when using the guide.  Traversing the guide itself is very snappy and responsive.  This is on new hardware that exceeds recommended spec, so the hardware is not to blame.

Any help is appreciated, thanks in advance :)

---

### Post by Greymonkey on 2008-12-31
Bump - anyone able to help?

---

### Post by newlinux on 2008-12-31
I'm not sure you can change the buffer, but I know there is a quicktune setting in the backend input setup. I haven't every played with it but it is something worth trying...

---

### Post by Greymonkey on 2009-01-02
Thanks Newlinux, I'll play with that and see if there's any change.

---

### Post by ReddogOne on 2009-01-02
No expert by any means but from what I have read this is not really possibly because of the way mythTV works.

Because of the way digital TV works you have to wait up to a second (though usually less) before you can start watching TV anyway but because MythTV insists of recording everything up have to wait for the data to get to the disk and then be pulled off again so 3 seconds is about it!

I'm sure it would be possible and reasonably easy to pipe the video straight to the front-end though as most people (who use PVRs) tend to watch recording 99% of the time the incentive probably isn't there for someone in the know to make the change.

Though personally I think it would be a good thing, get more new users and all that!

---

### Post by uncle hammy on 2009-01-02
Mythubutu uses to use a "ring buffer" for live tv...similar to what you suggest.  I htink it was changed for a couple reasons (I stand to be corrected)...

1.  It limited how long you could pause tv, because the buffer had limited size, and was recycled.

2. It limited how far you could rewind live tv, for the same reason.

3. If you decided to record a program mid stream, you only got what ever was in the ring buffer, rather than you entire viewing segment.

---

