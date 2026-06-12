---
title: "Another 'bulletproof xorg is useless' thread..."
date: 2009-04-29
forum: Multimedia Software
---

### Post by NT4usB on 2009-04-29
So I'm working remotely, ssh into my MythTV box.
x is jacked so I stop gdm to tweak xorg.conf. Start gdm but that stupid *'x is running in lo res mode'* notice is stuck on the display so gdm won't restart.
...Actually, it won't completely stop until I go find a keyboard, plug it in, and click on that stupid popup about do I want to run on low graphics mode...
Then, If I don't get back to the terminal and stop gdm again quickly enough, stupid bull... x goes right back into starting x in low res mode again.

So, how do we disable the idiot proofing and get this Linux box to run like Linux instead of that other built for idiots OS?

---

### Post by NT4usB on 2009-06-10
gharris on the mythtv mailing list was kind to point out the answer. Here's the [link]("https://answers.launchpad.net/ubuntu/+question/14320") and solution should anyone else find use for it.

> Comment out the line that reads:

 FailsafeXServer=/etc/gdm/failsafeXServer

In /etc/gdm/gdm.conf

This will disable the functionality.

---

