---
title: "Can't access Ubuntu server (Samba share) from Windows 7 machine"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by GaryReggae on 2012-12-05
I'm not sure whether this is a Windows problem or a Ubuntu one but I'll start here, as all the settings from the Windows perspective appear to be what they should be.

I have a server running Ubuntu (12.04 LTS to be precise). I have several shares of various folders set up - the usual stuff of one for music, one for photos etc. I can access these fine from my Windows XP machine - either by typing the \\servername or by mapping them as network drives. 

The laptop I recently got has Windows 7 on it (ugh!). I can't access my shared folders at all from that. Browsing for network devices doesn't show them and typing in the \\servername doesn't either. It's definitely connected as I can ping the server's IP address from a command line on the Win 7 machine and get a reply.

Is there anything I need to do from the server perspective to make it appear to Win 7 or is there something that needs doing on the offending Windows machine itself? I have added it to the same workgroup as the XP machine, which I assume the server is also on (sorry, I don't understand how workgroups work with Linux). I have enabled network discovery and gone into the TCP/IP properties and checked 'Enable NetBIOS' as I read somewhere that Samba was something to do with that.

Any suggestions you have to solve this, or to point me in the right direction are much appreciated!

---

### Post by TheFu on 2012-12-05
Be certain that your smb.conf file specifies the same workgroup as both the Win7 and WinXP use.  

Win7 changed some authentication things - making them more secure. I can't recall exactly whether samba was impacted or not, sorry.
Did you follow the samba how-to guide from the Ubuntu help website?

Hopefully someone else will post a better answer.

---

