---
title: "Managing Music on a Heterogeneous Network"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by Jamie Jackson on 2007-06-27
Apologies in advance for this rambling brain-dump...

I've got:
[LIST=1]
[*]a Win2K machine running iTunes (this is the "music server")
[*]wife's Mac iBook 
[*]kids' Edubuntu laptop
[*]my Ubuntu laptop (which I'm posting from)
[/LIST]

I'd like to be able to use machines 2-4 as clients, on which no music files are stored. I'm perfectly happy letting machine 1 host the files, and organize/download music through its iTunes.

On machine 2 (iBook), it seems seems my wife is using the "server's" music library on its filesystem (by mounting the share first). I guess this is working out for her. 

However, I'm not sure what to do on *ubuntu. Do any of the players act as simple clients (no local file importing/downloading and no attempts at reorganization of music on the remote "server")? Of course, I don't mind (actually I'd prefer it) if they cache info for speeding up future accesses, but I don't want the "client" players to download or compete with the "server's" iTunes for music organization.

Suggestions?

UPDATE: While looking at the iBook's iTunes configuration, I noticed the "share music library on local network" option. Is this the thing I need to be exploring on the "server's" iTunes configuration? I'll go try to find/read the iTunes docs for that...

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-06-27
A lot of info/ideas [here]("http://tinyurl.com/3dnxx9"), but it's all iTunes talk, and only for Mac/Win.

---

### Post by Jamie Jackson on 2007-06-27
So far, using Rhythmbox, and pointing the library to the server's library share (over SMB) seems to be working. I hope it's not trying to reorganize the library in the background. ;)

---

