---
title: "Need help with mythweb permissions"
date: 2008-06-13
forum: Mythbuntu
---

### Post by mathew_davis on 2008-06-13
I have setup a Ubuntu 8.04 install and installed Myth-Control-Centre on top of it.  It seems to be working for the most part.  I can record live television play music, online streaming shuts down mythfront end for some reason but I don't really care at this point.  But I would like to get myth web working. 

My mythweb music, and mythweb recorded tv streaming doens't work.  I think it has to do with a permission thing but I am not sure what I did wrong.  If I go to mythweb using the 127.0.0.1/mythweb on the local host I can play music and watch the streamed tv, but if I do it remotely it doesn't.  I have a router that is forwarding the ports so is there maybe a port I need to open up to it?  I am just pretty confused as to why it doesn't work.  Maybe I haven't given rights to Apache not really sure though.  Any help or a point in the right direction would be nice.

Thanks,
Matt

---

### Post by funkydan2 on 2008-07-08
Can you connect to your mythweb machine when you're using another computer on the same local network?
Can you connect to mythweb if you use the external ip address (rather than 127.0.0.1) on the same machine?

---

### Post by Lester_Burnham on 2008-07-08
Maybe just comment out the 127.0.0.1 in /etc/mysql/my.cnf if it's not already.

---

