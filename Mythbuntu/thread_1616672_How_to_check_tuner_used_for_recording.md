---
title: "How to check tuner used for recording"
date: 2010-11-08
forum: Mythbuntu
---

### Post by tonycollinet on 2010-11-08
I've got a novat 500, and one of the tuners works better than the other (the bad one gives frequent video distortion, and sound dropouts).

Is there anyway I can find out which tuner was used for a recording, so I can determine which is the "good" one?

Thanks

---

### Post by LowSky on 2010-11-08
you can try recording two shows back to back and specify which tuner they use during the recording, then playing them back to see which looks better

OR run this command from terminal when you have two simultaneous recordings.

```
mythtv-status
```

it will tell you what it being record on what tuner.

FYI: you might have to install it first... not sure if its installed by default

---

### Post by rburt on 2010-11-08
You could look at the actual file in the recordings directory.
It has a format like:

1213_20101108013000.mpg

Starting left to right this tells us; Tuner 1, channel 213 _ 11/08/2010 at 01:30 (24 hour time).

So find the recording in question, and the very first number of the filename is the tuner number.

---

### Post by tonycollinet on 2010-11-08
Excellent - that'll do it.

---

### Post by uncle hammy on 2010-11-08
> **rburt said:**
> You could look at the actual file in the recordings directory.
It has a format like:

1213_20101108013000.mpg

Starting left to right this tells us; Tuner 1, channel 213 _ 11/08/2010 at 01:30 (24 hour time).

So find the recording in question, and the very first number of the filename is the tuner number.

I don't believe that's cirrect.  The format you list is correct, but the first section is the channel only, has nothing to do with the tuner.  I have 12 tuners, and every single file starts with 1.  The section before the _ also exactly matches a channel id in the channels table in every single file.

The format is XXXX_YYYYMMDDHHMMSS.mpg where XXXX is the channel.

I guess that's a long winded way of saying you can't get the tuner from the file name.

Another simple way to do it is to start two recordings, open MythWeb and go to the status page.  It tells you what every tuner is doing.

---

### Post by nickrout on 2010-11-08
rburt is definitely wrong in his interpretation of the filename.

the correct method is to look at the mythbackend.log file. the following is an extract from mine:

> 2010-10-30 13:58:33.017 Started recording: The Headspace with Dylan C: channel 2936 on cardid 1, sourceid 1
2010-10-30 13:58:35.085 TVRec(1): rec->GetFileName(): '/mnt/sdb2/recordings/2936_20101030135900.mpg'


---

### Post by rburt on 2010-11-08
My apologies.
It must be a weird coincidence on my system because I have 3 tuners and anything recorded on tuner 1 starts with a 1, tuner 2 starts with a 2, etc.
Anyway, I guess that doesn't hold true for everyone.

---

### Post by nickrout on 2010-11-08
no problem. do you have 3 different video sources? I think maybe the first digit might be the video source.

As I have 8 tuners all tied to the same source, they all seem to start with the same digit.

---

### Post by rburt on 2010-11-09
Yes that must be it.  I do have 3 video sources.
Each has a different subset of channels.
One is an analog tuner, one is an HD-PVR connected to a cable box and lastly an ATSC tuner.

---

### Post by bcg30506 on 2010-11-09
> **LowSky said:**
> you can try recording two shows back to back and specify which tuner they use during the recording, then playing them back to see which looks better

OR run this command from terminal when you have two simultaneous recordings.

```
mythtv-status
```

it will tell you what it being record on what tuner.

FYI: you might have to install it first... not sure if its installed by default

Thanks for the tip on mythtv-status.  I'd never heard of this command and it is a nice little tool.  Maybe it should be installed in a default mythbuntu installation?

---

### Post by nickrout on 2010-11-09
> **bcg30506 said:**
> Thanks for the tip on mythtv-status.  I'd never heard of this command and it is a nice little tool.  Maybe it should be installed in a default mythbuntu installation?

It used to be, dunno why it isn't any more.

---

