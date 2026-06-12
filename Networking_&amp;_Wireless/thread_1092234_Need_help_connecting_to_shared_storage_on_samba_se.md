---
title: "Need help connecting to shared storage on samba server"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by SirDucky on 2009-03-10
Hi all,

Running:
Ubuntu with Gnome
Intel Dual-Core 3.0Ghz
Hard line LAN connection

I'm a new student at Uni (or college as you prefer) living in a residential college.  One of the services they offer on the network is a storage space for my files.  This is stored on a samba server.  For whatever reason, I cannot access my personal storage (or some of the uni network for that matter).

 I am dual-booting windows and can access it on the windows partition, so I know it's working, but I mostly run linux and can't go restarting all the time.

The process prescribed:
(this is pulled from my college intranet page, and is a step-by-step for connecting under Windows or Mac)

```

Windows:
Click to view the video version of these instructions.

   1. Open 'My Compter' -> Tools -> Map Network Drive.
   2. In the 'Map Network Drive' window that pops up, set the following options:
          * Drive: Z to Folder: \\timmay\homes
          * Reconnect at logon (should be ticked)
          * Click 'Finish'
   3. After you click 'Finish', it should popup a window asking for your username and password. Enter your intranet username (eg q2001234) and password. If you get the option to 'Remember your password', please tick the checkbox. Finally, click 'Ok'.
   4. A window should popup - this is your storage space.

Mac OSX:
The easiest way to access your network storage space is by "Connecting to a server". Follow these steps:

   1. In Finder, select "Connect to Server" from the "Go" menu (alternatively, press apple-k when in Finder)
   2. In the "Server address:" box, type "smb://10.0.0.2" and click "Connect"
   3. A window will pop up titled "SMB Mount" - select "Homes" from the drop down menu and click "OK"
   4. When prompted for your username/password, type in your queens username (q200....) and your password In the finder window, you will now be able to see a "HOMES" drive on the left.

```

What I've tried:

Okay, so I try to connect to it by clicking Places->Connect to a Server, and setting the Service Type to "Windows Share".  I've also tried Custom and FTP for all the good it did.

Under the fields I've tried:
Server - both name and IP (\\timmay and 10.0.0.2 and smb://10.0.0.2 and \\timmay\homes)
Share - Home or QUEENS or Homes
Folder - Home or Homes
User Name - my network login, goes q200####
Domain name - QUEENS or WORKGROUP or Homes or Home

I got an IT guy up here to help me brainstorm, and we tried literally EVERY COMBINATION, upper or lower case or caps, including leaving fields blank.  Nothing worked.  In many cases It will take me to the next screen, where I will have to enter
A) a Domain (if I didn't enter it in the previous screen)
B) a password (which I have tried both blank and the one corresponding to my user account)

no matter what, after this I get an error saying
"Failed to retrieve share list from server"

I know the WORKGROUP I'm supposed to be on is called "QUEENS".  However, I'm not sure is this is the same thing as a Domain, or if not, if it corresponds to another field.

When I type "smb://10.0.0.2" into the address for nautilus, I can see the folders contained by the samba server ("homes" is one of them).  Some I can double-click on and they will mount.  They have media on them.  When I double click on "homes" it gives me a slightly different error:

"Failed to mount Windows share"

same idea.

I think they have it set up so that you can mount the "homes" folder but can only view YOUR storage forlder.



As if this weren't enough, I'm having some other network related troubles that are less important/complicated but could use some help on:

A)  Many of my friends share media on the intranet network.  Most of them are under the QUEENS workgroup.  I can view a few computers on "Network" but not the ones on the QUEENS workgroup.  There is also an icon in Network called "Windows Network" which lists what look like a number of Workgroups such as "WORKGROUP", "MSHOME", "QUEENS" and "DEFAULT".  I can access all of them except "QUEENS" and "PRIVATE", sometimes with computers from "Network" reappearing.  However, when I double click on "QUEENS" or "PRIVATE" I get this error:

"Failed to retrieve share list from server"

Do I need to somehow change my Domain or (if I have one) my Workgroup?

B)  We also have some network printers.

I cannot print from them.  Apparently I need to connect to my storage space before I can use them (for payment purposes), so for now this is on the backburner.  Just throwing it out there so that I can possibly get back to it.


Thank you so much to anyone who actually takes the time to read this and reply.

---

### Post by SirDucky on 2009-03-11
bump.

pleaaaase?  I've tried everything.

---

### Post by KevinJr on 2009-03-23
Hello Everyone, 

I'm actually having this problem too. It started after installing Vmware2. I've tried to uninstall it via the uninstall script however that script proves useless. 

My Specs:

Ubuntu 8.10
Dell 1525 Pentium Dual Core
Local Workgroup based network.

I do believe this is directly related to VMware's network / network interfaces however I do not have the knowledge on how to reverse this. 

Thank you all so much for your help, I will provide any information needed to solve this issue.

---

### Post by ddnev45 on 2009-03-23
Start with these; all are from the "Tutorials and Tips". Hope you find your answer.

I use this one a lot:

[http://ubuntuforums.org/showthread.php?t=288534&highlight=join+windows+domain]("http://ubuntuforums.org/showthread.php?t=288534&highlight=join+windows+domain")


[http://ubuntuforums.org/showthread.php?t=202605&highlight=join+windows+domain]("http://ubuntuforums.org/showthread.php?t=202605&highlight=join+windows+domain")

[http://ubuntuforums.org/showthread.php?t=5409&highlight=join+windows+domain]("http://ubuntuforums.org/showthread.php?t=5409&highlight=join+windows+domain")

---

### Post by KevinJr on 2009-03-24
Hey ddnev45,

thanks a lot for getting back to my post. I will give these a try. I apologize for not looking in that section first. I spent countless hours on Google trying to find a solution.

Thanks again!

---

### Post by dmizer on 2009-03-25
Given the directions outlined by your college's website, you should be able to mount the shares using the second link in my signature.

ddnev45 gave tutorials for joining a domain, which is far more complex and shouldn't be necessary.

---

