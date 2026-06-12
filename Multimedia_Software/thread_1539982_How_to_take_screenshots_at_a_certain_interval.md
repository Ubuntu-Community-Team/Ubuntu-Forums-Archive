---
title: "How to take screenshots at a certain interval?"
date: 2010-07-27
forum: Multimedia Software
---

### Post by sordid on 2010-07-27
There are some great tools running under Windows that allow you to set any given interval and it would take a screenshot, save it and so on.
I want to make automated screenshots from a live ticker and unfortunately won't be able to make them myself as I'll be in the office and work when the actual action takes place. :(
Is there any piece of software that does this for me?
Or maybe a simple script?
Cheers.

---

### Post by sordid on 2010-07-27
OK, found a solution.

---

### Post by lemsst on 2011-12-15
How did you do it? Would you mind sharing..

---

### Post by lemsst on 2011-12-15
> **lemsst said:**
> How did you do it? Would you mind sharing..

i googled it and found the solution too.. sorry

---

### Post by FakeOutdoorsman on 2011-12-15
> **lemsst said:**
> i googled it and found the solution too.. sorry

Let's break this cycle of non-answer answers. And the solution is ...?

---

### Post by lemsst on 2012-03-29
> **FakeOutdoorsman said:**
> Let's break this cycle of non-answer answers. And the solution is ...?

This is the code. I could not find the original source. The **aplay ok.wav;** is optional.

```
#!/bin/bash
i=0; while true; do import -window root cover$i.jpg; sleep $1; aplay ok.wav; let i=$i+1;done
```

**To run:**

lem@lemUbuntu:~/Pictures/tmp$ ./timershot 5

where 5 is the interval (in seconds)

**Test Suite:**

Playing WAVE 'ok.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
Playing WAVE 'ok.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
Playing WAVE 'ok.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono

The files are saved in the same directory.

**To Stop:**

CTRL + C

---

### Post by codemaniac on 2012-03-29
i can remember a utility called scrot i often used while being on linux systems .It is really cool and has the capability of taking screenshots with countdown switch .

---

