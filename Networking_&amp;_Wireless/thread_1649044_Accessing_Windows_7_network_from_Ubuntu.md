---
title: "Accessing Windows 7 network from Ubuntu"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by testament0221 on 2010-12-19
Okay, just installed Ubuntu 10.10 on my Mom's netbook, and everything is working great. However, I'm having issues accessing our Windows 7 network from the Ubuntu machine. 

When I go to Network, I can see our Windows 7 PC's...but when I try to access them, it asks for a Username/Password, and I have no idea what to put in there. I've tried using the Home Group password thing, along with just giving my Windows 7 account a password and trying that...but nothing works. The same happens when I try to connect Ubuntu to our Windows 7 printer; asks for a UN/PW. 

So what am I doing wrong?

---

### Post by spiky001 on 2010-12-19
On the windows machine is network sharing set up

---

### Post by testament0221 on 2010-12-19
Yes, I have networking set up for my Windows 7 machines

---

### Post by spiky001 on 2010-12-19
I found this ```
Commontater:  You nailed it.  In advanced settings I had  "Use account  names and Passwords to access other computers"  checked as yes.  Not  sure how it got that way.  But unchecked it everything works now the way  I want it.  Just an FYI, I stopped using homegroups a while back  because I suspected it was  waking up on of my computers from sleep.   Thanks again for your help and thanks to everyone else that replied!
```It was here [http://www.sevenforums.com/network-sharing/77733-windows-7-asking-user-name-password.html](http://www.sevenforums.com/network-sharing/77733-windows-7-asking-user-name-password.html)  see if it helps

---

### Post by spiky001 on 2010-12-19
[http://www.howtogeek.com/howto/windows-7/share-files-and-printers-between-windows-7-and-xp/](http://www.howtogeek.com/howto/windows-7/share-files-and-printers-between-windows-7-and-xp/)

---

