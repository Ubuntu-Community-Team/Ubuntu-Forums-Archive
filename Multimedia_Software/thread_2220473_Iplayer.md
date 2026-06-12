---
title: "Iplayer"
date: 2014-04-28
forum: Multimedia Software
---

### Post by valephotofix on 2014-04-28
Me being a newbie how can I make Iplayer work on my system I have Ubuntu 14.04 installed all my youtube videos work fine .
thanks
Andy.

---

### Post by speartip on 2014-04-28
I assume you mean the BBC iplayer.
To download programs from the BBC, use get-iplayer, it's in the repos. After installing,
Run "get-iplayer"  in a terminal (without the "") & a list of what is available will be displayed.
If you know the program you want, eg. The crimson field, then run "get-iplayer crimson" & the episodes will be listed.
To download a program, each episode starts with a number, eg. 1002, 1003 etc so, then you need to run "get-iplayer -g 1002" or whatever the number is of the program you want.
You can also download multiple programs at once. The Crimson Field above has 4 episodes with the numbers 1002-1005. If you want to download them all, then run,
"get-iplayer -g 1002 1003 1004 1005".
Hope this helps.

---

