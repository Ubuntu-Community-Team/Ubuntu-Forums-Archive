---
title: "How to change frontend allowng remote control?"
date: 2008-07-26
forum: Mythbuntu
---

### Post by mark467 on 2008-07-26
I tried to use the mythweb remote control and it says no frontends allow remote control. I have looked through MCC and ran mythtv config but dont see where to change it.

---

### Post by superm1 on 2008-07-26
Like via the telnet interface?  That's in mythfrontend's options.  If you mean VNC, that's in mcc options.

---

### Post by mark467 on 2008-07-26
From MythWeb. There is a keyboard on one of the pages that supposedly is like a remote keyboard. I have it connected to the frontend but it just says no frontends have been selected when trying to press any of the keys.

---

### Post by danellisuk on 2011-04-27
I know this is an old post, but I found this today whilst looking for a solution to this problem using mythtv 0.24.

Here's what is required for the mythweb remote to work:-

[LIST]

[*]Make sure the frontend has "Network Remote Control interface" enabled (within Settings->General, on the last page).

[*]Also make sure that the server running mythweb can resolve the IP address of the frontend machine, as only the machine name of the frontend is stored in the database.  This is what was causing the problem on my system, and adding the frontend hostname to */etc/hosts* did the trick.

[/LIST]

---

