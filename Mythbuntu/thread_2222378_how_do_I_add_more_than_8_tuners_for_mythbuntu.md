---
title: "how do I add more than 8 tuners for mythbuntu"
date: 2014-05-06
forum: Mythbuntu
---

### Post by mikulator on 2014-05-06
Hi Guys,

My household can no longer live with tuners being occupied by ongoing recordings when they watch live tv...

But mythbuntu only supports 8 adapter.

I have previously compile debian kernel (using menuconfig) to support more tuners but I don't know if there is a "correct / standard" when working with mythbuntu?

anyone point me to a guide?

cheers
Mik

---

### Post by tgm4883 on 2014-05-06
> **mikulator said:**
> Hi Guys,

My household can no longer live with tuners being occupied by ongoing recordings when they watch live tv...

But mythbuntu only supports 8 adapter.

I have previously compile debian kernel (using menuconfig) to support more tuners but I don't know if there is a "correct / standard" when working with mythbuntu?

anyone point me to a guide?

cheers
Mik

How does it only support 8? I wasn't aware of such a limitation.

---

### Post by mikulator on 2014-05-06
the limit is in linux and is on the physical tuners

---

### Post by dannyboy79 on 2014-05-06
are you saying that somehow the linux kernel limits how many /dev/videoX's you can have? I can't really help since i only have 3 tuners but I am very curious about this limitation. I've heard about zoneminder which is security system software which has to have the ability to have more than 8 video devices, are you sure you're limited by the kernel?

---

### Post by mikulator on 2014-05-06
no /dev/dvb/adaptersX's

---

### Post by khPWXxF on 2014-05-06
and your environment does not support virtual tuners?
Phil

---

### Post by mikulator on 2014-05-06
yes it does (i have 2 for every physical tuner), but then the family has to switch source when surfing around.

I have tried for several years to teach them to record their shows, but... loong story

---

### Post by khPWXxF on 2014-05-06
I thought I'd seen some thread on tuner limits but can't find it.  Did come across these though.
[URL="http://www.mythtvtalk.com/exactly-how-do-multiple-tuners-work-inside-myth-16441/"]
http://www.mythtvtalk.com/exactly-how-do-multiple-tuners-work-inside-myth-16441/[/URL]  5 virtual per real.
 
[http://www.mythtvtalk.com/requirements-12-tuner-backend-nas-pbx-server-15818/](http://www.mythtvtalk.com/requirements-12-tuner-backend-nas-pbx-server-15818/)

Phil

---

### Post by mikulator on 2014-05-07
Many will recompile the kernel to allow for additional dvb tuners but they don't use mythbuntu.

maybe I should ask my question differently...

If I wanted to change som settings at kernel level for mythbuntu (i.e. number of available dvb adapters) would I use menuconfig or is there another way in Ubuntu?

cheers

---

