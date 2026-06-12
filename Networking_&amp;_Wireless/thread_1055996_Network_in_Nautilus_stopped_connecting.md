---
title: "Network in Nautilus stopped connecting"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by tsucol11 on 2009-01-31
I can no longer see my network from Nautilus (Ubuntu 8.10). It worked fine 2 days ago.

I did 2 things yesterday.

1- I added my partitions to Fstab and rebooted. The partitions were mounted automatically. I did not check the network at this time.

then

2- I updated, through update manager, from: 

Ubuntu 8.10, kernel 2.6.27-9-generic to Ubuntu 8.10, kernel 2.6.27-11-generic (automatically including all the required files).

Computer worked fine. Again I did not test the network at the time.

Today I tried to access my Windows XPpro box using Nautilus, with the end result being that the location (in Nautilus)is now "Network:///" notice the 3 forward slashes. When I click on the Network:/// I get "smb:///" in the Nautilus location box but cannot get the network up (no workgroup icon).

Now for the weird part: If I remove one of the forward slashed "smb://" and type in one ip address the whole network comes up. If I type the smb://..ip. address in Firefox I get connected asap. If I close Nautilus but keep my ubuntu session running I can reopen Nautilus & get immediate access to my network (including file transfers both ways).

Question-- what should I do to remove the third forward slash from "network:///" & "smb:///"

As stated above until 2 days ago my network was stable. Also if I boot from the older kernel kernel 2.6.27-9-generic I now get the same error.

Thank you

Brian

---

### Post by Another Monkey on 2009-01-31
Does "net view" at a command prompt on the windows machine work, or give an error?

---

### Post by tsucol11 on 2009-01-31
> **Another Monkey said:**
> Does "net view" at a command prompt on the windows machine work, or give an error?

From the windows XP box, it can see the shared shares on the Ubuntu computer. However it cannot enter the shares (or see the directories & files).

If I replace smb:/// with smb://192.168.2.88 on the Ubuntu box(IP add for the windows box) it wakes up the Ubuntu box & then the whole network is available (windows is then able to peruse the files).

The error is with the Ubuntu box. Why all of a sudden??

Brian

---

### Post by Another Monkey on 2009-01-31
Not sure why all of a sudden (I did notice that some of my network settings got nuked in the recent kernel update), but the only time I have had that exact issue was when one of my firewalls was getting in the way.  I had to make sure that "Microsoft SMB over TCP" was allowed in Firestarter (and "NetBIOS" allowed on Kubuntu via Guarddog).

You can try "net view \\ubuntu" on the Windows box and see if you get some message to explain things.  For exmaple "error 53" would indicate you have some name resolution problems.

I think I got my network going by trial and error and a bit of luck - I made some recent postings on the issues and solutions I found.  Maybe one of them might give you some help?

I'm pretty new at Linux, sorry I don't have the knowledge or time to be of more help just now.

---

### Post by tsucol11 on 2009-01-31
> **Another Monkey said:**
> Not sure why all of a sudden (I did notice that some of my network settings got nuked in the recent kernel update), but the only time I have had that exact issue was when one of my firewalls was getting in the way.  I had to make sure that "Microsoft SMB over TCP" was allowed in Firestarter (and "NetBIOS" allowed on Kubuntu via Guarddog).

You can try "net view \\ubuntu" on the Windows box and see if you get some message to explain things.  For exmaple "error 53" would indicate you have some name resolution problems.

I think I got my network going by trial and error and a bit of luck - I made some recent postings on the issues and solutions I found.  Maybe one of them might give you some help?

I'm pretty new at Linux, sorry I don't have the knowledge or time to be of more help just now.

I will try the "net view \\ubuntu" at the next reboot

Thanks

Brian

---

### Post by tsucol11 on 2009-02-01
> **tsucol11 said:**
> I will try the "net view \\ubuntu" at the next reboot

Thanks

Brian

Problem appears to be solved. I reinstalled Nautilus plus Nautilus add-ons and everything is working OK  right now.

Thanks for your time Another Monkey

Brian

---

