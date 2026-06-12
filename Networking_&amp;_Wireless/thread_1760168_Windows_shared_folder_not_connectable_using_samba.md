---
title: "Windows shared folder not connectable using samba"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Gendron5000 on 2011-05-16
From my Ubuntu(10.04) machine I have a VPN connection to a network where I have access to a windows PC.  The PC is connectible (using terminal server client) and ping-able.  However, I'm unable to mount a shared folder I have setup on the PC.

Trying 'smbclient -L <IP-Address>' gives me 'Error NT_STATUS_UNSUCCESSFUL'.  I have also tried using the -U switch and putting in my windows user name but i get the same error.

Going to nautilus->Network displays 'Windows Network', but trying to open it gives me a mounting error: 'Failed to retrieve share list from server'.

I have a feeling the problem is because the windows pc is on a domain...

I have searched for a solution, but have not been able to find a post with the same issues.

any suggestions on where to go from here would be great!  thanks.

---

