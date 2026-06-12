---
title: "samba share restricting no idea how to"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by mrgreaper on 2009-09-16
ok the title was hard to word so i hope i got it right lol

heres the problem, i have three shares on a server pc that is running the latest ubuntu desktop edition and default interface (gnome?) all shares were set up by right clicking and choosing sharing ticking all boxes but guest. through my powers of google i have found that the shares are stored in seperate files in /var/lib/samba/usershare and the main config file is smb.conf located in /etc/samba/ 
i also know that theres two types of authentication i can use, user and share sadly the help documention is not designed for mortals and only for system admins and it flys over my head. so im on the default of user names and log in as my ubuntu user when accessing shares from my windows netbook and pc, this is fine as it means anyone hacking my wifi would need that user name and pass to access my files. now my friends also access my folders when they are round this is also fine with one exception
ok the three shares are
main drive (this is the home folder of my ubuntu user) 
filedump (this is where all my files are stored and my mates files etc)
private (this has my bank statements bills letters etc )

now i want to restrict access to private 
two ideas spring to mind but no idea if they are doable
1)a 2nd password required to access the private share
2) only specific network ip addresses can access the private share (my netbooks ip or computername and my main pc ip or computername)

is it doable ...if so...how?

thnx in advance

---

