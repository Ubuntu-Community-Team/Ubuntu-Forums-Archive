---
title: "peerblock?"
date: 2012-08-26
forum: Multimedia Software
---

### Post by SirethSargas on 2012-08-26
as anyone aware of any software for ubuntu that does what peerblock does? sry if this post is in the wrong place.....

---

### Post by rectec794613 on 2012-09-08
Well, there is PeerGuardian Linux. Personally, I wouldn't really recommend it. The interface is very buggy and user-unfriendly, but the command line version does the job. Although, the developer is still maintaining it and it is getting better, at least.

Open a terminal and enter these commands to install it.
```
sudo add-apt-repository ppa:jre-phoenix/ppa
sudo apt-get update && sudo apt-get install moblock blockcontrol mobloquer
```

I hope you find it ok, and I also hope the bugs get fixed because as far as I know, there are no alternatives. :(

P.S. sorry nobody has posted until now. I was googling around for any new alternatives when I found this thread.

-Robert

---

### Post by jre on 2012-11-11
This advices to install the precessors of PeerGuardian Linux, the old moblock, blockcontrol and mobloquer. In the meantime I've made them empty reansitional packages. So you may directly install the new pgl from the same repository:
```
sudo apt-get install pgld pglcmd pglgui
```

Feel free to make bug reports! (pgl 2.2.2 with some bug fixes will be released today).

---

