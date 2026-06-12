---
title: "Network between Ubuntu computers"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by gwu777 on 2010-09-17
Hi there,

I have just been through the forum about this and I haven't found a clear answer to what I think is a very simple question.

How do I access my file on my second ubuntu machine? I guess the irony is I found 100 of post on how to share file with windows and not a single post on how to share file between ubuntu machines!

The only document I have read is how to create a file server with NFS, despite probably wanting to do that in a near future, my windows mind would like to do simply the following:

Go into Network in Nautilus, view my other ubuntu machine (as I see my windows one - again fairly ironic) and browse through my shared file and folder. (I haven't shared any files yet, don't know how to do...)

Awaiting your advice...

---

### Post by Morbius1 on 2010-09-17
I'll have to admit there does seem to be some kind of conspiracy between Ubuntu, Samba, Gnome, and router manufacturers to make this more problematic than it needs to be ( although it always works for me ) but the most Windows-like process is this:

_ On machine A:_
Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
[COLOR=Blue]*It will ask you if you want to install "Windows Networking" - you do*[/COLOR]
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done
[COLOR=Blue]*Just like setting up a "Simple Share" in WinXP*[/COLOR]

_ On Machine B:_
Do exactly what you posted you want to do:
> Go into Network in Nautilus, view my other ubuntu machine (as I see my  windows one - again fairly ironic) and browse through my shared file and  folder.79.65% of the time it works just as advertised. The other 20.35% of the time has been known to cause severe depression as the problem moves away from samba itself and into networking itself as the source of the problem.

Try it, if it doesn't work wait for the NFS'ers to drop by an tell you how easy that method is.

---

### Post by gwu777 on 2010-09-18
> **Morbius1 said:**
> I'll have to admit there does seem to be some kind of conspiracy between Ubuntu, Samba, Gnome, and router manufacturers to make this more problematic than it needs to be (...)
79.65% of the time it works just as advertised. The other 20.35% of the time has been known to cause severe depression as the problem moves away from samba itself and into networking itself as the source of the problem.

Gosh these are precise statistics! I know of Samba and everything is already working out of the box with my ubuntu the way you have described. I just found ironic, that I need to desguise my machine as a windows machine to have it on my ubuntu network. (It no appears under "Windows Network"!

I was surprised that Ubuntu didn't have anything integrated by default to see other computer on the network as simply as Windows does.

---

### Post by ronnielsen1 on 2010-09-18
> I was surprised that Ubuntu didn't have anything integrated by default  to see other computer on the network as simply as Windows does.
I guess you haven't tried linking a box running windows 7 to any other OS including XP

---

### Post by Morbius1 on 2010-09-18
> Gosh these are precise statistics!Sarcasm never works in print ;)
> I just found ironic, that I need to desguise my machine as a windows machine to have it on my ubuntu network.I don't know if I would describe it as "disguising" a Linux machine as a Windows machine. It's just another protocol. It's a reverse engineered SMB protocol originally created so UNIX servers could provide services to Windows clients - but it's just another protocol.

---

### Post by gwu777 on 2010-09-18
> **ronnielsen1 said:**
> I guess you haven't tried linking a box running windows 7 to any other OS including XP

I actually have, and it is true that win7 works ever so well with win7, and is tricki-er with other OS; but once you get sorted, password and username, it is not that bad. I do prefer the added security it offers compare to older version. However, this is probably a discussion for another forum! :)

---

### Post by ronnielsen1 on 2010-09-19
> I actually have, and it is true that win7 works ever so well with win7,  and is tricki-er with other OS; but once you get sorted, password and  username, it is not that bad. 
I'm still trying to figure it out. From googling, homegroup does not seem to be an option and I'm not sure of what program to use that windows 7, XP and linux all are compatible with. Homegroup keeps trying to popup

---

