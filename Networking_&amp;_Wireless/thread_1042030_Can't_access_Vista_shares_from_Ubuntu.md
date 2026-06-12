---
title: "Can't access Vista shares from Ubuntu"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by garylouden on 2009-01-17
Hello

I recently decided that Ubuntu does a better job than XP on my laptop. I installed it and it works great. So much quicker and it just works.....no problems.


Well except 1 little problem but im sure its my fault. I have made 2 drives a share on my Vista pc. I was able to access these on XP but now i have Ubuntu I can see the Computer via "Network" in places. When I open the computer its blank and I cant see the 2 drives. 


Does anyone know what i need to do for this to work?

---

### Post by garylouden on 2009-01-21
Sorry but I have to bump as this is driving me crazy.

---

### Post by jonobr on 2009-01-21
Hello


Can you ping the other machine?
are all devices accessible via network?

---

### Post by jimv on 2009-01-21
I'm fairly certain that this is a known issue.

You can see the computer, but when you open it, you can't see the shares, right?

Try typing in the share name in the address bar like this:

smb://computer/share

If it comes up, then everything's working fine on Samba's end.  The problem is that GVFS doesn't pass credentials like it should, so you don't see the shares.  I'm pretty sure they fixed this in a more recent version...I'm going to test that once I've got the Jaunty iso downloaded.

---

### Post by Coreigh on 2009-01-21
You may also need to grant share permissions on the Vista machine. It works better when this is an intentionally shared folder and not a default share or a "Shared Documents" folder. In Vista and some XP you have to actually find the "Permissions" button on the Sharing tab and grant everyone permission. This is different than NTFS file permissions on the Security tab and can be a pain to figure out on the "Home" versions.

Here are two links on shares in Windows land;

[http://technet.microsoft.com/en-us/library/bb727037.aspx](http://technet.microsoft.com/en-us/library/bb727037.aspx)
[http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/)

---

### Post by posterlion on 2009-02-03
> **garylouden said:**
> Well except 1 little problem but im sure its my fault.

Hey Gary,

If you are running 7.10, it is probably your fault, but if you are running 8.10, then it's probably not your fault.

What version of Ubuntu are you running?

poster . . .

---

### Post by lar5 on 2009-02-04
i do have the same problem with nautilus. I remember seeing more threats about this issue. 

lets say ip and subnet is ok on both sides...

what it make working for me is not using the network browser, instead making the connection manualy by using: Places   > Connect to server... 
as service type choose: Windows Share
in Server the ip of your server
and in share the name of the share. 
(take care not to have blanks in the name of the share. i am not shure about this, but anyway like this u are on the the shure sidde.) 

another good tool is smb4k to connect to windows shares. its for kde but works very nice in ubuntu.

---

### Post by Trojan_Neo on 2009-02-04
Hi guy's,

Today I bum into the same problem.
i'm running 3 OS with VistaHome Premium build 6000, XPProSP3, Ubuntu 8.10

with XP i don't have any problem only with vista.

I didn't install any SAMBA or SMB dependencies.  

any idea...will be welcome....

Trojan_Neo

---

### Post by stennieville on 2009-02-07
I'm pretty sure the problems connecting from Ubuntu to Vista have more to do with Vista's networking policies than anything on the Ubuntu side.  I had trouble just getting my two Vista computers sharing files back and forth; adding the Ubuntu computer to the mix was an extra helping of frustrating.

I was finally able to mount shares from my Vista Home PC's on the network by going through the following steps:

1. From the Places menu, choose "Connect to Server"
2. Service Type: Windows Share
3. Server: [Name of Computer you are connecting to]
4. Share: [Name of Shared Folder]
5. I left the other fields blank except Username, where I typed in the username for the Ubuntu computer.  **I also had to add this User to my Vista PC as an administrator, and grant permissions to the Share folder for this User.
6. Click "Connect" and when prompted, type in the password for your account.

The mounted share will appear on Ubuntu's desktop.  I still can't get the printer share to work, but at least now I can share data back and forth.

---

