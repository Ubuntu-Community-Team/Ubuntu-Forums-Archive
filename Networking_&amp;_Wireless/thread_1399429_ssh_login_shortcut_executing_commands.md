---
title: "ssh login shortcut executing commands"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Orange Kingdom on 2010-02-05
Hi,

I made a small script to passwordless login to server with ssh.

gnome-terminal  --command "ssh  myserver"

I can login but i want to execute a command, lets say a "ls".
So when i doubleclick the script it should login (which works) and gives me a listing (ls) on that server.


gnome-terminal  --command "ssh  myserver"  ---> and then execute ls on that server.

anybody?

---

### Post by hwttdz on 2010-02-26
Well to do this from the command line it's just 
"ssh user@host ls path/to/dir/*.txt" or whatever, anyway I'm not sure how exactly you're launching the command so that makes it harder.

Note that it will go to town with replacements unless you tell it not to.  i.e. "ssh user@host ls ~" works if your username on both machines is the same otherwise you need "ssh user@host "ls ~"" to prevent it from replacing ~ on the local machine.

---

