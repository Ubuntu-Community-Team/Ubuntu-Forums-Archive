---
title: "Transfering Files from Ubuntu 9.10 to Win XP Home"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Abisbowa on 2009-12-11
I am pretty new at using Ubuntu. I have a 7.5 gig file on my laptop that is running Ubuntu 9.10. I have a desktop that is running Windows XP Home. I want to transfer the file from the laptop to the desktop over a network (I don't have a flash drive). How would I go about doing this? 


When I go to Places > Network > Windows Network > MSHOME > MyComputer 
I get a pop up that says "Opening "MyComputer": press cancel to stop." It will sit there for a few seconds and another pop up will say "Unable to mount location: Failed to retrieve share list from server." 

Any ideas or direction to a post that this has been discussed would be greatly appreciated! 
Thanks in advance!

---

### Post by Rschnauzer on 2009-12-11
Did you specfy in Samba the same userid and password as in XP?
Otherwise you have to map the drive with explorer> tools and use option other userid.
Did you allow read access in Samba to the directory?

---

### Post by Abisbowa on 2009-12-11
Like I said, I am completely new to Ubuntu and Samba. I do have samba on my machine I just don't know how to use it. Could you direct me to a How To or Walkthrough please?

---

### Post by Rschnauzer on 2009-12-12
I only know the German Samba menu, the English terms may differ.
Enter Systemadministration > Samba
Complete the definitions.

[LIST]
[*]Add a user, f.i. the same user/pswd as in XP
[*]Add with server the workgroup from your XP system, in Windows "workgroup" is the default
[*]Add shares for all directories you want to read from XP.
[/LIST]

---

### Post by Iowan on 2009-12-12
[Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is a help page - but it's for 8.10.
[This]("https://help.ubuntu.com/community/SettingUpSamba") one has more information on Samba - but may not be exactly what you needed.
[This]("http://ubuntuforums.org/showthread.php?t=202605") How-To (although old) is still a good starting place.

---

