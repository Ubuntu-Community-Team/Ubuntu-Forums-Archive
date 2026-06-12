---
title: "Network error"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by matrixnis on 2011-01-22
..

my ubuntu is on the win network and I have  problem connecting,internet works great thru local network...even changing ip adress works ,I tried to erese connection and create new ,also I ttried automatical network...

and always shows me this message

[IMG]http://lh5.ggpht.com/_LczGLEzDP1c/TTqp699TvqI/AAAAAAAABYA/g9U4G11Q6Cs/s800/Screenshot-1.png[/IMG]


interested thing is that connecting to external ftp servers on windows platform works great as you can see bookmarks work like charm..

[IMG]http://lh6.ggpht.com/_LczGLEzDP1c/TTqr6tdh_lI/AAAAAAAABYI/JLJEo5N9lLU/s800/Screenshot-2.png[/IMG]

---

### Post by grahammechanical on 2011-01-22
I get the same message but then, I am using just one computer that is not connected to any network except the Internet. I did not expect to make a connection.

Surely, the server needs to be told to give your Ubuntu machine permission to share folders and files with other machines on the network?

Regards.

---

### Post by matrixnis on 2011-01-22
the machine..in this case win server works with all computers on the network with no problem...only with ubuntu...

every folder is properly shared and work group is the same like on the ubuntu...

---

### Post by kgriff on 2011-01-22
I ran into almost this exact problem a couple years ago.  Try installing Gnome Commander and see if you can connect to the network share that way.  When I had this issue, I found it to be a problem with Nautilus.  Using Gnome Commander, I bypassed the problem and was able to use the network share.

---

### Post by matrixnis on 2011-01-22
i tried already commander,krusader,interesting thing is that same problem is  both on automatic and manual ip ...

---

### Post by cariboo on 2011-01-22
Can you see the shares when you run:

```
smbtree
```

---

### Post by matrixnis on 2011-01-22
no I can not...

---

### Post by matrixnis on 2011-01-26
after this morning update network started working....
now i have aces to all shared folders...


[IMG]http://lh5.ggpht.com/_LczGLEzDP1c/TT_PbDu1roI/AAAAAAAABYU/azdjptIHdDE/s800/Screenshot-3.png[/IMG]

---

