---
title: "Mythweb - Unknown Program"
date: 2008-10-18
forum: Mythbuntu
---

### Post by funkydan2 on 2008-10-18
Hi,

I'm pretty sure that the problem that I'm about to describe has only occurred since a certain package related to codecs was updated, but I can't remember which one it was.

Since that time in MythWeb
[LIST]
[*]The 'thumbnail' image in the Recorded Programs list is now a black sqaure (i.e. the image doesn't exist),
[*]If I click on the far left of that box the HyperLink is still there, but when I click on the image I get a dialog box popup which says 'Warning: Unknown Program'.
[/LIST]
This has only occured recently, and older recordings can still be accessed normally through mythweb.  Newer recordings can still be accessed and watched through the full MythTV frontend.

I assume if there's an error occurring, there should be something in a log file somewhere, but I've had a look and can't see them.

Any ideas of how to fix this problem, or should I just hang out till the end of the month and hope that it's fixed in Ibex?

---

### Post by Namain on 2008-11-10
I'm actually having this same problem with some of my older recordings.

From what I can see, it looks like it happens with any recordings that are no longer in my Mythbox's program listing (ex.  I recently recorded most of "the Simpsons: Treehouse of Horror" episodes, and since they are not scheduled for showing any time soon, and the old listings have been purged from my system, I receive this error when I try to view them).

---

### Post by funkydan2 on 2008-11-10
I got this to work after upgrading to Intrepid.  I think the problem was related to some bugs in the version of PHP5 installed with Hardy.

However, there was more discussion about these sorts of problems [Here](http://ubuntuforums.org/showthread.php?t=959211)

---

