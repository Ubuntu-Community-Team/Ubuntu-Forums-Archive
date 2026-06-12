---
title: "gnomebaker - problem with latest update"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by kievking on 2006-10-05
Gnomebaker detects my cd/dvd writer, and I verified that the burner works
correctly with other programs(kb3,etc).  The problem occurs when I attempt to burn an ISO. I select the correct cdrom/burner, it begins the write process, and then it opens the regular cd/rom tray and asks for a blank cd, even though the blank cd is already in the burner tray. The previous version of gnomebaker worked flawlessly. Has anyone else had this experience?

---

### Post by Jonnhy on 2006-10-06
I have a problem similar to yours I am using to gnomebaker 0.6.0-0ubuntu1~dapper1 ( Backport ) I have put east problem like bug in launchpad 
[https://launchpad.net/bugs/63805](https://launchpad.net/bugs/63805) 
:(

---

### Post by factor on 2006-10-09
I have same problem too, in fact i was about to post about it. It also happens when trying to format a dvd+rw. don't know if it happens with a dvd-rw (notice the "-" instead of "+").

Regards.

---

### Post by neutrino82 on 2006-10-09
same problem. gnomebaker recognize DVD reader and DVD burner but when I try to burn a DVD it opens the DVD reader. Previous version worked.

---

### Post by phansiizwe on 2006-10-09
I also have this issue when burning an audio CD. I have a DVD player and a DVD writer. In the burn properties window (after pressing the burn button) I could only select my burner, OK so far. After converting files from .flac to CD audio gnomebaker asks me to put a blank disc into the DVD player (mentioned by its name: PIONEER DVD-ROM ATAPIModel DVD-106S ...)

---

### Post by Jallu59 on 2006-10-10
The problem came to me also. While copying disk from reader to writer Gnomebaker opens the readers tray after disk been read, and tries to write with that reader and not with the writer configured in the dialog.

Patch was to force the previous version (5.xxx) of Gnomebaker in Synaptic.;) 

I wonder how this kind of error could even get into the distributed version. Not even messmakers in Redmont have been able to create so obvious errors in their distributions. Has the maker of this version tested it with only one drive ?[-X 

Yours
Jallu59

---

### Post by puppy on 2006-10-10
Hands up for exactly the same error here - hope they fix this soon :???:

---

