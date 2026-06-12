---
title: "[SOLVED] Guide channels mixed up after rescan"
date: 2007-12-19
forum: Mythbuntu
---

### Post by pssturges on 2007-12-19
Hi,

I've had my guide data running nicely for about 6 months or so using the 'Shepherd' grabber to get my xmltv data here in Australia. One of the TV stations here made some changes to their dvb lineup, so I rescanned my channels. Now some of the channels are being populated with guide data from different channels.

I have tried reconfiguring my grabber, and I'm sure that's right. The correct xmltvid's are aligned with the correct channels in Myth, and the data in xmltv file is as it should be. It seems Myth is screwing it up somehow.

Any ideas?

Thanks
Phil

---

### Post by newlinux on 2007-12-19
you can try a ```
mythfilldatabase --refresh-all
``` which will refresh all data for your channels. I sometimes do this after rescans and channel changes and it seems to fix things for me. I don't know anything about the shepherd grabber, so I don't even know if this applies to you...

Good luck

---

### Post by pssturges on 2007-12-20
Yep, that did it.:)

Many thanks
Phil

---

