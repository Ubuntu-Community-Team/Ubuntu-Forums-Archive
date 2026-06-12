---
title: "Visible Hostname?"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by jondavidf on 2010-06-15
How do you make an Ubuntu machine show up in Windows Network Places?  It shows up occasionally (usually if I'm changing settings), but for the most part is not there.  I have tried resolv.conf and the hosts file but still no luck.

---

### Post by mgol on 2010-06-15
I would also like to know... I reinstalled Samba in Lucid and now neither I see Windows XP shares nor it sees mine...

---

### Post by Iowan on 2010-06-15
*/etc/resolv.conf* and */etc/hosts* are more for the benefit of the Ubuntu machine. I'm still trying to learn (or remember) how Linux/Samba interact with Windows networking.

---

### Post by bigmojo74 on 2010-06-15
This might help:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Also, more of an fyi, C:\Windows\System32\Drivers\etc\hosts is where the Windows local hosts file lives.

---

### Post by jondavidf on 2010-06-16
I changed the lmhosts and the hosts file to read:

 hosts file - 192.168.1.49               # Ubuntu-Server
 lmhosts file - 192.168.1.49     Ubuntu-Server      #PRE

Still no luck getting the server to show up in network places.  Sometimes the server shows up there, but more often than not it doesn't.

---

### Post by bigmojo74 on 2010-06-16
Why do you have a # between the IP and hostname in the hosts file?

Also, from the linked doc above it looked like you also needed to enable Wins (though I admit I didn't read it all, I'm actually phasing Windows out of my network setup all together right now.) 

Of the top of my head if you're using Seven I'm not even sure they still have Wins supported... think so though.

---

### Post by jondavidf on 2010-06-17
Update:
 
I can access the Ubuntu machine either by typing the IP address into the run command or by typing the hostname into the address bar, but it still does not show up on the network.

---

