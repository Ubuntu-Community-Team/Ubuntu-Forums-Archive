---
title: "Xmms"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by techgy on 2008-01-19
I've been trying to install XMMS onto my Linux Ubuntu v7.10 system.
I've looked in the Package manager and add/remove and it's not listed.
I understand that it's in a repository, but which one and how do I get to it?

Keep it simple folks, I'm new to Linux.

Thanks!

:)

---

### Post by jimrz on 2008-01-20
just add the "universe" repo

---

### Post by yabbadabbadont on 2008-01-20
To elaborate:

System->Administration->Synaptic Package Manager
Then
Settings->Repositories
Enable the Universe repository and save your change.  Hit the Reload button.  Now search for xmms and it should show up.

---

### Post by techgy on 2008-01-20
Thanks for the response. I search the Settings/Repositories and didn't see anything related to Universe. There were several boxes that were not checked regarding restricted items and I checked those, but nothing that shows a list of repositories.

From what I can glean from the help files the Repositories are either on CD or on-line.
Since I don't have the CD - I downloaded the Linux install file, I assume that the repositories are On-Line - but where.

---

### Post by jimrz on 2008-01-20
> **techgy said:**
> Thanks for the response. I search the Settings/Repositories and didn't see anything related to Universe. There were several boxes that were not checked regarding restricted items and I checked those, but nothing that shows a list of repositories.

From what I can glean from the help files the Repositories are either on CD or on-line.
Since I don't have the CD - I downloaded the Linux install file, I assume that the repositories are On-Line - but where.
on the first tab ( "Ubuntu Software") in Settings/Repositories, make sure that the line "Community-maintained Open Source software (universe)" is checked. If it already is, uncheck then re-check it and exit. It will tell you that the repos have changed and you need to refresh. Click the refresh button on the toolbar, then Search "xmms" (without quotes) and it should come up. If this does not work, please post the contents of you /etc/apt/sources.list here.

---

### Post by techgy on 2008-01-20
That did the trick! Thanks :)

One hurdle over - lots more probably to go. 

:)

---

### Post by disturbedite on 2008-01-20
i'd like to recommend using audacious instead of xmms.  xmms has been dead for a long time, afaict.  audacious is basically a "newer" version of xmms that is still actively developed.  it has many great features not present in xmms.

---

