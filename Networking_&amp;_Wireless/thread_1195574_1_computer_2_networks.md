---
title: "1 computer 2 networks?"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by I-Imaging on 2009-06-23
I have just started posting and another user told me that this is the best community and that it's not strictly Ubuntu/Linux questions that are answered. I hope I'm not overstepping what he meant by asking this question. If this is inappropriate or in the wrong stop I hope a moderator could just delete or fix it. 

Here is the question... I am trying to create a wireless network at my parents place and have it working, mostly. My system (Ubuntu) and my dad's (xp home) laptop connect to each other fine but my mom's (xp pro) is causing some issues. She can see our files and change them but we can't see her's. I think it's because her laptop is a work one and has a connection there. So is there someway to connect her computer to her work network and the home one?

Thanks.

---

### Post by fugaki on 2009-06-24
are you setting up an ad-hoc network, or do you have a router involved?

---

### Post by I-Imaging on 2009-06-24
Since I have no clue what an ad-hoc network is I'll assume it's strictly through the router? I did set up the router. Is this helpful?

---

### Post by puppywhacker on 2009-06-24
hi,

your network setup seems to consist out of one network, your computers get an ip-address from the router and it is probably a private address like 192.168.x.y (check it with ifconfig or ipconfig in windows). the problem you describe is about filesharing. "seeing" a computer is done based on broadcasting on the network to see who responds. "yoohoo, who is on workgroup XYZ". That a corporate laptop won't respond to these requests is usually due to corporate policies or software firewalls. you can try to connect to the machine anyway if you know the ip-address.

from nautilus you have to connect to smb://192.168.0.3
and from the windows explorer type \\192.168.0.3

ofcourse substituting the ip address with the one on the unwilling computer

---

### Post by I-Imaging on 2009-06-24
> **puppywhacker said:**
> hi,

your network setup seems to consist out of one network, your computers get an ip-address from the router and it is probably a private address like 192.168.x.y (check it with ifconfig or ipconfig in windows). the problem you describe is about filesharing. "seeing" a computer is done based on broadcasting on the network to see who responds. "yoohoo, who is on workgroup XYZ". That a corporate laptop won't respond to these requests is usually due to corporate policies or software firewalls. you can try to connect to the machine anyway if you know the ip-address.

from nautilus you have to connect to smb://192.168.0.3
and from the windows explorer type \\192.168.0.3

ofcourse substituting the ip address with the one on the unwilling computer

Ok it's the windows machine that's causing the trouble. I typed in the ip address in explorer and got my router setup settings. I'm kind of confused on what to do now. 

Since it can view the other computers and access them would it most likely be policies or firewalls preventing it from being seen from the others? I do have admin rights on all of the systems so I think I'd be able to change them if I knew what I was doing. ;)

Thanks for the help.

---

### Post by puppywhacker on 2009-06-25
if you get your router setup page two things went wrong, one you had the wrong ip-address, and also windows tricked you into going to an http:// address and not samba. Check the proper ip-address with ipconfig on windows. then do the smb:// again on the linux file explorer "nautilus"

but again, if it doesn't show you anything, it is probably the windows policies that are set on the corporate laptop, do you your sharing from the server side that doesn't have the policies and do use the laptop as client

---

