---
title: "Re visiting network connectivity issues........"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by parkland on 2012-11-26
So this place has been upgraded... new cables, new network switch, new computers... etc. 
Still the same network issues, so it must be nothing to do with hardware. 


How can I share a folder in ubuntu, and have it's contents also shared? 
Sometimes folders inside of an already shared folders are not accessible. 

Using samba and ubuntu 12.10. 

I already disabled any firewalls I can find, before that the firewall blocked all samba connectivity. 
I'm just trying to make this work in a way that doesn't need to be constantly messed around with.

---

### Post by bab1 on 2012-11-26
> **parkland said:**
> So this place has been upgraded... new cables, new network switch, new computers... etc. 
Still the same network issues, so it must be nothing to do with hardware. 


How can I share a folder in ubuntu, and have it's contents also shared? 
Sometimes folders inside of an already shared folders are not accessible. 

Using samba and ubuntu 12.10. 

I already disabled any firewalls I can find, before that the firewall blocked all samba connectivity. 
I'm just trying to make this work in a way that doesn't need to be constantly messed around with.

There cam be multiple reasons for lack of access.  What error messages do you get when you try to access the unavailable shares?

Usually the symptom you describe is due to user permissions applied to the directory or file in question.

What does the share configuration look like?  What does the file system structure (both permissions and hierarchy) look like?

---

### Post by parkland on 2012-11-26
> **bab1 said:**
> There cam be multiple reasons for lack of access.  What error messages do you get when you try to access the unavailable shares?

Usually the symptom you describe is due to user permissions applied to the directory or file in question.

What does the share configuration look like?  What does the file system structure (both permissions and hierarchy) look like?



Its ubuntu 12.10, and I shared my "videos" folder so we can watch the movies on other computers, and media players. 


Sometimes it works, sometimes it doesn't. 

Sometimes the videos in the folder show up, but not the sub folders.

---

### Post by parkland on 2012-11-28
2 or 3 days have gone by, all of which has been flawless network access. 

Now, all of a sudden, neither media player can play any shared movies, and trying to access from a pc gives random errors, or shares or files don't show up at all. 


I tried rebooting, un-sharing then re-sharing the folder, enabling and re-disabling the firewall.... 

What am I missing?

---

### Post by parkland on 2012-11-29
OK, SOLVED !!!!!


had to go into samba config, 

and at the shares at the bottom, add

forceuser=user

where user is the user name on the computer sharing the files. 
:guitar:

---

