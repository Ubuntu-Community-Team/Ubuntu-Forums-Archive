---
title: "sound problems"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by genefrench on 2007-06-19
i am running feisty on an acer aspire 5610...and have a wierd sound problem...
when i go to system..preferences...sound...the first three sound test work ... however sound capture just gives me a crackling noise...as a result...none of the tvtuner programs will produce sound...nor will kopete produce any sounds...however all other sound functions work correctly...i have an hsf internal modem using the Audio device: Intel Corporation 82801G ... using snd_hda_intel module and drivers...i understand i must have a conflict somewhere?? can anybody please help me...
thanks in advance
gene french

---

### Post by Gremlinzzz on 2007-06-19
Don't but did you check the guide   [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Sound)

---

### Post by genefrench on 2007-06-21
thanks for your reply...slowly figuring the problems out

this fixed the sound in tvtime!!!
sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp &

gene french:popcorn:

---

