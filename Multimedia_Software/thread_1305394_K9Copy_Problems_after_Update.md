---
title: "K9Copy Problems after Update"
date: 2009-10-29
forum: Multimedia Software
---

### Post by malleus74 on 2009-10-29
Hi! I'm running Ubuntu Studio 8.10 and K9Copy 2.30. I can't update to 9.04 or higher because of my laptop's ati 1200x graphics card. Testing it right now, I'm getting the error:

Unable to open file /tmp/kde-rick/k9copy/HARRY_POTTER_SORCERERS_STONE/VIDEO_TS/VTS_01_1.VOB

Any thoughts?

---

### Post by malleus74 on 2009-11-01
Bump

---

### Post by jimmers on 2009-11-02
Not wishing to teach anyone to suck eggs, but have you installed libdvdcss2.
I had problems with K9 Copy after installing, and I found that by installing K9 Copy first, it would work okay.
Worth a try anyway.

---

### Post by malleus74 on 2009-11-02
Thanks for the idea, :) but it was a bit more tricky. 

I'm going to mark it solved. Apparently what happened is the output goes to /tmp, and there's a write-access issue all of a sudden after working dozens of times. 

I'm just creating a folder under /Home and 'hiding it, and having K9Copy delete the files after the iso is complete as a workaround.

---

### Post by jimmers on 2009-11-03
Glad you have solved it, what I do is Create a Folder with the Name of the DVD, in my home folder, and save to that as the out-put directory, never had to hide it.

---

