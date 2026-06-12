---
title: "k9copy &amp; dvd95 produce a tiny iso"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by phidia on 2007-10-25
I am having problems getting k9copy to produce a iso that is useful from a dvd.
Running k9copy or dvd95 (for that matter) produces a 135Mb iso but of course that isn't the entire movie-even though while k9copy runs it shows 13 or 14 titles being extracted.

I can't seem to get this 7.8GB movie into an iso i can burn. Does anyone have ideas? TIA

BTW I installed k9copy with synaptic and it pulled in all the dependencies that were required.

Note the computer I'm posting this about is a sempron 2600 with 1Gb of ddr running Feisty fawn

---

### Post by mcallenSchmee on 2007-10-25
It sounds like you haven't selected all of the titles or chapters you need for the iso. You can select all of the titles by clicking on the very top checkbox that is beside the name of the movie. The iso is probably too big for a dvd so go to the selection sidebar by clicking on select on the far right. you can then choose which languages you want for audio and subtitles, unchecking the ones you don't need will free alot of space. If it still won't fit on a dvd you can remove some of the special features or director's commentary.

---

### Post by phidia on 2007-10-25
> **mcallenSchmee said:**
> It sounds like you haven't selected all of the titles or chapters you need for the iso. You can select all of the titles by clicking on the very top checkbox that is beside the name of the movie. The iso is probably too big for a dvd so go to the selection sidebar by clicking on select on the far right. you can then choose which languages you want for audio and subtitles, unchecking the ones you don't need will free alot of space. If it still won't fit on a dvd you can remove some of the special features or director's commentary.

Thanks, i wish I could say that worked-but unfortunately not.I have 10Gb of free space but k9copy crashes as it gets to about 80% complete. No complaints i'm  long time linux/ubuntu user but I don't think I'll every fully get video copy.

Thx again.

OK It did work finally WOOOOO! The process could use some fine tuning but I'm happy it worked.

---

### Post by eimor on 2007-12-08
Same thing happening to me, dont know why but i selected all the contents in the dvd and still get a minuscule iso file, like 100mb or less, hope someone can help us.

---

### Post by mc4man on 2007-12-08
How much free space do you have after the dvd is mounted?

edit: check filesystem/tmp/kde-<user name>k9copy/dvd and see what size the VIDEO_TS folder is

---

### Post by eimor on 2007-12-09
i have a lot of space in the hdd, this is a recently formated pc and a 1 week installed ubuntu. Thanks for answering quickly.

Ps: I have the k9copy config in 4400mb so is there anything im missing in there?

---

### Post by mc4man on 2007-12-09
did you check the size of the temp folder?

---

