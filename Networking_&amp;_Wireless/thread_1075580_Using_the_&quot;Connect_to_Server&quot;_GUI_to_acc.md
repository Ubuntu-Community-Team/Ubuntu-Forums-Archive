---
title: "Using the &quot;Connect to Server&quot; GUI to access Windows shares"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by weedwacker on 2009-02-20
Hi, All:

I posted this in the Beginners Forum already, but I thought I could post here in Networking and hope for the best.

The situation:

I just want to learn how to do this. I am using Ubuntu Ibex.

I have Samba installed and can access my Windows shares using the **Places>Network** access just fine. I am accessing from both machines networked through my Linksys router on my home network.
My machine is Ubuntu and the other is Windows XP.

But I want to learn how to access my windows shares using the **Places>Connect To Server** GUI which is just below the **Places>Network** link.

The question is, will this let me ***Samba*** into my Windows share?

I've tried to connect to my Windows share in the **Connect To Server** GUI by clicking on **Windows share** type of connection but I am having difficulty with the information to enter into the **Server** box.

I've tried the IP address of the machine I want to access, I've tried using **mshome** alone and in conjunction with the IP address, and also with the name of the computer I want to access: salsnotebook. I have tried finding this information on the net to no avail.

This is the message that pops up often:

    Cannot display location "smb://mshome/salsnotebook/documents"

    failed to mount windows share

Could someone help? What goes into the box labeled "Server"?

---

### Post by Iowan on 2009-02-21
That's curious... My older (Breezy) machine works the other way around - it has problems via Places>Network, but works fine with Places>Connect_to_Server.  You might try putting smb://ip-address-of-server/sharename (but I doubt that is really a solution.)

---

### Post by damis648 on 2009-02-21
Well the protocol SMB shares uses doesn't use IP's, that's a different protocol so don't bother with that. Here's what you need to put in exactly:

Server: The computer name (salsnotebook)
Share: What share (either put Documents or leave blank)
Folder: (leave blank)
User Name: username
Domain Name: workgroup (mshome)

also, do not forget that this is all case-sensitive.

---

### Post by weedwacker on 2009-02-25
Hi,

Thanks for the reply.

Question: In the **User Name** entry under Optional Information do I enter my user name from the Ubuntu computer or do I enter salsnotebook user name from the Windows laptop? :confused:

---

### Post by superprash2003 on 2009-02-25
the username of the machine where the shares are kept.. in this case windows machine

---

