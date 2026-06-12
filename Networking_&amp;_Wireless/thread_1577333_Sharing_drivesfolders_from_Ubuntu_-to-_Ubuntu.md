---
title: "Sharing drives/folders from Ubuntu -to- Ubuntu"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by Ben_neB on 2010-09-18
Greetings,

This is my first attempt at sharing folders across my three home computers. My main computer, which is the computer from which I need files and folders shared, is running Ubuntu 10.04. 

On this computer, there are two hard drives. Ubuntu and Vista are on the primary hard drive, and the second drive has XP and Mepis, and 300gb of NTFS-formatted storage space. 

My other two computers are both dual-booted with Ubuntu and XP. (One machine is still on 9.10, the other is 10.04) 

So, what I'm trying to do it two-fold; 1) Share files from the primary hard drive, which I can successfully do with all three computers whether the "client" computer is running Ubuntu or XP. However, step 2) is to share folders from my main computer's second hard drive. This is where I am encountering the problem.

I have the shares setup as follows. I go to System->Administration->Shared Folders and browse to the desired folder. Then I select "Share Through"->Unix Networks (NFS). (That is the only choice. For some reason, there is no option for it to be SMB. This is another of my incongruities.) Then I go to "Allowed Hosts" and add the IP addresses of my other two computers. 

I have also browsed to the desired folders in Nautilus and shared them that way. I'm honestly not sure if both steps are necessary, but that's what I've done in any case. 

Now, the results are that from either of my other two computers, I can boot into XP and access the shared folders on my main computer's primary hard drive with no problems. (I have to log in with my main computer's username and PW, which is a little annoying, but not a deal breaker.) But to access the folders on my main computer's secondary drive, I have to first access one on the primary drive. If I don't do that first, then Windows will tell me that I don't have permission to access that folder. (This is again, annoying, but I could live with that.) 

The biggest problem is that if I boot either of my two other computers into Ubuntu, I can access the main computer's primary drive just fine, but any time I try to access the folders on the main computer's second drive I get the error "Failed to mount Windows Share". 

What I find especially odd is that I even get this error when I use my main computer. I go to Places->Network->Windows Network->WORKGROUP->FolderName, and I get that same error, even though I'm trying to access it from the very same computer where I'm sharing it. 

So, I get the feeling that I'm fundamentally doing something wrong, or missing some step. 

Any help whatsoever would be greatly appreciated.

---

### Post by Ben_neB on 2010-09-18
Just an update; Got it to work by installing the Samba4 packages, and using the accompanying gui to share the folders. That's actually considerably easier to use than what I was trying to do.

---

