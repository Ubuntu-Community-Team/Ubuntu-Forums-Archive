---
title: "Myth Player only -or- restricting recording and deleting options"
date: 2009-05-26
forum: Mythbuntu
---

### Post by colinnwn on 2009-05-26
Hi All,

I have MythTV on my personal TV, and I would like to allow my roommate to watch the recordings on my Myth backend from her computer or TV. But I really don't want her to be able to delete stuff, and I'd rather not her have the ability to schedule recordings. Can anyone recommend a solution to do this? 

I saw MythPlayer, but has the ability to delete, and it is no longer maintained. I also saw the Myth plugin for XMBC, but it too seems to be able to delete. My roommate and I share internet access on the same router, but I have our intranets on different subnets to keep our networks separate. I don't mind opening up a port or 2 between our networks, but I'd rather not grant full access to something like SAMBA, since I have personal files on an internal SAMBA share. Do I have any options to share Myth content?

Thanks.

---

### Post by ian dobson on 2009-05-26
Hi,

I can think of the following solutions:-

1) Setup a mysql user that only has read/search permissions and no delete permissions and use that for the player user.

I'm not sure if that could work, but it's worth a try.

2) If you can run mythfrontend on the other box then you could edit the thema file and remove the "delete" options maybe.

Regards
Ian Dobson

---

