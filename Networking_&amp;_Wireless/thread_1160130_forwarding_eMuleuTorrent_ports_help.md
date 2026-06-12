---
title: "forwarding eMule/uTorrent ports help"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by augustowloch on 2009-05-15
hello people!

i have a problem sharing internet thru an ubuntu server. yesterday i read the great article  ([http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)). it helped to understand a little bit more how iptables works, but i still have the same problem (seems that my understanding is still very limited hehehe).

anyway, i want just to share my scenario and if someone can drop a couple of lines, i'll be eternally grateful :D

the ubuntu [COLOR=Navy]server[/COLOR] 9.04 is directly attached to my ISP provider's modem on **eth0 **(with dynamic ip).
on it's second network adapter, **eth1**, aka [COLOR=Navy]192.168.1.1[/COLOR], is connected my [COLOR=DarkOliveGreen]second computer[/COLOR] (running windows vista) aka [COLOR=DarkOliveGreen]192.168.1.2[/COLOR].

as i am a total newbie, in order to share my internet connection from eth0 to eth1 and share my lamp servers (share them on my lan and wan), i installed:
- *lamp *
- *squid *(it works perfectly sharing http protocol on port 3128 )
- *dante *(on port 1080. thanks to this i can connect my eMule and uTorrent, but with no traffic)
- *samba *(to gain access to my site's document root)

final result, almost everything works perfectly. 
i can even acces my server from PuTTY.
problem is, i can not download/upload files with emule nor uTorrent. they only connect but no traffic happens.



what's wrong? as far is i read, it must be something about iptables and forwarding the ports, i'd tried a lot, but still can't figure it out. *any ideas?*

the services i used.. are right or there's something wrong with some of them? (maybe dante isn't necesary and can be replaced with a good iptables' configuration)

ps: btw, if someone knows how to configure samba to make it validate user/pwd to a share against a users table... let me know! :)

---

### Post by FrankT-Qc on 2009-05-15
squid is fine for HTTP but it should not handle everything (like torrent traffic and many other things)

What you might want to do is to allow a real connection sharing.

Since torrents use inbounds connection (i.e. a computer on the Internet is going to connect to your torrent "client") you'll need to use some port forwarding. 

The best way to do this is to use netfilter/iptables but it's a little tricky if you're not comfortable with networking. 

Firestarter (a GUI to iptables) has connection sharing features that would let you share your connection properly. 

If you want to keep your proxy configuration, make sure that firestart blocks traffic that was meant for your proxy (else, you could bypass it without noticing...) if you don't really understand, you probably didn't need a proxy !!!

have fun

---

