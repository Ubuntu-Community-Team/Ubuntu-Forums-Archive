---
title: "Mythbuntu 10.04 Mythtv 0.24 Wont record"
date: 2011-02-26
forum: Mythbuntu
---

### Post by Archmage on 2011-02-26
I have been away for a few weeks and when I return home the hard drive had been filled and Mythtv did crash (although it should delete the recordings and leave 10 GB free).

I did clean up and now it seems to be running fine, however it will NEVER record everything not even show them in the upcoming recordings, although I have many recording rules and I'm even put some from the program guide as recording rules to test it.

However I'm able to watch live tv and it will work flawless.

I don't see any error message and I'm out of ideas.

---

### Post by tgm4883 on 2011-02-26
> **Archmage said:**
> I have been away for a few weeks and when I return home the hard drive had been filled and Mythtv did crash (although it should delete the recordings and leave 10 GB free).

I did clean up and now it seems to be running fine, however it will NEVER record everything not even show them in the upcoming recordings, although I have many recording rules and I'm even put some from the program guide as recording rules to test it.

However I'm able to watch live tv and it will work flawless.

I don't see any error message and I'm out of ideas.

I don't see any error messages either...

---

### Post by Archmage on 2011-02-26
Yeah, that was crazy. Everything is fine, but no matter what I did, it never record anything nor show anything in the upcoming recordings, while in the log everything was looking good.

I did find a strange way to fix it. While watching live tv I just hit "r" for recoding and now it is recoding everything just fine. (Also the upcoming recordings if full.)

---

### Post by xkev on 2011-06-05
> **Archmage said:**
> I did find a strange way to fix it. While watching live tv I just hit "r" for recoding and now it is recoding everything just fine. (Also the upcoming recordings if full.)

Confirmed.  This solved it for me too.  Very odd.

*mythtv 0.24.0+fixes.20110322 from mythbuntu lucid ppa*

---

### Post by xkev on 2011-06-05
> **xkev said:**
> Confirmed.  This solved it for me too.  Very odd.

*mythtv 0.24.0+fixes.20110322 from mythbuntu lucid ppa*

I take that back.  My eyeballs must have misparsed the upcoming recordings list.  It did not help.  I have some recordings that work fine, but anything I've created since going to 0.24 just won't activate unless I force it.

---

### Post by xkev on 2011-06-05
Hah.  Better reporting from the frontend (I rarely use it).  One of my backends was offline.  Duh.

---

