---
title: "Commercial skipping: how reliable is it?"
date: 2009-02-24
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-24
Hi All

I was feeling very proud of myself a couple of days ago: I'd finally figured out how the commercial skipping in MythTV worked and watched an entire episode of CSI that seamlessly skipped over all the adverts without my having to do a thing.

Imagine my disappointment when I watched a recording of ER this evening and had to manually fast forward through all the adverts.

So, my question is this: is this because the commercial skipping technology is imperfect, and works sometimes and doesn't work somtimes, or is it actually pretty good and in fact I haven't figured out all the settings I need to skip adverts automatically?

Many thanks
NM

---

### Post by august495 on 2009-02-24
I use the Myth defaults for commercials and I am about 90% successful in cutting out commercials. Tricky FOX has decided to overlay their logo on commercials recently.

---

### Post by klc5555 on 2009-02-25
> **NautiusMaximus said:**
> Hi All

I was feeling very proud of myself a couple of days ago: I'd finally figured out how the commercial skipping in MythTV worked and watched an entire episode of CSI that seamlessly skipped over all the adverts without my having to do a thing.

Imagine my disappointment when I watched a recording of ER this evening and had to manually fast forward through all the adverts.

So, my question is this: is this because the commercial skipping technology is imperfect, and works sometimes and doesn't work somtimes, or is it actually pretty good and in fact I haven't figured out all the settings I need to skip adverts automatically?

Many thanks
NM

The commercial-flagging technology would be fairly reliable, save that broadcasters are acutely aware that such things exist, and are quite persistent in modifying their broadcasts to foil common autoskipping methods. If the technology just missed ads it would merely be a waste of time, but it also regularly mis-marks some program content as commercials on all the channels I normally record and/or archive, under the defaults or whatever other flagging algorithm I have cared to set up. 

Manually skipping through commercials, on the other hand, I find to be 100% reliable, and much less irritating.

---

### Post by 4dognight on 2009-02-25
> **NautiusMaximus said:**
> Hi All

Imagine my disappointment when I watched a recording of ER this evening and had to manually fast forward through all the adverts.



Are you sure it had run the commercial flagger job? My experience is it is about 90% accurate in flagging. Sometimes I have to backup and manually do a fast forward.

---

### Post by newlinux on 2009-02-25
> **4dognight said:**
> Are you sure it had run the commercial flagger job? My experience is it is about 90% accurate in flagging. Sometimes I have to backup and manually do a fast forward.

ditto - been using it for years and it is 90-95% accurate. Lately it seems even better than that. A couple of things I have noticed:

1. Sometimes turning the autoskip while watching a recording just doesn't work for me, even though the commercials are flagged. So I just wait until a commercial comes and hit the commercial skip button (z on the keyboard, I believe) and it still skips the commercial. Not sure what is up with the autoskip not working.

2. For a while my commercial flagging jobs were failing intermittently. Check your logs on the programs where commercial skip apparently isn't working to make sure the mythcommflag job ran to completion. If it didn't then you need to troubleshoot that.

---

### Post by ian dobson on 2009-02-25
Commflagging actually works quite well for me.

I found adding the option CommDetectMaxCommBreakLength for my master backend and setting the value to 600 improved the comm detection for very long commercials.

Have a look here [http://www.mailinglistarchive.com/mythtv-dev@mythtv.org/msg11779.html](http://www.mailinglistarchive.com/mythtv-dev@mythtv.org/msg11779.html)

Regards
Ian Dobson

---

### Post by jMon54 on 2009-02-25
Commercial skipping works great for me with the exception of football games where it nearly always skips the kickoff after a side scores and there is a change in possession.  I think it is because the logo stays on during it.  I've come to just manually skipping since it's so easy and reliable.  But I am pretty happy with the way it works for everything else including episodes on Fox of House and 24.

---

### Post by newlinux on 2009-02-25
> **NautiusMaximus said:**
> 
Imagine my disappointment when I watched a recording of ER this evening and had to manually fast forward through all the adverts.


I should also note, that you don't have to fast forward the entire time through the commercials. You can skip predetermined lenghts like on a Tivo and you can direct seek (e.g. if you enter "45i" you will go directly to the 45th minute of a broadcast. So if your commercials start at around 12 if you press "16i" you'll essentially do a 4 minute skip and go directly to the 16th minute of the show - most commercial breaks are around 3:30-4:30 minutes).

---

### Post by NautiusMaximus on 2009-02-27
> **4dognight said:**
> Are you sure it had run the commercial flagger job? My experience is it is about 90% accurate in flagging. Sometimes I have to backup and manually do a fast forward.

No, I'm not sure it had run the commercial flagger job.

When setting up the TV channels I made sure that commercial flagging using all available methods was the default behaviour. I have also set the option to automatically skip commercials using the playback options of the front end. Is there something else I need to do as well?

Thanks
NM

---

### Post by newlinux on 2009-02-27
> **NautiusMaximus said:**
> No, I'm not sure it had run the commercial flagger job.

When setting up the TV channels I made sure that commercial flagging using all available methods was the default behaviour. I have also set the option to automatically skip commercials using the playback options of the front end. Is there something else I need to do as well?

Thanks
NM

I'd recommend investigating the two things I wrote in the earlier post. When it doesn't auto skip the commercials does pressing the z button still skip the commercial? This will let you know whether it is a detection problem or a frontend autoskip problem.

---

### Post by NautiusMaximus on 2009-03-08
> **newlinux said:**
> I'd recommend investigating the two things I wrote in the earlier post. When it doesn't auto skip the commercials does pressing the z button still skip the commercial? This will let you know whether it is a detection problem or a frontend autoskip problem.

OK, I've tried that. The results were pretty variable.

Sometimes, nothing happend at all. Sometimes, it worked nicely and skipped to the end of the adverts. Sometimes, it just skipped a minute or two and I had to press z again before it would go right to the end of the adverts.

And finally, and by far the most annoying, it sometimes skipped to the end of the following set of adverts so I then had to rewind to the end of the adverts I was trying to skip.

Is this normal?

Thanks
NM

---

### Post by newlinux on 2009-03-08
> **NautiusMaximus said:**
> OK, I've tried that. The results were pretty variable.

Sometimes, nothing happend at all. Sometimes, it worked nicely and skipped to the end of the adverts. Sometimes, it just skipped a minute or two and I had to press z again before it would go right to the end of the adverts.

And finally, and by far the most annoying, it sometimes skipped to the end of the following set of adverts so I then had to rewind to the end of the adverts I was trying to skip.

Is this normal?

Thanks
NM

Doesn't happen that often with me (but it does happen) - about 90-95% of time it works fine, but when it doesn't what youa re describing is what happens. Might success rate  might be a function of the programming and types of commercials I'm skipping. You don't have to rewind to get back to where you were. You can skip back too - I think it is the "q" key. It goes backwards throught he breakpoints. When it doesn't work for me, I use direct seeking and just skip 3 or 4 minutes.

---

