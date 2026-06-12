---
title: "Remote sends twice in Mythfront-end"
date: 2009-12-04
forum: Mythbuntu
---

### Post by mongrol on 2009-12-04
Hi folks,
I've just done a fresh install of Karmic over my old hardy install and have the following issue.

My DVICO Fusion remote appears to send twice when inside mythfrontend. This means it skips enu entries, and if I press to enter a menu, it goes two levels down if it can. Obviously this is unusable. irw registers only one entry when testing. The remote config was done with the generator. Anyone seen this before?

---

### Post by gwagchunks on 2009-12-04
> **mongrol said:**
> Hi folks,
I've just done a fresh install of Karmic over my old hardy install and have the following issue.

My DVICO Fusion remote appears to send twice when inside mythfrontend. This means it skips enu entries, and if I press to enter a menu, it goes two levels down if it can. Obviously this is unusable. irw registers only one entry when testing. The remote config was done with the generator. Anyone seen this before?

I had a similar issue with my remote in 9.04 once, I found out it was due to 2 instances of lirc running (do a ps -A) and see how many lirc processes you have. Can't remember why I had 2 running?!

---

### Post by mongrol on 2009-12-04
Not that. Just one lircd process running.

---

### Post by mongrol on 2009-12-05
Ok, this is definitely a MythTV problem. irw shows the correct type of repeats.

```
00010046000053fe 00 down DVICO_MCE
00010046000053fe 01 down DVICO_MCE
0001004600005bfe 00 left DVICO_MCE
0001004600005ffe 00 right DVICO_MCE
00010046000051fe 00 up DVICO_MCE
00010046000051fe 01 up DVICO_MCE
00010046000053fe 00 down DVICO_MCE
00010046000053fe 01 down DVICO_MCE
00010046000053fe 02 down DVICO_MCE
00010046000053fe 03 down DVICO_MCE

```

Also setting the .lirc/mythtv file with delay=10 on every button, meaning ignore 10 repeats if they come in results in no change. Myth still interprets remote presses twice.

---

### Post by SiHa on 2009-12-05
Have you, somehow, got either two entries for each button in your lircrc, or have you got two files included in your lircrc, which both have Myth keybindings in them?

I've seen multiple presses when I accidentally had two entries for one of the arrow keys.

To test it, you could rename your ~/.lircrc file, copy a single button definition into a new one, and see if that button functions properly. You'll need to restart lirc for it to pick up the change.```
sudo /etc/init.d/lirc restart
```

---

### Post by t3chn0b0y on 2009-12-06
I went through the same type of problem coming over to 9.10.

you might check ~/.lirc/mythtv 

I was getting about 10 of every button, and I was getting
all sorts of numbers like 10 , 100  etc.. so when changing
to channel 2 it was giving me 210 .. I had to seriously
clean it..

---

