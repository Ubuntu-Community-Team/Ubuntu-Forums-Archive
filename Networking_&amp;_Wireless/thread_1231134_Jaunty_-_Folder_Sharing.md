---
title: "Jaunty - Folder Sharing"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by lyghtkruz on 2009-08-04
Greetings Fellow Linux Users, 

I setup 'folder sharing' via the add/remove applications. I'm using Jaunty 64 bit with all the latest patches as of 08-04-2009.  

All of my shared directories are visible/writable from Windows via Start->Run \\Calypso (my computer name)

I had to manually enter my computer's static IP address in the /etc/hosts file of any Jaunty box but it was accessible via the Network->Workgroup.

I shared the directories by Right Click->Sharing in Nautilus. (No other configuration on my server was required)

About a week ago it just "stopped" working.  The Ubuntu clients and are no longer accessible via the Network browsing.  I have tried to go to Network->Workgroup and I get a 'Failed to retrieve share list from server.'   Running /usr/bin/smbtree returns: 

	\\CALYPSO        		Calypso server (Samba, Ubuntu)
		\\CALYPSO\movies
		\\CALYPSO\pictures
		\\CALYPSO\music

(The Windows boxes can still read and write to all of my directories.)
After looking through some posts, I saw people mentioning smb.conf so I manually added a share in /etc/samba/smb.conf.  No change.  Windows is able to see the directories shared via the smb.conf and Nautilus, but Ubuntu returns an error.  (Jaunty 32 bit and 64 bit clients are unable to view the files.)

Can anyone shed any light on this?  If Samba wasn't working or setup properly, Windows wouldn't be able to access the folders.  I'm assuming it was an update in Ubuntu, but I can't think of whut would have changed on the client to prevent it from accessing my directories. 

Thanks in advance for those of you that try to assist. (: 
-Kruz

---

### Post by superprash2003 on 2009-08-04
have you tried accessing via  ip..like smb://x.x.x.x

for reference: [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by lyghtkruz on 2009-08-04
> **superprash2003 said:**
> have you tried accessing via  ip..like smb://x.x.x.x

for reference: [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

No, I had not.  For when I tried to access the system via the "Connect to server"  It prompted with "Cannot display location smb://calypso/"

I manually opened the URL via Nautilus smb://calypso/ and voila.. it opens (on both Ubuntu machines).  It still doesn't explain whut caused the Network browsing to break, but as long as it's accessible, I don't care too much. 

(:  Thanks a lot.

---

