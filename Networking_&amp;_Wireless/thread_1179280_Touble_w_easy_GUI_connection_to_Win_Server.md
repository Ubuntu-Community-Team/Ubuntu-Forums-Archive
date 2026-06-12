---
title: "Touble w/ easy GUI connection to Win Server"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by ktritty on 2009-06-05
I'm gradually assimilating Ubuntu into our workplace after a fairly easy process of convincing my boss that it is the way to move forward.  Our employees are used to windows XP.  They are used to using a desktop shortcut to get at our office documents.

I am trying to set up something similar on our Ubuntu workstation (9.04 Desktop).  My server is a Windows Business 2003.  I also have a MacBook that I use for most of the admin (via ssh, web utils, etc).  I find it interesting that my MacBook automatically sees the Windows server, and with the click of a mouse, I get exactly what I want.

But, I am having a horrible time getting into the Windows Server from the Ubuntu computer via anything other than ssh.  I am still new to Ubuntu, I have tried a few things with Samba, but no avail (I don't think the Win box is setup as a samba server).  I have tried using the 'places' tab and going into 'network' which works great for getting into my MacBook, but when I click on the windows server icon, it says 'unable to mount location, failed to retrieve share list from server.'  I am wondering what I am missing, and what is likely the easiest course to get my magical "Network Place" shortcut as my employees are used to.

Remember that my MacBook does it fine, so I think there isn't anything to change on the Win Box.

Many thanks!

---

### Post by MonsterDuc on 2009-06-06
Hi, I am still in the early stage of getting used to Ubuntu but saw you didn't have any replies so figured I'd give you my best shot :)

I have, at home, a windows vista and a ubuntu desktop.  I have setup a "shortcut" to a share on the vista by using Places->Connect to Server.  Change connction type to Windows Share, then fill out the credentials.  I then added a bookmark for the connection that I can access through Places->Bookmarks. 

May not be what you are looking for in a work environment but it works for me.

Cheers!

---

