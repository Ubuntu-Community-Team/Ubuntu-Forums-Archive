---
title: "How does SMB work?"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Unkraut on 2009-09-22
Hi!
I'm really confused about SMB. I want to share some folders on the local network and make them visible and browsable for everyone there.
If I do that via Nautilus (right click on folder -> share options (or whatever that is in English) -> share this folder + allow guest access) I can access the shared folders by typing smb://my computer's name in Nautilus. But I can't find my computer in smb:///.
I then edited the smb.conf and changed my work group's name from the generic "workgroup" to "perkele" and restarted samba to see if I'd find that group in smb:/// but no, I didn't.
Then I further edited smb.conf and added a share there (but the shares I created through Nautilus are not listed in smb.conf) and restarted samba. After that I found the group "perkele" listed in smb:/// but when I try to access it, it says "failed to retrieve share list from server".

So, I am very confused now. Why in hell are there two different ways to create a samba share and why does everything behave so strange?
- When I create shares via Nautilus they are not written to smb.conf. So there must be another configuration file somewhere. I can't find my workgroup or computer's name in smb:/// by this method but I can find the shares in smb://my computer's name/.
- When I then add a share in smb.conf I can see my workgroup in smb:/// but I can't open it. I can still access smb://my computer's name/ but it's empty. However, if I then type smb://my computer's name/some shared folder's name/ I can open it if the share is in smb.conf. The Nautilus created shares on the other hand cannot be accessed anymore.

Why is the Samba file sharing so ****** up and inconsistent? I remember that it did work somehow without problems one year ago or so.

What I want is to make my shares visible and accessible for everyone on the network. Any solution?

Regards
Unkraut

edit: I'm using Ubuntu 8.10

---

### Post by Iowan on 2009-09-22
A couple of How-To's that might help... maybe you've already seen them.
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

