---
title: "Problem accessing Ubuntu shared files from Windows XP"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by stephenconnolly on 2010-12-13
Hello,

I've recently installed ubuntu on an old desktop pc. I want to use this as a home server. I've installed samba. I have two laptops, one is a vista machine and the other is an XP machine. The Vista machine works fine, I can access all the shared folders on the ubuntu server. But I can't access anything from the XP machine. I get the following error in the attachment. 

From the RUN window, I type \\xxx.xxx.x.xx and it opens up a Samba Ubuntu window with a Printers and Faxes folder.

Any help would be much appreciated. I've been googling this for awhile but have been unable to resolve the issue.

Regards,
Stephen

---

### Post by stephenconnolly on 2010-12-22
*Bump*

---

### Post by CharlesA on 2010-12-22
Do you have any folders shared?

Are you able to connect using the ip address from the Win XP box?

---

### Post by stephenconnolly on 2011-01-04
Yes, I have multiple folders shared and I can access these on the Vista machine. 

I have no problem logging in directly with the IP address on the XP machine using Putty.

---

### Post by CharlesA on 2011-01-04
Try adding the hostname of the Ubuntu box to the hosts file at %windir%\system32\drivers\etc\hosts of the Windows machine.

---

### Post by stephenconnolly on 2011-01-04
I've just tried that. When I try to map a network drive to a shared folder sometimes it can't find the folder, error message: "The network path \\ubuntu\all music could not be found" and other times it asks for a username and password.

I tried my server log on details but no luck.

Any thoughts ?

---

### Post by CharlesA on 2011-01-04
It kinda sounds like a communications problem. Is there a firewall running on the Ubuntu box?

---

### Post by stephenconnolly on 2011-01-05
No firewall installed.

---

### Post by CharlesA on 2011-01-05
Is nmbd and smbd running?

```
service smbd status
```
```
service nmbd status
```

---

### Post by stephenconnolly on 2011-01-06
just tried both commands and got the following responses:

smbd start/running, process 590

nmbd start/running, process 1186

I fairly new to ubuntu, so this doesn't mean much to me.

---

### Post by CharlesA on 2011-01-06
Looks like they are both running, so they shouldn't be a problem.

---

### Post by drdos2006 on 2011-01-06
Is your shared folder formatted as NTFS or is it linux ext3 or ext4. If your shared folder is NTFS, it cannot be read by MS Operating system because Windows does not recognise linux format.

regards
[edit]
ignore my comments, it has been a long time since I have used Windows.
I just did a test from a Windows 7 virtualbox and a second machine useing desktop 10.4 with shared folder, formatted to ext3. I shared allowing guest access.

You may be having a permissions problem instead.
[/edit]

---

### Post by stephenconnolly on 2011-01-08
Problem solved, I was connecting to the server under the laptop user name. 

When I used the correct username and password, everything worked fine.

Thanks all for the help.

Regards,
Stephen

---

