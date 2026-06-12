---
title: "Large Sustained Transfers"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Kissell on 2008-12-21
I'm going to be doing a 7TB transfer from one Ubuntu server to another Ubuntu server this week, and I'm looking for some input as to what application I should use to make this happen.

1) I could just use the GUI and copy and paste with Samba shares... ughh... 

2) Last time I did this I used FTP... not bad, I like that it shows me the transfer rate and allows resuming in case of a failure.

but thought I'd check to see if there's anything else better suited for this...  I've very interested in what does it quickest, like if something will transfer faster than other methods...  also I really need it to be able to recover if there's a failure...  say the switch hiccups, or the power goes out, or someone knocks a cable loose (the eSATA cables are very crappy on one of these servers)...  anyway, in the likely event the transfer isn't done and it quits, I need it to be able to resume the transfer and have confidence in it copying everything without having to start over on the 7TB.

What would you guys use?  I've really liked robocopy in windows for this sort of thing...  should I be looking at rcopy in linux?  what's best for this sort of operation?  Currently I'm planning on just using FTP again, but since I expect this to take a few days to copy I thought I'd check to see if there's something better before I start.

---

