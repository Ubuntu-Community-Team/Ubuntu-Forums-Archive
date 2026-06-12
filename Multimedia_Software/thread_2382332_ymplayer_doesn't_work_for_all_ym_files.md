---
title: "ymplayer doesn't work for all ym files"
date: 2018-01-11
forum: Multimedia Software
---

### Post by dalekky on 2018-01-11
I've installed ymplayer (from stymulator package) and for the most part, it works, but occasionally some files it throws up an error.
The problem files play in other players on other systems, but ymplayer doesn't seem to be able to recognize them.

An example of an unplayable file: [http://www.cpc-power.com/YM/Venom%20Strikes%20Back%201-2%20(1988)(Gremlin%20Graphics)(Ben%20Daglish).ym](http://www.cpc-power.com/YM/Venom%20Strikes%20Back%201-2%20(1988)(Gremlin%20Graphics)(Ben%20Daglish).ym)

The error is:
Error in loading file Venom Strikes Back 1-2 (1988)(Gremlin Graphics)(Ben Daglish).ym: Unknow YM format ! (sic - yes there is an "n" missing in the error message)


Is there some fix for this or is there an alternative ymplayer for linux?

---

### Post by Holger_Gehrke on 2018-01-12
A quick check using 'file' tells me that this is not an ym-file but a lharc archive. Installing lhasa and unpacking the archive gives a file 'Venom Strikes Back 1-2 (1988)(Gremlin Graphics)(Ben Daglish)().ym5' which works just fine in ymplayer.

Holger

---

### Post by mc4man on 2018-01-12
It can also play in [Audio Overload ]("http://www.bannister.org/software/ao.htm")player though ao needs to be started with 
padsp ao
or 
padsp /path/to/ao

---

### Post by dalekky on 2018-01-12
@Holger_Gehrke
@mc4man

Thanks Holger & Mc4man,
That fixed it.
I did look at Audio Overload earlier, but could not figure out how to use it. But thanks to your new information about how to start it, I will give it another go.

---

