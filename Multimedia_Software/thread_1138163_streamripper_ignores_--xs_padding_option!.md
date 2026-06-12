---
title: "streamripper ignores --xs_padding option?!?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by kubumar on 2009-04-26
Hey,

I try to record a radiostation with streamripper. My command is streamripper [http://fm4.nobody.at:8080/fm4-hq.ogg](http://fm4.nobody.at:8080/fm4-hq.ogg) -s -d /files/streams --xs_padding=600:60000

The stream-tags are too late for at least 30sec. therefore the --xs_padding option. But it seems streamripper just ignores this option. It shows no effect. 

Am I using the wrong code?


It drives me crazy! Please help!

martin

---

### Post by mtron on 2009-05-28
i guess it's because you are recording an ogg stream, and according to "streamripper -h" Splitoptions are for mp3 only.

> Splitpoint opts **(mp3 only)**:
      --xs2                        - Use new algorithm for silence detection
      --xs-offset=num              - Shift relative to metadata 
      --xs-padding=num:num         - Add extra to prev:next track 
      --xs-search-window=num:num   - Search window relative to metadata
      --xs-silence-length=num      - Expected length of silence 

---

