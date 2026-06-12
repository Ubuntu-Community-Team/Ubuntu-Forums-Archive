---
title: "SSH port change no longer working"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2009-12-18
So I had SSH working for me so I could transfer files from work to home.  

I decided to try and change the port but now I can't connect.  I changed the port in the SSH config, and I forwarded the new port to my computer, and I use the -p command with ssh from the remote machine.

I'm at work now, and can't connect, and the only thing I can thing of is if Ubuntu is blocking my new port in the firewall?  I thought by default the firewall didn't block anything.  But do I need to specifically allow the firewall to allow my new port?

Or could it be something else?

---

### Post by lewisforlife on 2009-12-18
Did you open up the new port on your router and port forward it to your SSH box?

---

### Post by NertSkull on 2009-12-18
I did.  The router is forwarding the correct port.  I'm pretty sure everything is set up correctly for the ssh server.  I was just curious if it could be the firewall.  I guess I'll just mess with the firewall setting when I get home, and if that doesn't fix it, I'll come back.

---

