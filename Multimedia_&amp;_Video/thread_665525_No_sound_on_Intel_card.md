---
title: "No sound on Intel card"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by orrie on 2008-01-12
I have just followed a [guide](https://help.ubuntu.com/community/HdaIntelSoundHowto) since the sound was lagging on the Intel 82801H card. The motherboard is an ASUS.
And, after rebooting and installed those three and rebooted again, then I get a message that no sound card is detected at all..
Before I did all this, I wrote:
```
lspci|grep Sound
```
Then I got a long output (one row), but now I got nothing actually.

What is the sollution to this...?

---

### Post by balaknair on 2008-01-12
Hello Orrie
Could you please type this command in a terminal and post the output
lspci -v

also do you know what linux kernel you're using?

---

