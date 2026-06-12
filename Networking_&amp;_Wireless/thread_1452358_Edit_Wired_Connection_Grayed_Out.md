---
title: "Edit Wired Connection Grayed Out"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2010-04-11
So I'm trying to edit my wired connection but the edit and delete buttons are grayed out. How can I go about getting the available? I want to make sure my connection is checked for all available users. I was able to edit my wireless connection on my laptop fine, just not my desktop.

Any help would be much appreciated.

---

### Post by Iowan on 2010-04-11
Which release are you using (Karmic?)? Are you editing from Network Manager applet or from System pulldown? Is wired connection is configured via NM, or is there a definition for it in */etc/network/interfaces*?

---

### Post by Muhnamana on 2010-04-11
Oh damn, there you go getting all technical on me. I'm still a noob when it comes to Ubuntu. I believe its 9.10 Karmic and I am editing from the Network Manager applet.

As far as your other question, not sure on that one. Sorry I'm not much of a help.

---

### Post by Iowan on 2010-04-11
2/3 isn't bad. System>About Ubuntu should tell which release you're using. You can use a text editor to view */etc/network/interfaces*. Ordinarily, it contains only:```
auto lo
iface lo inet loopback
```

---

### Post by Muhnamana on 2012-01-30
I completely forgot about this post and it seems like I'm having the same issue again when it comes to 11.04.

I keep getting the "no active connections found" and there are entries in the /etc/network/interfaces not what you have listed above though.

Any ideas?

*for clarification, this shows up when clicking on connection information. Is this a bug in 11.04? I also seen this in 11.10 but reverted back to 11.04 for other reasons. One more thing, I do have a network connection and have successfully browsed the information super highway.

---

