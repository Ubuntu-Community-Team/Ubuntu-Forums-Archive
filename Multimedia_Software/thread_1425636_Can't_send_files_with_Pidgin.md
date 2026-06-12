---
title: "Can't send files with Pidgin"
date: 2010-03-09
forum: Multimedia Software
---

### Post by damnated on 2010-03-09
I have no idea when this issue started. I remember that I was happily sending and receiving files last October/November.

Anyways: ATM I can't send files to people who use yahoo messenger. I'm using a yahoo account as well. In the past this worked without a problem. Now, I can only receive files, which is weird, considering that if I can use yahoo's protocol in one direction, it should work in the other one as well. When I drag a file in the 

I'm using the latest (2.6.6) version of Pidgin, updated today from 2.6.2.  I had the same problem with that version as well, trying to fix this issue was the sole reason behind the update.

---

### Post by damnated on 2010-07-09
I'm bumping this, because under Lucid the 2.7.1 version can't even receive files through the yahoo protocol. Am I the only one with this?

---

### Post by jazz_air_312 on 2010-07-16
Hello! I'm running Ubuntu 9.10 and have upgraded to the latest version of pidgin, 2.7.1, for the exact same reason of resolving the send/receive problem. I also use a yahoo account, and when a friend tries to send me a file, as soon as i accept it it gives the error the the sender has cancelled the transfer. When I try to send a file and the recipient accepts it, the file transfer hangs with the message "waiting for accept". I encountered the problem in pidgin 2.6.6, upgraded to 2.7.1, reinstalled by compiling from source, but the result is the same, the file transfer doesn't work.

---

### Post by damnated on 2010-07-16
> **jazz_air_312 said:**
>  when a friend tries to send me a file, as soon as i accept it it gives the error the the sender has cancelled the transfer. When I try to send a file and the recipient accepts it, the file transfer hangs with the message "waiting for accept". 
Those are my symptoms as well. It seems there's a general issue with the yahoo protocol then.

---

### Post by peacewithall on 2010-07-24
I have this too, I tried googling and didn't come up with much at all, I tried different versions too, file transfers just alert me as being cancelled, as soon as I begin the transfer.

---

### Post by jazz_air_312 on 2010-07-24
I remember the file transfer working when I first installed Ubuntu 9.10 in february, but I can't recall the pidgin version I had then. What version of pidgin did you try, and where can you find older versions of pidgin, to compile from source? 
I've recently tried some options reported by users that fixed the file transfer on previous versions of pidgin, mainly: pidgin accounts -> modify yahoo account -> advanced tab -> tick the "Use account proxy for SSL connections" box, as well as changing the proxy type on the Proxy Tab, but none of these options worked.

---

