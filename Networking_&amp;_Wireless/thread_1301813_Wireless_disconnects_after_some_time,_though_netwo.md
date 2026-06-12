---
title: "Wireless disconnects after some time, though network manager thinks it's fine!"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by pulsarunlimited on 2009-10-26
Hi!

I'm using unbuntu jaunty jack on an asus laptop. My wireless internet connection is fine right up until i leave the notebook alone for a few minutes. The connection manager (tried network-manager and wicd) then show that the connection is ok, but Ktorrent has stopped downloading and i can't open any web page and such until I've  'disconnected' and reconnected using my wireless network manager.

Any ideas on what might cause this?
Could this be some energy saving thing? It does not seem to happen when i'm actively using my computer (e.g. when surfing the internets).

Hope you can help!

P.U.

---

### Post by kreggz on 2009-10-28
Try going to System/Administration/Logs after it disconnects and see if there is any error messages.

---

### Post by Scotty00Dont on 2009-10-28
Hi,

I am having the same issue with my machine running 8.10
My wireless loses connection but my Pc still says it is connected.
When it is disconnected it can ping itself and the loop back address so there is no issue with the stack. I have checked in /var/logs & /var/crash but i cant seem to find anything.
I replaced NewtworkManager with wicd hopping that would help, but it didn't.
My wireless card is a netgear WG111v3 using WEP hex.
If any one has any suggestions it would be greatly appreciated.

---

### Post by kreggz on 2009-10-28
Try pinging these in this order:

ping router
ping dns
ping google.com

---

### Post by Scotty00Dont on 2009-10-28
hi,
after the disconnect i can not ping my router, the machine can only ping itself and the loop back address.
if i restart the wicd daemon it will then connect and i can ping my dns etc.
Although i can only restart the daemon 4 or five times then i need to reboot.
After a few hours it will disconnect again.
i have re installed wicd just to make sure that it had not corrupted,
but still bo luck

Scotty

---

### Post by Scotty00Dont on 2009-10-30
I found a fix for the issue, i removed ktorrent.
I can't explain why but when i changed to deluge the issue went away.
You could try that and see if it works for you.

Scotty

---

### Post by pulsarunlimited on 2009-11-01
[Scotty00Dont]("http://ubuntuforums.org/member.php?u=933736"), now that you mention it, I dont' really really remember having the problem when I wasn't using k-torrent.

Will definitely try this, and will let you guys know how it works out.
(sorry for the slow reply by the way)

[kreggz]("http://ubuntuforums.org/member.php?u=546503"), I will also see if there's any error in the log when i do use ktorrent.

PU

---

### Post by pulsarunlimited on 2009-11-01
I've tried Deluge. Still the same problem. When i'm surfing and downloading torrents, it's fine. When i'm downloading and not using the computer, i come back after a while and downloading has stopped and i can't visit any webpage without first disconnecting and reconnecting my wireless connection.

kreggz, i've taken a look at the logs, but i don't immediately see anything significant under 'messages'. But there are loads of other logs. At which do i look?

---

### Post by bekirserifoglu on 2009-11-03
I use deluge and transmission and I have the same problem. my wireless connection gets lost after starting to download something. I think this is a bug with the network manager because I don't have any problems with wicd.

---

### Post by kevdog on 2009-11-03
This happened to me all this time (frequent disconnects).  I reinstalled new firmware on the router and problem was solved.  That was a life saver!!!  What tipped me off was that my laptop would only disconnect frequently at home and no where else.

---

### Post by pulsarunlimited on 2009-11-03
[bekirserifoglu]("http://ubuntuforums.org/member.php?u=268206"), I already switched to wicd, didn't help :-(

[kevdog]("http://ubuntuforums.org/member.php?u=257393"), did your disconnects also occur during active surfing on the web? (not with me) did it look as though you were still connected (by looking at network manager/wicd)
I guess I'll have to try at someone else's place to see if it could be the router/switch. Don't know yet when i'll have the opportunity to do so.

---

### Post by jasu00 on 2010-04-08
I tried this and it worked for me:
 sudo iwconfig wlan0 power off


My power mangement option is "on" by default. so when I used to keep the wireless network idle for around 2~5 min, network used to disconnect and then only connect after reboot...

but i have to run the above command every time I restart....i put it in script and run it on startup...

---

