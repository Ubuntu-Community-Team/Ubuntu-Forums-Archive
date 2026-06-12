---
title: "Samba server???"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by tygsxr on 2011-05-15
Hi, Can anyone help me with this issue? When inspecting my router logs i found this line
"Samba name server ROUTER is now a local master browser for workgroup WORKGROUP on subnet 192.168.5.17" My question is why is Samba name server running when i have not intenionally enabled it, i dont network between windows and ubuntu. So should this be running and if not how do i turn it off.. Question 2- It shows the IP 192.168.5.17 but the ip range for my router is 192.168.2.1-100. I typed this IP into my browser and it took me to my routers configuration page. My routers log on page is at the start of the range i mentioned above. Sorry if this is a noob sort of question.. Any help would be appreciated  Cheers

---

### Post by dandnsmith on 2011-05-15
What sort of equipment is this router? - standard netgear,dlink ..., or a PC which you have configured yourself?

You haven't given any sort of clue, unless someone else happens to have seen the same thing (I haven't in any of my router logs)

---

### Post by tygsxr on 2011-05-16
Hey Derek, My modem/router is a Belkin N600 HD. Cheers

---

### Post by dandnsmith on 2011-05-16
Perhaps it's automatically enabled on that (separate) subnet to provide services for use with the usb ports on your router - I'm just guessing, as I haven't used one, or specced it for possible use, and the Belkin site isn't much help.

---

### Post by tygsxr on 2011-05-17
Thanks for having a look at the belkin site derek. I checked it myself and got the same results. You could be right it could be some ip used for some other service to do with the router. I am still interested in knowing about this Samba server issue. Something about smb protocol. I am thinking that it might be WINE that is using this program because samba is used to share programs between windows and linux. ill keep researching and post when i no more. Cheers[B]
[/B]

---

