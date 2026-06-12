---
title: "[SOLVED] How can I change Recording / Playback Group?"
date: 2008-10-24
forum: Mythbuntu
---

### Post by SiHa on 2008-10-24
OK, I've got a list of stuff I've recorded. Until I'd fully got to grips with Myth,I didn't bother assigning a recording group when scheduling, so it's all in the 'Default' group.

I'd like to be able to re-assign recordings to a different group, so that I can use the display filters on the View Recordings menu, but I can't seem to find a way of doing this, from the Frontend GUI, at least.

Am I missing something, or can't I do this from the frontend?

A thought occurs while typing this, could I do this via Mythweb?

Any help appreciated.

Simon

---

### Post by ian dobson on 2008-10-24
Hi,

With mythweb you can change the recording group. Another way would be to modify the tables directly in MySQL using phpMyAdmin or directly from the commandline.

I would recommend  mythweb.

Regards
Ian Dobson

---

### Post by SiHa on 2008-10-24
Thanks Ian,
I'll have a look at the Mythweb option tonight - I really don't want to go delving into MySQL just yet. Not until I have a backup system in place anyway!

Cheers,

Simon

---

### Post by SiHa on 2008-10-24
Nope - Mythweb will show the recording group, but it won't let me change it. Ah well - It's not important.

---

### Post by SiHa on 2008-10-28
Now there's a thing.

I looked today, and now when I bring up the menu (cursor right) on a recorded programme within 'watch recordings', and select change storage options -> change recording group, there's the goups to select from.

I think the problem for any that may stumble across this, is that although I had created a new recording group (when scheduling a recording), it was only available once the recording was actually made.

---

### Post by SiHa on 2008-10-29
I've filed this as Bug [[COLOR="Blue"]#290699[/COLOR]](https://bugs.launchpad.net/mythbuntu/+bug/290699)

If I create a recording group, it is only available to add other recordings to, once it has something in it. If I delete all items from a group, the group disappears also, and has to be created again, by the longwinded process of scheduling a recording and creating a new group in the storage options.

---

