---
title: "Renaming/Disabling Channels of Soundcard..."
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by POSTGOOP on 2006-09-17
Hi all,

I'm using Kubuntu Dapper 6.06 and I've been searching everywhere for this info... #-o 

I'm trying to rename/disable a slew of the channels of my M-audio Delta 1010 soundcard, because no matter what mixer I use, I simply can't navigate through 20 ADC's, 20 DAC's, 20 Multi..., 20 Analog Input's, etc. with out indication as to which it points to. Also, many of these are dead/duplicate/non-existent and I would like to get them out of my way. Since I'm probably stuck using windows for my more in-depth audio work, it's not a big problem, but it's a problem none-the-less.

Any help would be appreciated. Also, if anyone can point me in the direction of a mixer that emulates the windows delta 1010 mixer, that would be even better.

Thanks.


-Mike

---

### Post by jocheem67 on 2006-09-18
I've got the same card, and --acually-- am happy that it works.

Got two soundcards here, well a chip and the delta....

It's a fact that alsamixer just throws in a lot of channels for the delta and they're named differently from the names in windows.

To actually change those names, uhmmm , well maybe you can configure some alsamixer conf. file ? I'd be cautious though, probably alsa just dies on you doing that kind of actions...if even possible.

---

### Post by POSTGOOP on 2006-09-18
To update the situation, I discovered that you could change the names in the Gnome ALSA mixer, but all channels that have the same name by default (DAC, DAC, DAC, DAC, etc) all revert to the most recent name given to one of them... now Out 8/HR, Out 8/HR, Out 8/HR, etc... So I think I need something closer to the soundcard end, if that's possible.

Thanks again.

---

