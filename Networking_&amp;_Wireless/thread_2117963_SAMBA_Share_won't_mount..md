---
title: "SAMBA Share won't mount."
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Fait on 2013-02-19
Hi, I had my windows shares working perfectly a few weeks ago with my two Ubuntu machines. I have changed absolutely nothing except updating Ubuntu and now they dont work. I get      


Unable to mount location    

Failed to retrieve share list from server      


When I set it up originally I had to add     


WORKGROUP = WORKGROUP 
 name resolve order = bcast host     

to "/etc/samba/smb.conf"    

When trying to fix this issue I have tried it with and without that modification and neither has worked (I rebooted between attempts)  Since then I have added 


netbios name = computer name     


where computer name is my computer's name in Ubuntu adding that line or "name resolve order = bcast host" gets me to the error I have mentioned above. Without either nautilus will hang when attempting to browse the windows network and eventually error out without displaying any of the computers. After the addition of one of those lines I am able to browse the network's computers but am unable to connect and instead recieve above error.    

Any help would be very much appreciated.

---

### Post by Fait on 2013-02-25
Any help would go a long way, even just pointing me in the right direction, thanks.

---

### Post by jimbo99 on 2013-03-15
After a long and deliberate consideration I've concluded that most people today don't actually know the technology going into Ubuntu and that those that are trying are just guessing.  

I've the same issue and it was caused by Kernel 3.8.x.

You can get this installed by when you install ubuntu 13.04 or by installing it on purpose from one of the repos.

---

### Post by bab1 on 2013-03-16
What were the kernel errors?  How did you determine that the kernel was the problem?

Yes, I understand Samba (SMB/CIFS).  ;-)

---

### Post by 23senick on 2013-03-16
Hi I had share issues in 12.04, not sure they related to upgrade but I missed something obvious. I think this highglghts the need for some decent, well publicised how-tos for Samba.   

Do you have firewall running?  That will block samba.  I use UFW and there's a simple command to open the appropriate ports

```
   [FONT=Ubuntu][SIZE=3]sudo ufw allow samba[/SIZE][/FONT]


```

This sorted it for me.  The only other thing is to right click the folder you want to share, check "properties", and then "share." Are all the right boxes checked?  I found I could only do this through Ubuntu - In LXDE and XFCE the file manager didn't have the same menus through propoerties.  

Hope this helps, and apologies if that was just too obvious...

---

