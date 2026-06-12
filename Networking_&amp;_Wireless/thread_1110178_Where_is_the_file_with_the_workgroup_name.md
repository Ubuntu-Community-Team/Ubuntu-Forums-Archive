---
title: "Where is the file with the workgroup name?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by ranch hand on 2009-03-29
I think that I have all the info I need to connect my 2 8.10 boxes using NFS.  This is very exciting for me - ADSL and a huge (2 boxes) home network.

There is one problem with this though.  I do not know what the workgroup is on my other computer (I didn't write it down).

I have been searching all day and all I am coming up with are references to Samba networks including off brand computers.  These references tell me my workgroup name is in /etc/samba/smb.conf.

This is not the case at all.  I know the workgroup of this box (I edited and wrote it down during install).  This is not in that file.

I need to know where it is so that I can find it in my other box and change that one to match this box.

I do have a number of installs on the other box so I could just have another and make the workgroup conform that way.  This seems silly if all I need to do is edit some other file and be able to work with one I have or change the name in several I have so they can all get to this one.

It is my hope that there is someone out there that is smarter than I am.  It would help if I were smarter than the keyboard.

---

### Post by capscrew on 2009-03-29
> **ranch hand said:**
> I think that I have all the info I need to connect my 2 8.10 boxes using NFS.  This is very exciting for me - ADSL and a huge (2 boxes) home network.

There is one problem with this though.  I do not know what the workgroup is on my other computer (I didn't write it down).

I don't think "workgroups" are used when you use NFS.> 

I have been searching all day and all I am coming up with are references to Samba networks including off brand computers.  These references tell me my workgroup name is in /etc/samba/smb.conf.


This seems appropriate.  What do you mean by "off brand computers."?  The workgroup in Samba is used to define the computers that are browsable in the network.
> 

This is not the case at all.  I know the workgroup of this box (I edited and wrote it down during install).  This is not in that file.


What did you edit?  Could you be referring to the term "domain"?
> 

I need to know where it is so that I can find it in my other box and change that one to match this box.

If you are using NFS, you export the directories and then mount them on the remote host (computer).> 

I do have a number of installs on the other box so I could just have another and make the workgroup conform that way.  This seems silly if all I need to do is edit some other file and be able to work with one I have or change the name in several I have so they can all get to this one.


I'm not clear on what you mean about "installs".  Installs of what?
> 

It is my hope that there is someone out there that is smarter than I am.  It would help if I were smarter than the keyboard.

I'll try and help but, I'm not sure I understand what you are doing.  I do have 2 Samba servers that have Ubuntu and XP clients.  If you are looking to use NFS, then I would suggest starting [**[COLOR="Blue"]here[/COLOR]**]("http://www.google.com/search?q=nfs+howto&btnG=Go!")

---

### Post by ranch hand on 2009-03-29
I believe that I need to have a workgroup name with a NFS network.  I could be wrong.

By off brand computers I am refiering to OSs that are the product of MS.

I did not use the workgroup name selected by the installer.  This comes up after you enter your name, username and password.

I actually have 5 320Gb Hdds with various flavors or different configurations of flavors on them.  I believe that I currently am playing with 9 flavors (that box is 54 miles away with a blizzard currently trapping me in town instead of at the ranch).

Thank you for the link.  I may haave missed some of those.

What I really want to know is where that workgroup name that is created when you install is actually filed.

Everything else, I think, will be very simple once I get the other computer to town and get my router (being shipped) and cables (also on the way).

Even here in the BIG CITY (county seat population 500) it is faster and cheaper to order things and have them delivered.

---

### Post by capscrew on 2009-03-29
> **ranch hand said:**
> I believe that I need to have a workgroup name with a NFS network.  I could be wrong.

I do not believe that is the case.  It's been a long time since I have used NFS (Sun Solaris 8 days), but I'm sure that there were no "workgroups" in NFS.  In practice, how would you use the workgroup"?  Would this be browsing for a share?
> 
By off brand computers I am refiering to OSs that are the product of MS.

Hmmmm
> 
I did not use the workgroup name selected by the installer.  This comes up after you enter your name, username and password.


I dont remember that part.  What was the default name used by the installer?  I believe you will find that until you install Samba, workgroups are not relevant. 
> 

I actually have 5 320Gb Hdds with various flavors or different configurations of flavors on them.  I believe that I currently am playing with 9 flavors (that box is 54 miles away with a blizzard currently trapping me in town instead of at the ranch).

Thank you for the link.  I may haave missed some of those.

What I really want to know is where that workgroup name that is created when you install is actually filed.

Could you be referring to the hostname of the box?  That is stored in /etc/hostname.
> 

Everything else, I think, will be very simple once I get the other computer to town and get my router (being shipped) and cables (also on the way).

Even here in the BIG CITY (county seat population 500) it is faster and cheaper to order things and have them delivered.

Once again, the term workgroup (a MS convention) is used to define group of computers that can be browsed in the network.  Samba is the open source equivalent of Windows Sharing.

Let me know how I can further help when you  have everything in one spot.

---

### Post by ranch hand on 2009-03-29
The host name is not what I am looking for but if I don't need the workgroup name who cares.

All linux flavors that I have installed have set a workgroup name pretty much at the same stage of installation.  I have not paid much attention to them as I have always just had 1 box.

---

### Post by capscrew on 2009-03-29
I agree.  If you are going to set up NFS then the workgroup name is irrelevant.

Maybe that is so they are ready to browse for Windows shares straight away.  I've noticed a trend with Ubuntu to be more compatable with all OS's

---

