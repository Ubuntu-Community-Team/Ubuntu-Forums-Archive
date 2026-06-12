---
title: "Send Ubuntu Print Job to Windows Printer"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2009-12-24
Okay, this is what I have so far:

Toshiba Notebook running either Ubuntu 9.04 or 9.10, connected by ethernet to router shared by three Desktop PCs.  Two desktops set up to boot to either Ubuntu (even OpenSUSE in one case) or Windows 2000 Pro or XP.  The third is just Windows 2000 Pro  Haven't been able to get the RTL8187B wireless adapter in the notebook to fly yet, but that should come later.  

The desktops in Windows can see each other as part of the same workgroup.  I can connect to some part of the shared portion of any from the notebook by using a userid and password on the targeted desktop.  Simple enough, just use Places/Network, or Places/Computer/Go/Network.  You can see the desktops, but they don't see you (check My Network Places/Computers Near Me or under my Network Places/Microsoft Windows Network and your specified Domain or Workgroup if you want to be sure)

I also have the option with Ubuntu to go another route, to use Places/Connect to Server, then I can specify more about the manner of connecting and provide a userid and password.  Again, this must be a userid and password to the targeted desktop. Trouble is though, I keep getting errors that the notebook could not connect to the server when I try this, but I don't yet know why.

What I've learned to date is that Windows has its own special way of networking, something shortened to SMB.  This is not how Linux does it, but efforts have been made to write Linux code to bridge this so that Linux can work with SMB.  There are two sides to this.  If you want to set up a server to handle SMB, and that server is running Linux or other non-Windows OS, you need to get a version of Samba and install it on that computer so that Windows-based PCs, called clients can come to you either to access your files of to send you print jobs.  But Samba is not what I need here, because I want the Windows PCs to do the printing for the Notebook.  And you don't need Samba on Windows, because it already uses SMB.

Okay then, what do I need for my notebook instead?  Seems like what I need is smbfs and smbclient, and this is what is suppose to make it possible for Ubuntu to access the Windows files and also send print jobs to the Desktop.  So I've installed these now using the Synaptic Package Manager, which you find under System/Administration.  With me so far?  There is also mention of cifs that might be used in place of smbfs, but not much detail found on that yet.

Actually, there's not much detail anywhere.  You might get asked for a userid and password, but it's not clear whether that is suppose to be for the client PC or the targeted PC which is acting like a server.  Then in another place they want you to replace $SERVER with the name of the machine that you are trying to get to, but you try it different ways, and somehow it is always wrong.  All you get told is that you must use // or \\ in place of single slashes.

They also want some additions made to /etc/fstab, where you specify the network address and give a mount point, the either a type of smbfs or cifs, and then details about the options to use.  Only again, the exact form of the network address is not made clear, and though it suggest you can just use the IP address if you have it, this is not accepted either.

It's confusing, and unfortunately, nothing tried so far has really worked.  I did get to use smbclient once to see what my desktop PC has set up for sharing, including reference to the printer, but that is about it.  I guess I just have to remember to use -L after smbclient, then the network name, following that with -U%, to get the list again.

Oh, I did find several references to using GhostScript, GSView, and RedMon on the Windows server side to create a virtual PostScript printer attached to the Desktop, which the Ubuntu output could be directed to, which would then in turn convert it to form my actual printer should be able to handle.
But if I carry then notebook about with me to other places, then chance to want to send an output to an available printer there, I don't want to have to make changes to their Windows OS to make this feasible.  The changes should be just on my end.

Anyway, I hope to hear from some that have gone this route and can now relate just how they got there.  It would make life a whole lot easier, and probably not just for me.  Meanwile, if can can come up with anything to help, I will try to add to this thread as well.

---

