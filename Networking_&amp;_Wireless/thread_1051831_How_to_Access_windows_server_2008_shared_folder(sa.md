---
title: "How to Access windows server 2008 shared folder(samba is installed) from Ubuntu"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by pincustomer on 2009-01-27
Hello Friends,

I would like to access windows 2008 shared folder from ubuntu.

I try to connect using :

places -> connect to server

smb://servername/foldername

but it ask for server username/password so many times........

how to solve this problem.

Please help .

thanks in advance.
Pin

---

### Post by normanp on 2009-01-27
Have you installed Samba? Check in Synaptic Package Manager. If not and you don't have an Internet connection, go to Settings, Repositories in the Package Manager, uncheck all the Internet repositories and check the top one of the CDRom entries. Insert the install CD. When a browser window appears close it. In Package Manager, Refresh, select samba, install. Browse with Places, Network - hope this works!

---

### Post by pincustomer on 2009-01-27
Thanks for your reply,

I have already installed samba on Windows Server 2008.

When i try to connect server, it ask about username/password contineously...

---

### Post by scheuri on 2009-01-27
I am sorry

Please verify:
[LIST]
[*]You have a Windows Server 2008 which has shares definded which shall be accessed by a linux client. Is this correct?
[*]You have installed samba (especially the samba-client) on the linux client which shall use the shares on the windows server. Is this correct?
[*]What version of Ubuntu are you running?
[*]What version of Samba are you running?
[/LIST]
Cheers
Stefan

---

### Post by Another Monkey on 2009-01-27
Are you able to browse to the share on the network, or do you need to go to the share directly?  If you cannot browse to the share, it may be your iptables configuration blocking full networking functionality.  I had that problem with Samba.

If you create a share on the Ubuntu machine, can you browse and access that OK over the network?  If not, it might point to a fault in your Samba/firewall set-up.

It is [explained here]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access").

I found that opening the iptables config GUI ("Firestarter") and adding an inbound policy for the local network (e.g. "192.161.1.0/255") and removing the check beside "Block broadcast from external network" in "Advanced Options" cured it for me.

Note: I do not know if unblocking the broadcasts is safe, I am trying to find out.

I am pretty new at Linux, so please excuse me if this is of no help to you.  Seems like other are giving good advice.

---

### Post by pincustomer on 2009-01-27
> **scheuri said:**
> I am sorry

Please verify:
[LIST]
[*]You have a Windows Server 2008 which has shares definded which shall be accessed by a linux client. Is this correct?
[*]You have installed samba (especially the samba-client) on the linux client which shall use the shares on the windows server. Is this correct?
[*]What version of Ubuntu are you running?
[*]What version of Samba are you running?
[/LIST]
Cheers
Stefan
Thanks scheuri,

absolutely correct that i have server 2008 & install samba client on Ubuntu.
 
One thing i would like to ask that i need to install all samba product on ubuntu or just samba client.

Pin

---

### Post by pincustomer on 2009-01-27
> **Another Monkey said:**
> Are you able to browse to the share on the network, or do you need to go to the share directly?  If you cannot browse to the share, it may be your iptables configuration blocking full networking functionality.  I had that problem with Samba.

If you create a share on the Ubuntu machine, can you browse and access that OK over the network?  If not, it might point to a fault in your Samba/firewall set-up.

It is [explained here]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access").

I found that opening the iptables config GUI ("Firestarter") and adding an inbound policy for the local network (e.g. "192.161.1.0/255") and removing the check beside "Block broadcast from external network" in "Advanced Options" cured it for me.

Note: I do not know if unblocking the broadcasts is safe, I am trying to find out.

I am pretty new at Linux, so please excuse me if this is of no help to you.  Seems like other are giving good advice.
Thanks another,

i am getting ping from both PC and can also surf the web from ubuntu but just sharing problem is there.

Pin

---

### Post by Another Monkey on 2009-01-27
> **pincustomer said:**
> i am getting ping from both PC and can also surf the web from ubuntu but just sharing problem is there.
That really sounds like a firewall blocking the SMB related ports.

Check out that URL and make sure your Windows firewall is allowing File and Printer Sharing.

---

### Post by pincustomer on 2009-01-27
I have checked firewall, firewall is not blocking anything.

I can access server from the other windows client also.

so there may be problem with samba server.

may i directly access without using samba server.

if any thing plz help me.

---

### Post by Another Monkey on 2009-01-27
> **pincustomer said:**
> I have checked firewall, firewall is not blocking anything.
Which firewall?  There are at least two.  Open "Firestarter" and leave it running for about 7 minutes, then check "Events" (or just try "Reload" in the "Events" tab immediately).  If you see something like "192.168.0.2, port 32763 UDP blocked" then you know that the broadcasts from Windows are being blocked.  That thread I linked to explains why and how to resolve it.  Have you read this?  (The message will appear about 5 times and the IP address will be that of your Windows sever.  The port may not be the same).

> **pincustomer said:**
> I can access server from the other windows client also.
You mean you can access with Windows server from another Windows client?  Good - that means your Windows networking is working.

> **pincustomer said:**
> so there may be problem with samba server.
Can you browser to the Ubuntu PC via Windows Explorer?  Can you see its shares via Windows Explorer?  Try this by expanding the tree, not just going to \\ubuntu\some-share

Can the Ubuntu PC browse the network and see the Windows PCs?  If not, then it is your Ubuntu firewall blocking the broadcasts (that was one problem I had).

From the Windows command line, does "net view" show your Ubuntu PC?  How about "net view \\ubuntu-pc-name"?  Does that work?  Or did you get an error 53?  If you got error 53, check the Ubuntu firewall.  If you got a different error, look that up as it may help.

> **pincustomer said:**
> may i directly access without using samba server.
In order to share folder from Ubuntu, you need Samba server.  If you just want to use folders shared on Windows then you just need smbclient.

It took me a long time to get networking going (most of big problems were caused by damaged Windows networking) and that thread I linked to really helped me sort out Ubuntu in about 5 minutes.  You need to read it a few times, but it does become clear.

HTH

---

### Post by pincustomer on 2009-01-28
Thank you very much for your kind reply.

you are absolutely right.

I am getting error 53 from windows client.

so now i am checking about ubuntu firewall.

---

