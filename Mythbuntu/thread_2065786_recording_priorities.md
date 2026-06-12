---
title: "recording priorities"
date: 2012-10-02
forum: Mythbuntu
---

### Post by deanie44 on 2012-10-02
hi everyone.  I am trying to get the hd homerun prime to record from mythtv and windows 7 media center.  mythtv seems to be "stuck" on tuner 1 for recording tv shows.  How do I make mythtv only record on tuner 3 instead of tuner 1.  I tried to prioritize the tuners, but that did not work.  Any help will be appreciated.  deanie44:(

---

### Post by tgm4883 on 2012-10-03
> **deanie44 said:**
> hi everyone.  I am trying to get the hd homerun prime to record from mythtv and windows 7 media center.  mythtv seems to be "stuck" on tuner 1 for recording tv shows.  How do I make mythtv only record on tuner 3 instead of tuner 1.  I tried to prioritize the tuners, but that did not work.  Any help will be appreciated.  deanie44:(

Don't add tuner 3 as an option?

---

### Post by goffa on 2012-10-04
Mythtv will use the lowest number tuner for recordings and the highest number tuner for live TV. You will need to delete all tuners/capture card and add them again in the order you want mythtv to use tuners for recordings. The last tuners you add will be used for live TV.

bit of an explanation here [http://forums.whirlpool.net.au/forum-replies.cfm?t=1858138&p=5#r89](http://forums.whirlpool.net.au/forum-replies.cfm?t=1858138&p=5#r89)

---

### Post by deanie44 on 2012-10-04
Hi. goffa.  If I numbered the tuner cards 0,1. and 2, Live tv will be on the last tuner=2.  Will the recordings be on tuner 1?  deanie 44

---

### Post by goffa on 2012-10-05
Mythtv will number the turner cards as they are defined. for example-

encoder 1
encoder 2
encoder 3

live TV will use encoder 3, recordings will be on encoder 1 & 2. The recording that starts first will be on encoder 1 the next recording will use encoder 2 (if encoder 1 is in use).

---

### Post by nickrout on 2012-10-05
If you define the tuner in mythtv, you cannot also use it in windows in on  another computer. They will interfere.

You could use, say, tuner 0 and 1 on linux and tuner 3 on windows, or any similar combination.

---

