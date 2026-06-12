---
title: "Can't see Windows homegroup"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by xbobby_bobx on 2012-11-15
Okay here is my problem.. When I use the gui to access network servers it says cannot mount location.. After playing around I installed samba and the message stopped appearing, but instead it shows my local server on my Ubuntu machine... But when i go to the file browser and hit CTRL + L and enter smb://192.168.2.25 it actually shows up my network places.

Noting that I already modfied the smb.conf to accept the windows network

My Ubuntu version is 12.04 32 bit

Server: Windows XP service pack 3 (Homegroup is up and running)

can somebody help me with the problem?

---

### Post by Morbius1 on 2012-11-16
A couple of suggestions so the people here can help you better.
> Noting that I already modfied the smb.conf to accept the windows networkThat sentence alone requires that you post the output of the following command because it makes no sense:
```
testparm -s 
```
>  Server: Windows XP service pack 3 (Homegroup is up and running)
There is no "HomeGroup" in winXP so I'm not sure how it can be up and running but if you post the output of this command it might help folks determine the nature of the problem:
```
smbtree
```

---

### Post by xbobby_bobx on 2012-11-16
Alright I will do that.. But I changed the lines where it says WORKGROUP = workgroup and added the broadcast IP address.. It was working before but when I checked last night it wasn't working at all even after couple reboots.

---

