---
title: "DVDs Won't Play on Karmic Koala"
date: 2009-12-10
forum: Multimedia Software
---

### Post by sfarber53 on 2009-12-10
I've been using linux in one form or another since 1995, but this is the greatest disappointment to me.  Once I rip a DVD using Windows (DVD Decrypter), Movie Player and VLC will play it back, no problem.  The problem is that none of these players will play a DVD directly.  Why?  I have all of the codecs loaded and the "data" will play once it has been ripped so why won't the original media work?

I'm sure I would be embarrassed to discover that this is caused by something simple that I've missed, but I don't think so.

Can someone please give me a hand?

Thanks in advance,

Steve

---

### Post by gordintoronto on 2009-12-10
Did you install the Restricted Extras?

---

### Post by sfarber53 on 2009-12-10
Yes, I've installed every codec and player I could get my hands on but no luck.

---

### Post by ajgreeny on 2009-12-10
You probably need **libdvdcss2** from [medibuntu]("http://www.medibuntu.org/").  Most commercial DVDs are encrypted and need this decryption library package to be read and usable.

Medibuntu is also very useful for more advanced versions of other multimedia packages.

---

### Post by sfarber53 on 2009-12-10
Thank you, thank you, thank you!

Adding medibuntu and libdvdcss2 solved my long standing problem.

You are a hero!

All the best,

Steve

---

### Post by sfarber53 on 2009-12-10
I just wanted to say that I love the way the gnu linux world works.  I'm sitting here in Ohio, USA and have just had my problem solved by a very kind gentleman from the UK.

This kind of access and cooperation is available in no other endeavor I know and I'm thrilled to be a part of it.

Thank you everyone!

---

### Post by Maheriano on 2009-12-10
This problem arises at least once a week and nobody ever searches before posting. I've helped 5 people already with the same thing.

---

### Post by slumbergod on 2009-12-10
> **Maheriano said:**
> This problem arises at least once a week and nobody ever searches before posting. I've helped 5 people already with the same thing.

If you are tired of helping then just ignore repeat messages. I never get tired of helping people; sadly, in recent days I've noticed a lot of sarcastic, pissy replies on here. I hope this forum doesn't lose the friendliness that makes it so great.

---

### Post by natravis on 2009-12-10
> **slumbergod said:**
> If you are tired of helping then just ignore repeat messages. I never get tired of helping people; sadly, in recent days I've noticed a lot of sarcastic, pissy replies on here. I hope this forum doesn't lose the friendliness that makes it so great.

I think the issue is not that he is tired of helping people, he is tired of helping people who refuse to even try to help themselves. I understand his frustration and in order to avoid pissy replies, I take your advice and ignore questions that can be solved by typing your question into google prior to posting.

---

