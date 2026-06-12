---
title: "sound only turns on with volume above about 10%"
date: 2011-03-01
forum: Multimedia Software
---

### Post by fpgdu on 2011-03-01
my sound has been only turning on if i turn it up beyond about 10%. it didnt used to do this. This has been happening for quite a long time, i just now wanted to bring it to the forum.

---

### Post by zenwalker on 2011-03-01
go to terminal and run alsamixer command. Check if all the sound levels shown are max!

---

### Post by fpgdu on 2011-03-01
> **zenwalker said:**
> go to terminal and run alsamixer command. Check if all the sound levels shown are max!

Thank you zenwalker.
I'm not sure what making sure they are all to the max does other than making my speakers play much louder then i want. I want to play at below 10% but it jumps 2 notches when i press the up arrow in alsamixer command.

---

### Post by fpgdu on 2011-03-01
bump

---

### Post by lidex on 2011-03-01
Have a look here and see the section "Volume range anomalies":
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by fpgdu on 2011-03-02
> **lidex said:**
> Have a look here and see the section "Volume range anomalies":
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Thanks! The first instruction under that section fixed the problem.

---

### Post by lidex on 2011-03-02
Excellent. Please mark the thread solved using 'Thread Tools' up top.

---

