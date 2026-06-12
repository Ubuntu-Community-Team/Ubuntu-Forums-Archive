---
title: "[SOLVED] Grip tags cut off?"
date: 2008-07-09
forum: Multimedia Software
---

### Post by ZOOstation on 2008-07-09
When I rip CDs with Grip, it cuts off the tracks' tags after a certain character limit. How can I stop it from doing that?

---

### Post by rainwalker on 2008-07-09
I don't know about Grip, but if you need to edit tags I would recommend installing tagtool (it will be under Applications > Sound and Video > Audio Tag Tool)

---

### Post by mcduck on 2008-07-10
Are you using IDv1 or IDv2 tags? I believe IDv1 only supports fairly short tags..

---

### Post by rainwalker on 2008-07-10
> **mcduck said:**
> Are you using IDv1 or IDv2 tags? I believe IDv1 only supports fairly short tags..

He's right, but tagtool can copy the v1 tags to the v2 one and then you can fill in the missing characters :)

---

### Post by ZOOstation on 2008-07-11
I don't know what version the tags are, it's whatever Amarok uses.
And it's not that the tags inherently don't go beyond that character limit. I can edit them in Amarok to be as long as I want. It's that Grip creates the file, organizes it, names the file and its directory properly, but its tags are all cut off past a certain letter and I have to fill in the rest myself, which is tedious.

---

### Post by mcduck on 2008-07-12
> **ZOOstation said:**
> I don't know what version the tags are, it's whatever Amarok uses.
And it's not that the tags inherently don't go beyond that character limit. I can edit them in Amarok to be as long as I want. It's that Grip creates the file, organizes it, names the file and its directory properly, but its tags are all cut off past a certain letter and I have to fill in the rest myself, which is tedious.

You have to change the setting in _Grip_, not in Amarok. Grip is able to write both IDv1 and IDv2 tags. If you have configured it to use IDv1 that's what you get.

So, if Grip is configured to use IDv1 it writes IDv1 tags to your files, and as that doesn't allow long tags the parts that are too long will be cut off. Then you open the file in Amarok, complete the tags and Amarok saves them as IDv2 tags.

Instead just configure Grip to use IDv2 in the first place, and you'll get the long tags.

---

