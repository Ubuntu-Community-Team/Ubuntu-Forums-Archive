---
title: "Nuvexport keeps restarting"
date: 2008-11-15
forum: Mythbuntu
---

### Post by lingenfr on 2008-11-15
For the last rev or two of myth, my nuvexports have been messing up. I normally just export to medium quality, medium sized xvid/mp3/avi but for the last few revs, each recording I try to export ends up in multiple (4-8) of varying sizes. Usually one will have the entire show, but the others are short. Here is the userjob that worked previously:

nuvexport-xvid --mencoder --quantisation 12  --a_bitrate 128 --nice 10 --input="%FILE%"

If anyone has experienced and solved this, I would appreciate some help. Thanks.

---

### Post by lingenfr on 2008-11-17
Bump.

---

### Post by ian dobson on 2008-11-18
Hi,

Do you see anything in the myth backend log file. Could you run nuvexport-xvid from the command line a dump all the output here.

Regards
Ian Dobson

---

### Post by lingenfr on 2008-11-23
At this point, it seems to be working. I guess that updates fixed it. If it recurs, I will post the log.

---

