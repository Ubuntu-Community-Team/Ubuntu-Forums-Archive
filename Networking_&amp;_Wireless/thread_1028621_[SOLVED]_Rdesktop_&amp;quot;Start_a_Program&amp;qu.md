---
title: "[SOLVED] Rdesktop &amp;quot;Start a Program&amp;quot; problem W2K8"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by weigh2tall on 2009-01-02
I've tried searching for a solution to this but haven't found anything relating to the specific issue I'm facing.

I can RDP fine into a Windows 2K8 box and a W2k3 SBS box.  I'd like to have the login automatically launch a program installed on the computer.  As a test I'm using notepad.

If I run these commands pointed at the 2k3 box they work well enough.  If I point it at the 2k8 box it doesn't work.  I get logged in but the desired app never launches.  Below are the commands.  Has anyone else seen this and found a way around it?  I'm not sure if this would behave the same way in Vista.  

On the Windows 2003 SBS box
```
rdesktop -s "C:\windows\notepad.exe" ComputerName -d DomainName -u UserName

```
For the Windows 2008 box (had to modify path as notepad's not in the same place
```
 rdesktop -s "C:\windows\system32\notepad.exe" ComputerName:PortNum -d DomainName -u UserName

```

I am able to get the desired results from a Windows box and a OS X Leopard RDP client

---

### Post by DocForbin on 2009-01-02
Just a shot in the dark, but are you logging in as administrator? If not, have you tried that?

---

### Post by DocForbin on 2009-01-02
interesting, have a look here:

[http://blogs.msdn.com/ts/archive/2007/12/17/changes-to-remote-administration-in-windows-server-2008.aspx](http://blogs.msdn.com/ts/archive/2007/12/17/changes-to-remote-administration-in-windows-server-2008.aspx)

search for "Start program on connection" does not work."

---

### Post by weigh2tall on 2009-01-02
I've tried logging in as several users, all of them have admin rights on the box.  I haven't tried the local administrator account, but those I've used are members of the group which has local administrator rights.  

I read most of the linked article.  It seems that the one person wasn't getting where they wanted because they didn't have RemoteApp manager running.  I do have it enabled, and the clients which connect from other OS's work, however they were both made by MS.  

Thanks for the response.  Any other thoughts?

---

### Post by weigh2tall on 2009-01-06
I'm a moron the problem turned out to be that I was pointing the command at the wrong server.  Apparently Windows Server 2008 requires that the RemoteApp manager roll be defined to enable the "Start a Program" feature.  From what I can tell this doesn't seem to be the case with 2k3 (I could test 2K3 SBS, and 2k3 storage server)

Thanks for the help though...

---

