---
title: "mount windows share: &quot;Cannot allocate memory&quot;"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by cparham on 2010-03-26
Hello Ubuntu users,

I'm trying to connect to a Windows XP share from my Ubuntu 9.10 server. I thought this would be rather simple - maybe you can show me it is??

On the Windows XP side, I have created a local user "ubuntu" and given the user Full Control of the share. (btw: the XP machine is a member of a domain)

This is how I'm connecting from Ubuntu:
sudo mount -t cifs //192.168.2.153/websrv01_logs /media/bio171_websrv01_logs -v -o username=ubuntu

and this is the error I get back:
mount.cifs kernel mount options: unc=//192.168.2.153\websrv01_logs,ver=1,rw,username=ubuntu,ip=192.168.2.153,pass=********
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I see this when running dmesg:
CIFS VFS: cifs_read_super: get root inode failed

Help, please!

---

### Post by cparham on 2010-03-26
It's funny how things go, but within hours of posting this question, I stumbled upon the solution. And believe me, I spent a lot of time trying to find answers before posting...

The solution: right click the shared folder on Windows and open the Properties dialog. The two tabs of interest are Sharing and Security. I had to grant the local user access on BOTH tabs. Initially, I had only done this on the Sharing tab. It's unfortunate the error message - "cannot allocate memory" - was not more helpful.

Hope this helps someone...

---

### Post by amidsin on 2010-11-13
Thank you, it worked perfectly.

---

### Post by allanfigueiredo on 2011-06-07
Thank you [cparham]("http://ubuntuforums.org/member.php?u=1043200")! You save a lot of my time.

---

