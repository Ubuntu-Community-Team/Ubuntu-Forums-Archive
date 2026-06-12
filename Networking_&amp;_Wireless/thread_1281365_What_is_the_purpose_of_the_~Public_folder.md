---
title: "What is the purpose of the ~/Public folder?"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by John Baptist on 2009-10-03
By default, each user has a ~/Public folder. In older versions of Ubuntu, and even today in other distributions, such as Fedora, this folder could be easily shared using the WebDav protocol, via the gnome-user-share utility. All shared Public folders on the local network would be visible in the Network folder (under the Places menu).

More recently, though, gnome-user-share has been replaced with nautilus-share, which is based on Samba, not WebDav. Despite some rough spots, this seems to be an improvement has Samba is understood by Windows machines, and the interface lets you share arbitrary folders, not just ~/Public.

So, I have several questions, given this turn of event:

1. Since ~/Public no longer has special meaning with the new default file sharing method, why does it still exist? Does it have any special meaning or should it be removed?
2. A disadvantage of the new system is that shares no longer show up in the Networking folder, not even shares from the local machine. Is there a way to fix this? Is there a way to force nautilus-share to use WebDav instead of Samba?

---

### Post by Gourgi on 2010-01-21
bump :confused:

---

### Post by labatts on 2010-12-26
Well, I'll bump this too since I found this wondering what the answer was...

---

### Post by Boondoklife on 2010-12-26
It exists as a simple place to put files you want to share with others. While it is not setup by default to be shared, it is still a great idea to keep it.

As far as the shares not showing up in the networking folder, this may just be a networking issue on your side as it works just fine here. I did not configure anything beyond the right click share and checking the boxes.

---

