---
title: "Lost access to shared folders on XP"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2010-05-09
Prior to upgrading from Karmic to Lucid I could access shared folders on my partners XP system.  Now when I attempt to connect to the shared folder I am unable to see the folders.

When I display the network I can see MSHOME but thereafter end up with the following :

[B]"Unable to mount location
Failed to retrieve share list from server"[/B]

Can anyone offer guidance?

Strangely enough I am able to connect to another Lucid system easily enough from my laptop.

In each instance both my Lucid systems and the XP one are connected via wireless and as far as I can see the setup on the XP system is networked OK.

---

### Post by Scunnered on 2010-05-12
Bump

---

### Post by JoeEndUser on 2010-05-12
Can you connect via Places - Connect to Server - Windows Share? You should not need any more information than the ip address of the machine you are connecting to.

---

### Post by xtremedementor on 2010-05-12
I have just realised that i have the same issue.

I have 3 machines
1 Ubuntu 10.04 desktop
2 Ubuntu NBR 10.04
3 Windows 7 Home Premium.

My win 7 can see all the share on  machines 1 & 2.
1 & 2 can access shares if i use Go - IP Address

However if i go to Network / Windows Network / Workgroup i get the error message "Unable to mount location Failed to retrieve share list from server"

I cant remember this being a problem in 9.1 with the same setup.

Any help is greatly appreciated as i am trying to convince the rest of the household to drop win 7 for Ubuntu.

Thanks

---

### Post by Scunnered on 2010-05-13
**JoeEndUser**

Thanks vm for the suggestion however the result is still the same.

---

### Post by xtremedementor on 2010-05-13
I connected at work today on a mixed network Macs and Win and the 
Network / Windows Network / Workgroup worked fine.

Apple AFP shares showed up under network even though i can not connect to AFP and the win shares (Both MS and Mac) showed under Network / Windows Network / Workgroup and i could connect no problem.

Meanwhile back at home Ubuntu to ubuntu samba shares are still a no show in Network / Windows Network / Workgroup

but my Win 7 can see and connect to both ubuntu boxes.

I have doublr checked that i am set to "WORKGROUP" for the smb workgroup.

At this point i am stuck  :confused:

---

### Post by JoeEndUser on 2010-05-13
I got my lucid machine talking to Windows and others with Dmizer's guide [http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve")

Specifically problem 3.

I rebooted my modem, router and all machines just for good measure, I don't know if that is necessary though.

It did take 5 or 10 minutes to catch once my machine was rebooted.

---

