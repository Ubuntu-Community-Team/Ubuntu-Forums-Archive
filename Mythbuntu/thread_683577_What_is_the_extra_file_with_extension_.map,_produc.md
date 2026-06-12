---
title: "What is the extra file with extension .map, produced by mythtranscode?"
date: 2008-01-31
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-31
When I use mythtranscode in my user job, on a recording file, the output .mpeg file is created, as desired, in my videos directory, but another file with the same name, but with a .map extension, is also created in the videos directory.

Anyone know why, and what it's for?

---

### Post by stdPikachu on 2008-01-31
Not a clue (unless it's something to do with the cutpoints?), how big is it? Does it change in size during the transcode process?

---

### Post by ubnewbie2 on 2008-01-31
> **stdPikachu said:**
> Not a clue (unless it's something to do with the cutpoints?), how big is it? Does it change in size during the transcode process?

It's a text file, and it's about 250k for a 10GB recording. It's full of numbers and the start of it looks like this

```
Type: 9
0 14
10 514062
22 1142798
34 1798158
46 2465806
58 3115022
70 3797006
82 4409358
94 5064718
106 5810190
118 6418446
130 7055374
142 7704590
154 8370190
166 9027598
178 9699342
190 10422286
202 10975246
214 11536398
226 12169230
238 12828686
250 13510670
262 14260238
274 14989326
286 15708174
```

---

### Post by stdPikachu on 2008-01-31
Aha, I think it might be a position map, a log of which frame the transcode has currently gotten up to. Not quite sure what the number represent though, they're either too big or too small for things like frame numbers, file size (as in current position the transcode is at) maybe. What are the end values like?

---

### Post by Nikas on 2008-01-31
The recordedseek table in the database that mythtv uses looks a bit like that.

[http://www.mythtv.org/wiki/index.php/Recordedseek_table](http://www.mythtv.org/wiki/index.php/Recordedseek_table)

Mine:
chanid	starttime	mark	offset	type
1001	2007-12-26 17:00	0	0	9
1001	2007-12-26 17:00	15	251544	9
1001	2007-12-26 17:00	30	507224	9
1001	2007-12-26 17:00	45	762904	9
1001	2007-12-26 17:00	60	1018020	9
1001	2007-12-26 17:00	75	1273700	9
1001	2007-12-26 17:00	90	1529380	9
1001	2007-12-26 17:00	105	1784496	9
1001	2007-12-26 17:00	120	2039988	9
1001	2007-12-26 17:00	135	2295292	9
1001	2007-12-26 17:00	150	2550784	9
1001	2007-12-26 17:00	165	2804208	9
1001	2007-12-26 17:00	180	3060076	9
1001	2007-12-26 17:00	195	3316132	9
1001	2007-12-26 17:00	210	3571624	9
1001	2007-12-26 17:00	225	3827492	9
1001	2007-12-26 17:00	240	4083548	9
1001	2007-12-26 17:00	255	4336784	9
1001	2007-12-26 17:00	270	4592464	9
1001	2007-12-26 17:00	285	4848896	9
1001	2007-12-26 17:00	300	5104576	9
1001	2007-12-26 17:00	315	5358940	9
1001	2007-12-26 17:00	330	5614244	9

And so on. :)

---

### Post by ubnewbie2 on 2008-01-31
> **stdPikachu said:**
> Aha, I think it might be a position map, a log of which frame the transcode has currently gotten up to. Not quite sure what the number represent though, they're either too big or too small for things like frame numbers, file size (as in current position the transcode is at) maybe. What are the end values like?

Huge:)

So I suppose I can delete them?  They cause confusion when using myth video in file browse mode.

---

