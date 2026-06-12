---
title: "Samba shares seen, but only accessed with IP address"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by argentum2f on 2009-11-07
I just upgraded from feisty server edition to hardy server. The smb.conf is the same I had before (checked that).
I've got everything pretty much working but have this problem with samba.
From a windows machine if I enter
\\servername\
the shares all come up. I can see them but if I try to access them (ex. \\servername\data) it prompts for a username/password, and it doesn't work no matter what I enter
If, on the other hand, I try the server ip
(ex. \\192.168.0.5\data)
it works just find. I can access the share.
I can also ping using just the servername, and it works just fine.
Where do I need to look to solve this?
All the computers on the network(~10) have the network drives mapped with the servername, and I don't want to set it all up again manually with IP's.

---

### Post by argentum2f on 2009-11-09
I beat my head over this for a while and never figured anything out. Went home for the weekend and came back and everything's working just fine and dandy. Not often I've had problems fix themselves like that.
I think I did try something with the folders group and user owner before I left (they seem to have got change in the upgrade). Maybe it was because of that.

---

### Post by Thirtysixway on 2009-11-09
Glad it all worked out okay :)

---

