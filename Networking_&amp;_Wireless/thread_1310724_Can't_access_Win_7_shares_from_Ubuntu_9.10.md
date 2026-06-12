---
title: "Can't access Win 7 shares from Ubuntu 9.10"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by agro666 on 2009-11-02
I just installed Ubuntu Desktop 9.10 tonight.  Using smbclient I can access Windows XP shares, but I cannot access Windows 7 shares.  I read other posts on forums and a lot of people had problems trying to access Ubuntu (samba) shares from Windows 7, but I am going the other way around.  The issue seems related to Windows 7, not Ubuntu.  

No firewalls present.  All systems on the same network.  Am able to go from Windows XP to Windows 7 fine and Windows 7 to Windows XP fine.  It is only going from Ubuntu to Windows 7 where I receive this "session setup failed: SUCCESS - 0" error.  The shares I have on the Windows boxes below DO exist.  They are confirmed from Windows to Windows.  I know they are shared, and I know that the usernames I am specifying have Full Control over those shares anyhow.

_TRYING TO ACCESS WINDOWS 7 PRO_
username@servername:~$ smbclient //192.168.1.101/Archived_Videos -W WORKGROUP -U xbmc_username
Enter xbmc_username's password: 
session request to 192.168.1.101 failed (Called name not present)
session setup failed: SUCCESS - 0
username@servername:~$ 

_SUCCESSFUL ACCESSING WINDOWS XP PRO_
username@servername:~$ smbclient //192.168.1.102/c$ -W DOMAIN -U windows_user
Enter windows_user's password: 
session request to 192.168.1.102 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[DOMAIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

---

### Post by wootah on 2009-11-07
Well, I'm hoping someone gives you a reply because I am having the exact same problem.

---

### Post by JBAlaska on 2009-11-07
I know this is not a "Fix" but you could setup a FTP server on win 7 and access files that way..but you probably want to stream video so.. Can you axx your win 7 box outside XBMC?

---

### Post by JamesUser on 2009-11-07
Are you able to ping the windows machine from ubuntu?

---

### Post by agro666 on 2009-11-08
> **wootah said:**
> Well, I'm hoping someone gives you a reply because I am having the exact same problem.

Nobody ever gave me a resolution on any forum.  I did however finally plug in the correct thing on Google and got the resolution from another members post.

Remove Windows Live Assistant.  Right after you do this, no reboot needed, just simply try smbclient again and whammo you get in fine.

---

### Post by HostileJava on 2009-11-10
I'll have to try this when I get home, this has been bothering me for days.

Edit:  This worked great!  Thanks!

---

### Post by arryo on 2009-11-11
I don't have windows Live Assistnat installed but still can't get to my win 7 shares. The result from smbclient -L mywindows7: Error returning browse list: NT_STATUS_NOT_SUPPORTED

---

### Post by Iowan on 2009-11-11
[This ]("http://ubuntuforums.org/showthread.php?t=1169149")How-To covers Vista shares, but dunno if Win7 is different...

---

### Post by wootah on 2009-11-12
So this is a crappy situation, but at least I got this to work AND I managed to get better speeds.

Turns out something broke with 9.10 (some change in a newer version of Samba causing the problem)

I wasn't able to fix it but instead I mounted my partitions using CIFS. Do a quick search on CIFS and you'll see some options for how to mount.

If someone else can explain what happened that would be extremely useful.

PS: There was a notice about this problem in the release information for Ubuntu 9.10. I guess I should have read it more carefully lol :(

---

### Post by KwaggarookDagga on 2009-11-20
Hi
I am having the same problem. I can "see" the ubuntu shares from the win7 machine, but can't access the win7 shares from the Ubuntu machine.
I have changed the workgroup to be the same on both. Ubuntu says Can't mount the share ????
I would really like a solution to this because I want Ubuntu to work for me this time.
Thanks in advance

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
Same problem here but with XP shares. Still diligently searching for a fix or workaround. Insofar just a lot of hair pulling and teeth grinding.

---

### Post by Iowan on 2009-11-20
Sin@Sin-Sacrifice:
Check the link I posted in #8.

---

### Post by Sin@Sin-Sacrifice on 2009-11-26
> **Iowan said:**
> Sin@Sin-Sacrifice:
Check the link I posted in #8.

I went through that... still not working. I can't get them in android either though so I know it's a configuration in windows that I'm screwing up.

---

### Post by keenox on 2009-12-08
i'm absolutely sure this is an ubuntu problem. i used 9.04 without any problems along with xp and vista and i didn't have to install samba. now it asks me for the password and even if i give it the right password it does nothing. it's weird though, because i have absolutely no problem accessing ubuntu shares from windows.

---

### Post by BLTicklemonster on 2011-05-05
Turn off the firewall on the offensive (that'd be windows 7) machine. How funny, that for all their efforts to secure their software, you have to hike it's skirt for it to work. Go Microsoft! keep going... keep going, a little further, a little further...

---

