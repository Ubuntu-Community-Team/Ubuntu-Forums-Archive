---
title: "Full Scan misses channel 9 (Australia) - are the transport streams correct?"
date: 2007-11-21
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-21
I have a newly setup mythbuntu (7.10) machine and just tried my first full channel scan (I am using DVB-T cards).  It found everything
i.e.
Channels 7, 10, SBS, ABC and all the individual streams within them

But it found none of channel 9's.  Anyone else had problems like this?

It makes me think maybe the list of transport streams might be missing that frequency.  I notice you can edit this data, and add new streams, so does anyone know where I can find a table of this transport stream data for Australia, so I can check it?

---

### Post by ubnewbie2 on 2007-11-21
Ok, mythbuntu definitely is missing the channel 9 transport streams. I found the following info

```

# T freq          bw    fec_hi fec_lo    mod       transmission-mode guard-interval hierarchy
# ABC
T 226500000 7MHz   3/4   NONE     QAM64      8k                    1/16             NONE
# Seve
T 177500000 7MHz   2/3   NONE    QAM64      8k                      1/8             NONE
# Nine
T 191625000 7MHz   3/4   NONE    QAM64       8k                     1/16           NONE
# Ten
T 219500000 7MHz   3/4   NONE    QAM64       8k                      1/16           NONE
# SBS
T 585625000 7MHz   2/3   NONE    QAM64       8k                       1/8            NONE
```

And manually added the info for channel nine, as best as I was able to decipher the parameters.  I scanned again, and it found channel 9.

So, maybe it got left out of the config in Mythbuntu and can be added next time?

---

