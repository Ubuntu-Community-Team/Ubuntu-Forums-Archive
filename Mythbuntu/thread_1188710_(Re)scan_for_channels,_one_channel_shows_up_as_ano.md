---
title: "(Re)scan for channels, one channel shows up as another"
date: 2009-06-16
forum: Mythbuntu
---

### Post by mathog on 2009-06-16
After rescanning for channels today (ATSC, with an antenna using an HDHomeRun) oddly enough, channel 34 (as seen in MythTV) was actually channel 62 (by broadcast content).  In mythtv-setup 34 showed digital channel 35, which is I believe correct, yet 62 is what showed up when it was tuned in.  Finally I deleted all channels, did a full ATSC scan, and it did not find it.  This is all very odd, since before the rescan channel 34 was OK.  As far as I can tell every other station is where it should be.

I tried to add 34 manually, but there was no ATSC option present, just NTSC, SECAM, PAL. etc.

What translated Digital (ATSC) channel 35 to KHZ?  Is it from SchedulesDirect (which would make sense if it varies by area) or is it a fixed table so that ATSC 35 is the same throughout the US?

And more importantly, how do I convince Mythtv to use channel 34 again?

Thanks.

---

### Post by mathog on 2009-06-16
Curiouser and curiouser:

 hdhomerun_config 1011F855 scan /tuner1/channelmap t1_scan.txt

look through the results:

SCANNING: 599000000 (us-bcast:35)
LOCK: 8vsb (ss=100 snq=82 seq=100)
PROGRAM: 1: 62.1 KRCA-DT
PROGRAM: 2: 62.2 KRCA-DT

This is where I expected KMEX to be.  There is no KMEX listing in the file.  But see:

[http://en.wikipedia.org/wiki/KMEX-TV](http://en.wikipedia.org/wiki/KMEX-TV)

which does list KMEX at digital 35.  So where is KRCA supposed to be?

[http://en.wikipedia.org/wiki/KRCA](http://en.wikipedia.org/wiki/KRCA)

ALSO at Digital 35!

Can it be that the FCC really assigned two stations within the same general broadcast area (Los Angeles) the same Digital channel????

---

### Post by mathog on 2009-06-16
Ah, from the KMEX link in the preceding post, down near the bottom:

```
After the analog to digital transition on February 17, 2009,
KMEX will move its digital signal back to channel 34, currently used
for its analog signal. Digital channel 35, currently used by KMEX-DT
will be the final digital channel assignment for KRCA-DT. KRCA is
required to abandon its pre-transition digital channel 68, as it lies
outside of the post transition core channels 2 through 51.

```

But the hdhomerun_config scan shows nothing on bcast:34.

Let's see what the antenna sites say:

tvfool.com has KRCA at 68 and KMEX at 34.
antennaweb.org has KRCA at 45 and KMEX at 34.

This might all make sense if KMEX moved to a transmitter on the very far side of Mt. Wilson from my home, between the last time we tuned them in and now.  Having a mountain between their transmitter and our antenna could completely block their signal.  Something similar happend for channels 2, 9, and 11, although in none of those cases was the signal completely blocked.  Might as well be though for 2 though, since it is unwatchable.

---

### Post by LowSky on 2009-06-16
The FCC said that During the digital switch some stations may move to other channels to help free up frequencies.

---

### Post by mathog on 2009-06-16
> **LowSky said:**
> The FCC said that During the digital switch some stations may move to other channels to help free up frequencies.

Yep.  Evidently things got a bit out of synch during the transition, with the info from SchedulesDirect still showing KMEX on digital 35, when KRCA had already moved to that frequency.  Thankfully this transition will soon be over.

Begin Rant

Overall the Analog to Digital transition has for us resulted in a net loss of service, or at least a loss of the service we care about.  Even after building and installing a 4 bow tie UHF antenna (because the set top UHF antenna was hopeless) there are still many channels which now have too low a signal strength to view.  With analog we could watch these low power stations, and just ignore the static, but with digital they are completely unwatchable.  Now Univision (KMEX) is gone, CBS is unwatchable 50% of the time, local channel 9 about 80% of the time, local channel 11 about 25%. (Which means we can't reliably record any of these, but can occasionally watch them live for a few minutes.)  In exchange for these channels we used to watch, we now have very good access to channels broadcasting in Vietnamese and Mandarin - which isn't of much use since we don't speak these languages.  The stations that do come in are sharper, which doesn't change the content any.

I just hope that the geometry issues we face in the San Gabriel valley with respect to line of sight access to the transmission towers on Mt. Wilson are not very common elsewhere in the country.

My wife pointed out that the Time Warner trucks were scurrying around our neighborhood yesterday.  No doubt they were hooking up cable for many folks who had believed the "plug the rabbit ears into the converter box and watch DTV" rosy scenario.

End Rant

---

### Post by LowSky on 2009-06-16
At least you can get over the air. I live in a dead zone between New York City and Albany. I get 5 local stations that broadcast out of Kingston and Poughkeepsie, NY. The locals short wave guys dont broadcast anything good, they are just religious channels.

I need Cable TV to get NYC local channels. Which works great but means I pay for expensive Cable TV.

---

