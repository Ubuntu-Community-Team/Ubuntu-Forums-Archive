---
title: "What's the reason for Jack's xrun policy?"
date: 2010-11-10
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-11-10
I'm sure the question has been asked and answered elsewhere, but Google isn't turning it up.

Why is Jack so brutal about killing processes? I suspect it has something to do with the callback model, but I'm not sure.

I'm having a discussion/argument with a collaborator. He argues that Linux plus Jack is inherently unstable for real-time audio work because there's always the possibility of an unpredictable set of circumstances that would cause CPU use to spike up over Jack's threshold, and then your show is over. I don't have an answer for that, except that xruns are extremely rare for me (and only happen when I make a mistake in my SC code).

James

---

