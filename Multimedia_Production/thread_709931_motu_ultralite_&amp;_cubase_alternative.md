---
title: "motu ultralite &amp; cubase alternative"
date: 2008-02-27
forum: Multimedia Production
---

### Post by davesec on 2008-02-27
hi!

i have a motu ultralight that connects to the computer via a firewire card. is this thing going to work at all on ubuntu?

second, is there anyway i can export a bunch of cubase sx3 projects into ardour or whatever the popular alternative is?

awesome, thanks!
dave

---

### Post by chipants on 2008-02-28
i'm pretty sure the answer is "no" for both of your predicaments.

motu has been very unhelpful in getting their devices to work under linux. a list of firewire audio interfaces supported by FFADO (formerly freebob) is available at [http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

and, as far as i know, there is no currently available application that will allow the use/conversion of cubase files.

the best option (right now) is to export individual tracks as audio files and import them into your preferred linux audio DAW.

sorry.

---

### Post by vo!d on 2008-02-28
If you're talking about audio files, I agree with the above post. But I'd say it's impossible to export midi track arrangements and all used vst plugins and settings.

---

### Post by chipants on 2008-02-28
> **vo!d said:**
> If you're talking about audio files, I agree with the above post. But I'd say it's impossible to export midi track arrangements and all used vst plugins and settings.

yes, i was referring to audio files only, largely in response to the original poster's mention of ardour. i should have been more explicit. the current stable release of ardour doesn't have midi recording or editing functionality anyway, so it was kind of a moot point. (although it's coming in future versions!)

---

### Post by davesec on 2008-02-29
does anyone know if cubase runs under WINE?

thanks for the answers, by the way! i'm definitely excited to play around with ubuntu studio in the future and see what sort of music i can make with their software.

dave
myspace.com/hrswhip

---

### Post by chipants on 2008-02-29
> **davesec said:**
> does anyone know if cubase runs under WINE?

thanks for the answers, by the way! i'm definitely excited to play around with ubuntu studio in the future and see what sort of music i can make with their software.

dave
myspace.com/hrswhip

you can always use the application compatibility database at [http://appdb.winehq.org/](http://appdb.winehq.org/)  to check for specific applications.

i didn't see an entry for the newest version of cubase. just cubase le, which apparently works to some degree. however, i did an actual search for cubase 4. a few different versions of that release apparently do not work at all.

i say this all the time to people: if you're trying to use linux as a professional music creation platform, run native applications!

you will likely never get 100% performance/compatibility using a windows audio app on linux. if you simply must use a proprietary windows audio app, you should just stick with windows. sucky, huh?

fortunately, there are a plethora of quality audio apps for linux. it would be silly to overlook them. i haven't had a windows machine at home for the better part of a decade. there's no way i'd go back now.

---

### Post by Stochastic on 2008-02-29
> **chipants said:**
> 
i say this all the time to people: if you're trying to use linux as a professional music creation platform, run native applications!

you will likely never get 100% performance/compatibility using a windows audio app on linux. if you simply must use a proprietary windows audio app, you should just stick with windows. sucky, huh?

fortunately, there are a plethora of quality audio apps for linux. it would be silly to overlook them. i haven't had a windows machine at home for the better part of a decade. there's no way i'd go back now.

I couldn't agree more with that.

But I'd like to add that it's always beneficial to ask Steinberg or whoever WHEN they're going to get around to porting to Linux.  Even if they blow you off as a loon that has no business sense, we all know that there is a market here (a growing one) for that software and the more we ask the sooner it will come.  Though I do prefer FOSS, some commercial apps are quite well designed and the Linux DAW could benefit from having them.

---

### Post by chipants on 2008-02-29
> **Stochastic said:**
> I couldn't agree more with that.

But I'd like to add that it's always beneficial to ask Steinberg or whoever WHEN they're going to get around to porting to Linux.  

steinberg, especially, has been been relatively unhelpful in many ways. specifically, considering VST support. they couldn't possibly care any less about the linux community. i assure you, they aren't planning on porting any of their audio software.

please don't think we haven't tried to get major developers and hardware manufacturers in the professional audio industry to play nice. we have and we continue to beg for application support, and drivers. most of the big players won't even consider more open specifications so that we can write our own drivers.

this has been an ongoing struggle for a decade. it's partly because of their dismissing us that we have such wonderful open source audio software for linux. they wouldn't (and generally won't) help, so we've created our own solutions.

i strongly advocate purely open source audio solutions, and generally avoid proprietary audio software.

---

