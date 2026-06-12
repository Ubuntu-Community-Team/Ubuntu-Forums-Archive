---
title: "problem create audio cd  with russian names songs."
date: 2009-10-30
forum: Multimedia Software
---

### Post by din on 2009-10-30
Hi
i want to create audio cd with russian names files.
when i add the files, program add them to project, but
names of files became unreadable.
also this happens in k3b.
i added russin to languages. 
also i can type rssian in terminal.
anyone to help here?

---

### Post by din on 2009-10-30
when i run audacious i have ???????? instead of song names.

actually i found this:


**Why do I have ????? - ???????? (Invalid UTF-8) in my playlist?**

You haven't set up chardet, or you do not have appropriate fallback encodings defined, or your locale is set incorrectly.

For what it's worth, Audacious will attempt to use the character detection feature first if you have it enabled, and it can generally figure out what encoding is valid for text in a specific region. Additionally, Audacious can make use of Mozilla's universal character set detection library if it is available.

If the character detection feature doesn't support your locale, you can always provide fallback encodings. You can seperate them with most common seperator values.


but how it helps me?

---

