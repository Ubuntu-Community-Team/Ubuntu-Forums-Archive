---
title: "(Yet another) Cannot connect to Windows share from 12.04 LTS"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by jbhtexas on 2013-01-08
Hello!

Up until about a week ago, I was able to do the following in order to connect to a Windows XP SP3 share from my 12.04 LTS client:

1) Select Home Folder from the Launcher
2) Select File > Connect to Server...
3) Select Type: Windows Share, and fill in relevant information (Server, Share, Domain, User Name, Password)
4) Share was connected with no problems.

For some reason, that has stopped working. Now, I keep getting "Please verify your user details", with a red exclamation point in the password box whenever I try this procedure.  I installed some software and did updates on the Ubuntu client.  Nothing has changed that I know of on the Windows share computer.

The command:
```
sudo mount -t cifs //192.168.0.1/net1 /mnt/net1 -o username=myusername,password=mypassword,iocharset=utf8,file_mode=0777,dir_mode=07*&#8203;77

```
works fine, and other clients can still connect to the Windows share, including android clients through Astro File manager and XP clients, without any difficulty.

I've read through quite a few threads about this issue, including making changes to smb.conf for 
```
client lanman auth = yes/no
client ntlmv2 auth = yes/no
ntlm auth = yes/no
workgroup = WGNAME

```
but nothing helps.  The consensus seems to be to give up and use mount -t cifs.

Also, "Browse Network" no longer works either; it used to.  I can open the Windows Network folder and then the HOME folder (my workgroup is named HOME), but when clicking on the HOME folder, after a time, the response is "Unable to mount location; Failed to retrieve share list from server"

I'm just checking to see if there may be any new solutions, or new troubleshooting for this issue.  mount -t cifs works, but the GUI method is also very handy, and troubling that it all of a sudden failed.

Thanks!

---

### Post by smo0th on 2013-01-08
did you tried these?:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
[http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html](http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html)

---

### Post by jbhtexas on 2013-01-08
> **smo0th said:**
> did you tried these?:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
[http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html](http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html)

Yes.  The first link addresses the mount command, which works fine for me.

The second link, although it addresses the GUI method of accessing shares, doesn't provide any insight into why the GUI method refuses to accept a valid password.

---

### Post by smo0th on 2013-01-08
maybe it's just the order of the parameters? have you tried this format?

mount -t cifs -o username=USERNAME,password=PASSWD //192.168.1.88/shares /mnt/share

---

### Post by smo0th on 2013-01-08
I noticed you have an * in your line:
sudo mount -t cifs //192.168.0.1/net1 /mnt/net1 -o username=myusername,password=mypassword,iocharset=utf8,file_mode=0777,dir_mode=07*&#8203;77

it may be tampering the command

---

### Post by jbhtexas on 2013-01-08
> **smo0th said:**
> maybe it's just the order of the parameters? have you tried this format?

mount -t cifs -o username=USERNAME,password=PASSWD //192.168.1.88/shares /mnt/share

I think you have misread my original post.  As I stated, I don't have any problem with the mount command.  It works fine.  

The problem is when trying to connect from the GUI interface provided by the "Home Folder" application.

Thanks!

---

