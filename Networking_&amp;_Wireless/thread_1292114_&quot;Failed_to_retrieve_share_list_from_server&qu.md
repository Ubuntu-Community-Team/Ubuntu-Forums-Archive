---
title: "&quot;Failed to retrieve share list from server&quot; please help"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by saintslaughter on 2009-10-15
I know this is posted already, but with so many small differences from person to person, I made my own post to get direct clarification.

On my network I have two machines. One has windows vista installed, the other Ubuntu 9.04, both are a fresh install. When browsing my network with vista every computer shows up. When I try to with my ubuntu machine, I click on Windows Network and I get the Error ; "Unable to mount location: Failed to retrieve share list from server." I can ping my vista machine. I have samba installed, (though smb.conf might not be configed properly) I did follow Dmizer's tut. but no dice. [http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve+share+list+server](http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve+share+list+server)

I cannot reach the machine via ip smb:\\ip address\share folder  in Nautulus, Fire fox, or opera. In a terminal via smbclient (if i remember right) it returns a message Connection_Rejected.

On my vista machine I have tried with password protect on and off, as well as making the ip static, and sharing a folder instead of the root drive.

I have tried this at work as well which as a mix of linux machines, and  M$ machines of various os ver. I can not browse to any of them, except for my Hacked Ipod touch :P that worked great.

I had two fire walls installed, (testing purposes) GUFW? something, as well as firestarter, both have been uninstalled before I began troubleshooting, and I have manualy added iptables to allow any and all on ports that windows might try to use, via Dmizers tut. 

I have had this problem for a few months any help would be really awsome, and would totaly save my lazy butt from getting off the couch to transfer files via jumpdrive.

thx.

---

### Post by wbm on 2009-10-15
I was just about to post the exact same question. So you are not alone :(

This solution worked for me to get to the workgroup:
[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

I still cannot browse the network though from Places < Network

---

### Post by saintslaughter on 2009-10-15
Thank you for the reply, This has worked!!! Last time I tried, it did not, Not sure what has changed... However if anyone has a fix rather than a work around please post! thanks again wbm

---

### Post by wbm on 2009-10-16
> **saintslaughter said:**
> Thank you for the reply, This has worked!!! Last time I tried, it did not, Not sure what has changed... However if anyone has a fix rather than a work around please post! thanks again wbm

I did notice that you used "\" in your original post, where in that link it shows to use "/".
Can you browse the network though? That still does not work for me. I can only access locations if I know the address.

---

