---
title: "channel information is wrong"
date: 2008-02-15
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-02-15
so the channel information is usually pretty consistent, and rarely wrong. but recently all the channel information is wrong. like it will say there are movies on the history channel (when there arent) and the movies on HBO all have the wrong information. ive tried to update by running mythfilldatabase, but its still wrong. any ideas?

---

### Post by newlinux on 2008-02-15
Have you changed anything (added a different source, or input, or channels)? Are the channel numbers and names right, just the info wrong? Maybe try refreshing the entire program table:

```

mythfilldatabase --refresh-all

```

---

### Post by gsrcrxsi on 2008-02-15
yea the channel numbers and names are right, just the information about each program is way off. ill try to refresh the whole table.

---

### Post by gsrcrxsi on 2008-02-15
w00t that fixed it. thanks man.

---

### Post by newlinux on 2008-02-16
Your welcome. Been there and had that problem :) whenever I have problems with wrong channel data or missing data refresh-all usually fixes it. For me it usually happens after I make a change to one of the sources.

---

