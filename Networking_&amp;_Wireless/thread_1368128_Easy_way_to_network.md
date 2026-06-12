---
title: "Easy way to network"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by mikecanada on 2009-12-30
Good Morning,
 I have two computers with Ubuntu 9.04 one with working pci wireles card the other cabled to a Dlink 625 router.

If I start Firefox on either computer and type 192.168.0.1 both computers log into the router,so that works.

If I go " Places" then " Network" neither cpmputer is seen,what do I have to do next to get the Ubuntu,s talking?

Thanks Mike

---

### Post by issih on 2009-12-30
For the purposes of this I shall guide you about using samba...which effectively uses windows networking protocols, nonetheless it is probably the most seamless way of doing networking on ubuntu. In some ways using ssh is easier, but its a bit more manual.

If things are working correctly (which I admit is not a guarantee :s) you should simply need to set up some shared folders on one of the machines.

By default ubuntu ships with the samba client (which allows you to see shared folders on other pcs) but no server element.

To share a folder, you just open the file browser, navigate to the folder (it must be one you own...not a root owned location) and then right click on it and select sharing options.

In that dialog select to share it and set it up as you wish in terms of who can access it. Once that is done the system should tell you that it needs to install various things, so ensure you are connected to the net and hit ok.

Once the system has finished downloading and installing the server packages you should be able to see the shared folder from the other pc, although some people find it doesn't work until they reboot the machine with the shared folder.

Once the server packages are installed, you can easily share folders directly from the file manager.

Hope that helps

---

### Post by Iowan on 2009-12-30
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is an NFS How-To you may want to look over.

---

### Post by mikecanada on 2009-12-31
Okay I should have mentioned sooner,I do have Samba on both machines with a Shared folder on each desktop.I did enable Share Options.

If I go Places,Network, then Windows Network the reply is "Unable to mount location" Failed to retrieve share list from sever.

Both firewalls are off,and my Windows laptop will connect but not the Ubuntu,s.

Any ideas ?

---

### Post by Iowan on 2009-12-31
On older versions, I had better luck with the "Connect to Server" option.

---

### Post by mikecanada on 2009-12-31
Does it matter if both computers are Mike-Desktop ?

Should I change one to another name?If I use "Connect to sever"like you did what settings did you pick ?

---

### Post by Iowan on 2009-12-31
Should probably pick another host name for one of the machines. There are a couple of threads with details - Can't find one showing the GUI way. In brief, you need to edit both */etc/hosts* and */etc/hostname*, otherwise **sudo** will get upset.

---

### Post by Morbius1 on 2009-12-31
There is another way if you're interested. Samba by default will use the hostname as the netbios name but you can tell samba to use another..

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:

**netbios name = some_name**

Change some_name to anything you want but it must be 15 characters or less and not have any spaces or Windows will have a nervous breakdown.

Save the file, exit gedit, and back in the Terminal type: [B]sudo service samba restart


[/B]

---

### Post by Iowan on 2009-12-31
Once again - I like your way better. If it makes Samba browsing happy, it sure seems less risky than a hostname change.

---

### Post by Morbius1 on 2010-01-01
> **Iowan said:**
> Once again - I like your way better. If it makes Samba browsing happy, it sure seems less risky than a hostname change.

It's only because, as you accurately stated, changing the hostname if not done in the right order and on both files results in you being sudo-less :). The reason I know this is because I made that mistake - twice :):)

---

### Post by mikecanada on 2010-01-01
Okay do I opened the terminal and did this,Open Terminal
Type gksu gedit /etc/samba/smb.conf


And after a short pause nothing happened,it went no further.

Maybe what you are trying to tell me is completely over my head and I had better give up.Won,t be the first one defeated by linux....

I will keep watching this thread,not the end of the world if I have to reload.

---

### Post by Morbius1 on 2010-01-01
Maybe it's the way I posted it:

Press **Alt+F2** ( press the Alt and F2 keys at the same time )

The "Run Application" should start. In the box type:
**gksu gedit /etc/samba/smb.conf**

It should ask you for your password and then open up gedit with smb.conf.

Does this not work?

---

### Post by Iowan on 2010-01-01
Whether to quit or learn is your decision.  
It occurred to me that some additional background work might be useful. Check the IP addresses of each machine (from the terminal, enter **ifconfig -a**).
 Verify that each machine can **ping** the other. If the machines have addresses 192.168.1.11 and 192.168.1.12, from the 192.168.1.11 machine terminal, type **ping -c5 192.168.1.12**, and from the 192.168.1.12 machine terminal 
type **ping -c5 192.168.1.11**. This doesn't need to be done simultaneously - you can do first one, then the other.

---

### Post by mikecanada on 2010-01-01
Okay guys I am back,just did the ALT F2 and the hit run,right now just looking where to put this name change described early.

---

### Post by mikecanada on 2010-01-01
Okay I am going to quite for now,not getting anywhere. Going to spend some time and think what I am doing some more.
       Thanks Guys Mike

---

