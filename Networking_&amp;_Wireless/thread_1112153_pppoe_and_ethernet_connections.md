---
title: "pppoe and ethernet connections"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by adc on 2009-03-31
Hello,

I'm having a problem with keeping up and functional a pppoe connection and an ethernet one at the same time. I'm in a private network and I use pppoe to access the internet. At first I used Network Manager to manage my connections but when I connected to the pppoe one the ethernet connection was automaticly closed. Even though my internet connection was working fine I couldn't access the private network anymore.
Next I tried to bypass the Network Manager and decided to manually start and manage the two connections. They seem to be working fine up to a point when the pppoe connection stops working. The connection is still up but I cannot access the internet anymore. After I manually close and and restart the pppoe connection it works fine. Untill the same thing happens.
At the moment I am using Ubuntu 8.10 but I had this problem in Fedora Core 9 too.

Does anybody have an idea why this is happening? I'm preety sure that this problem is related to the way pppoe connection works in general, but I haven't found an answer till now. Maybe I'm just google-ing the wrong thing.


Edit: I forgot to mention that the computers that have Windows do not have this problem and a friend of mine that also had Fedora Core had this problem too.

---

### Post by deviant on 2009-04-17
I`m having the same problem with my pppoe connection in campus. 
I`v looked at every possible log and came up with nothing useful. 
What I did find out is that the DNS get broken after a while (I have NO idea why), that`s why your internet connection seems not to work anymore. 
For example, if you are connected to a IRC server or using a P2P app (like a torrent client) you will notice that they still work.

How about you? Better luck than me with finding a solution?

---

### Post by ZhuaSD on 2009-07-28
I have this problem too.  So far, it is better in 9.04.  Before I had to restart the whole comp, now I just have to stop and re-start the connection.  Still its a workaround.

---

### Post by madmax1735 on 2009-07-28
please use 

sudo plog 

to see the pppoe log and post them here.

also if you think its a dns related problem, make sure that those are listed in the /etc/resolve.conf as name servers.

you can verify the name servers against the those on the windows computer on your network.

---

