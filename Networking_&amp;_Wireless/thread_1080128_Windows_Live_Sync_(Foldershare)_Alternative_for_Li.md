---
title: "Windows Live Sync (Foldershare) Alternative for Linux"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by ouija on 2009-02-25
I'm looking for a Windows Live Sync alternative that works for Ubuntu Intrepid amd64 (Debian/Linux) which works in the exact same fashion as Windows Live Sync (and Foldershare would have been it if Microsoft didn't pull the same old b.s. that they do and stopped supporting linux users!!) 

I am well aware of Dropbox and have used it; However I need support for more than 2GB in my shared folders (and even paying for 50GB isn't enough!)

I want something that can support multiple clients/users/computers, that acts like a P2P connection when syncing a specified folder (meaning it would sync up files using multiple computers/connections/shared folders on the network), has no file limits or size restrictions (or at least larger caps), and works cross-platform (windows/mac/linux).

Dropbox would be perfect if it wasn't for the 2gb limit, and if it allowed for an option to not even bother using their online storage but rather acted as just a file synchronization agent.  Even if they allow you supplying your own server and removing the limits that would work.

Ifolder ([http://www.ifolder.com](http://www.ifolder.com)) could possibly be an option, but I would like to hear if anyone has ever tried using it and if it would actually perform like I require?

Powerfolder would work like a charm ([http://www.powerfolder.com](http://www.powerfolder.com)) if the Personal edition allowed more than 5 computers.  And the business is far too expensive for what I require.

Any Suggestions?

Thanks!

---

### Post by ouija on 2009-02-27
No suggestions? :(

---

### Post by ouija on 2009-02-27
SpikerOak ([https://spideroak.com](https://spideroak.com)) is another cross-platform backup and storage service that looks promising -- however it doesn't support synchronization just yet (althought the website states that it will soon)

---

### Post by www.rzr.online.fr on 2009-03-03
Just curious does WLS works on wine ?
-- 
[http://rzr.online.fr/q/wine](http://rzr.online.fr/q/wine)

---

### Post by ouija on 2009-03-03
> **www.rzr.online.fr said:**
> Just curious does WLS works on wine ?
-- 
[http://rzr.online.fr/q/wine](http://rzr.online.fr/q/wine)

I have tried on numerous occasions to use it under Wine with no success so far.. :(

---

### Post by cb951303 on 2009-03-03
ifolder works ok. and it's designed for enterprise use so it's solid.
it looks like the latest update was in 2007 though. does anyone know if the development continues?

edit: here is intreipd repo if you want [https://launchpad.net/~ruiboon/+archive/ppa](https://launchpad.net/~ruiboon/+archive/ppa)

---

### Post by ouija on 2009-03-03
> **cb951303 said:**
> ifolder works ok. and it's designed for enterprise use so it's solid.
it looks like the latest update was in 2007 though. does anyone know if the development continues?

Not sure if it is still being developed or not... So have you actually used iFolder?  Is it complicated to setup (under linux?)  Have you run it under Windows at all as well?

Thx.

---

### Post by cb951303 on 2009-03-03
> **ouija said:**
> Not sure if it is still being developed or not... So have you actually used iFolder?  Is it complicated to setup (under linux?)  Have you run it under Windows at all as well?

Thx.
The one time I tried it, it worked out of the box. But I remember that I needed to install the server too eventough I was using it in P2P mode.
So don't forget to install simias package too. I think it's in that repo too.

---

### Post by ouija on 2009-03-03
> **cb951303 said:**
> The one time I tried it, it worked out of the box. But I remember that I needed to install the server too eventough I was using it in P2P mode.
So don't forget to install simias package too. I think it's in that repo too.

Yeah, I think that's what was throwing me off.  Speaking of P2P mode, how well does it function? Meaning, does it actually grab multiple "segments" of files from each system on the network, or does it simply grab one file from here, one file from there (like the way Live Sync currently works?)

Also, is there a limit to how many machines you can have "synced"?

I have a number of systems I am looking to implement this across, and this has been a factor to why I can't find a proper alternative to Windows Live Sync...

---

### Post by www.rzr.online.fr on 2009-04-18
> **ouija said:**
> I have tried on numerous occasions to use it under Wine with no success so far.. :(

I tested too , still need some fix :


[http://www.codeweavers.com/compatibility/browse/name/?app_id=5439;forum=1;msg=49566](http://www.codeweavers.com/compatibility/browse/name/?app_id=5439;forum=1;msg=49566)

-- 
[http://rzr.online.fr/q/wine](http://rzr.online.fr/q/wine)

---

### Post by ouija on 2009-04-20
SWEET!!! SpiderOak has finally released v3.0 of their software NOW WITH SYNC CAPABILITIES!!! ([https://spideroak.com/whatsnew](https://spideroak.com/whatsnew))  I'm not sure if there is a limit like dropbox but it does say there is 2GB for storage (but that might not effect sync -- will have to check next week when I re-install Ubuntu onto my new pc; been waiting for the official release of Jaunty since converting my HP Pavillion Elite to MacOS86 this weekend) so I will post my results then.

Otherwise, great news for linux users that there is at least another option for file synchronization.. :)

---

### Post by sprajc on 2009-05-18
Hello guys,
 
 True. PowerFolder would perfectly match for your needs!
 It's a mature [peer-2-peer file synchronization tool]("http://www.powerfolder.com/wiki/Private_peer-to-peer_networking") that can [URL="http://www.powerfolder.com/wiki/Limitations"]automatically
 sync unlimited amount of data[/URL] (Not 2GB, not 5GB. it's unlimited)
 
 The best: There is a [Linux client for it (Mac as well!)]("http://www.powerfolder.com/wiki/Runs_on_Windows%2C_Mac_and_Linux").
 
 You are right about the [commercial version of the software]("http://www.powerfolder.com/download.html").
PowerFolder Pro Home version allows only to sync
up to 5 computers. But you can stack up these licenses 
 
 OR
 
 Use a older but completely [URL="http://code.google.com/p/powerfolder--/"]free open source GPL license version of
PowerFolder[/URL] (3.0.2, latest commercial is 3.1.8 ):

[**Download the free direct p2p file sync version of PowerFolder from code.google.com**.]("http://code.google.com/p/powerfolder--/downloads/list")
 
 It hope this helps!

 Best regards,
 Christian

---

### Post by ouija on 2009-06-06
Looks like Canonical has jumped on the bandwagon now and is offering a Sync/File Sharing program now, which is (unfortunately) only for Ubuntu systems (ie: Not yet for Windows or Mac) and is currently still in the beta stages and is available by invitation only.

[http://www.ubuntuone.com](http://www.ubuntuone.com)

To ask for an invitation request, follow this link (requires openid/launchpad account: [https://ubuntuone.com/invitation/1/request/](https://ubuntuone.com/invitation/1/request/)

---

### Post by ouija on 2009-06-06
> **sprajc said:**
> Hello guys,
 
 True. PowerFolder would perfectly match for your needs!
 It's a mature [peer-2-peer file synchronization tool]("http://www.powerfolder.com/wiki/Private_peer-to-peer_networking") that can [URL="http://www.powerfolder.com/wiki/Limitations"]automatically
 sync unlimited amount of data[/URL] (Not 2GB, not 5GB. it's unlimited)
 
 The best: There is a [Linux client for it (Mac as well!)]("http://www.powerfolder.com/wiki/Runs_on_Windows%2C_Mac_and_Linux").
 
 You are right about the [commercial version of the software]("http://www.powerfolder.com/download.html").
PowerFolder Pro Home version allows only to sync
up to 5 computers. But you can stack up these licenses 
 
 OR
 
 Use a older but completely [URL="http://code.google.com/p/powerfolder--/"]free open source GPL license version of
PowerFolder[/URL] (3.0.2, latest commercial is 3.1.8 ):

[**Download the free direct p2p file sync version of PowerFolder from code.google.com**.]("http://code.google.com/p/powerfolder--/downloads/list")
 
 It hope this helps!

 Best regards,
 Christian

That doesn't help at all, since the open source version does not appear to work (anymore at least) and they charge $50/year for only up to 5 computers per license... and since I'm looking to spend ZERO that pretty much sums it up :p

---

### Post by wtstommy on 2009-06-19
Try dropbox. 

[https://www.getdropbox.com/referrals/NTExMjczNzk](https://www.getdropbox.com/referrals/NTExMjczNzk)

---

### Post by dkbk on 2009-09-02
Sorry to revive this topic but isn't it possible the mac version might work ?  OS X is based on linux after all if I'm not mistaken ?

---

### Post by ouija on 2009-09-15
Not quite.  Mac OSX is UNIX based, and now with the release of Snow Leopard, Windows Live Sync no longer works (for now).

SpiderOak or SugarSync look like the best (paid) options for now.

---

### Post by solnyshok on 2009-10-12
Try Wuala. P2P java xross platform (I use it now to sync between W7x64 and Karmic-x64) and allows to have unlimited GBs of storage if you keep one of computers online most of the time.

---

### Post by sprajc on 2009-10-14
Hi again,

The [sync software PowerFolder]("http://www.powerfolder.com/new_file_sync_software.html") is available as freeware since version 4.0 release.
You can sync up to 5 GB of data without cost on up to 5 computers.

[http://www.powerfolder.com/new_file_sync_software.html](http://www.powerfolder.com/new_file_sync_software.html)

So give it a try! Regards

---

