---
title: "Problem connecting to channels with sopcast player"
date: 2018-05-11
forum: Multimedia Software
---

### Post by saikari on 2018-05-11
Hi,

I have Ubuntu 16.04 and have installed sopcast from ppa:linuxthebest.net/sopcast
However, I am incapable of viewing any channel. Whenever I try to connect, nothing gets displayed and there is just a message at the bottom of the sopcast player window which says "Connecting" then "Retrying channel". This goes on indefinetely.
From looking on the forum for similar issues, one of the causes pointed out is that library /libstdc++.so.5 is absent or misplaced. However, I seem to have the library in the right place. 
Here is the result of my ls command for the library:

 ls -l /usr/lib/libstdc++.so.*
lrwxrwxrwx 1 root root 38 may  6 21:35 /usr/lib/libstdc++.so.5 -> /usr/lib/i386-linux-gnu/libstdc++.so.5
lrwxrwxrwx 1 root root 42 may  6 21:35 /usr/lib/libstdc++.so.5.0.7 -> /usr/lib/i386-linux-gnu/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root 38 may  6 21:35 /usr/lib/libstdc++.so.6 -> /usr/lib/i386-linux-gnu/libstdc++.so.6
lrwxrwxrwx 1 root root 43 may  6 21:35 /usr/lib/libstdc++.so.6.0.24 -> /usr/lib/i386-linux-gnu/libstdc++.so.6.0.24

Can anyone suggest what I can do to get sopcast working?
Many thanks.

---

### Post by howefield on 2018-05-11
Duplicate thread closed.

Feel free to bump your original thread once a day if no response rather than creating a new thread.

---

