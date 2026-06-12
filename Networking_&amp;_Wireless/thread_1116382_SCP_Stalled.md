---
title: "SCP Stalled"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by sarky7 on 2009-04-04
I am using scp to copy a 45 megabyte file to my web hosting server.

It works for about 15 seconds fine and then slows down and finally says "stalled".

If I try using SFTP with FileZilla, the same result happens: 

It will work for 10 to 30 seconds and then stall.

What can I do to copy this file?




Even if I can somehow force scp to break the connection and then automatically resume the copy it would resolve the problem.

---

### Post by kreggz on 2009-04-04
if you try at the commmand line you can use the -v flag to output error messsages, it might help you locate the problem

---

### Post by sarky7 on 2009-04-04
I found a workaround.  With FileZilla, I set the settings to "resume transfer" and then have a timeout of only 30 seconds.  If it times out it will restart now.

(It times out maybe 30 times during the transfer, but will eventually work).

---

