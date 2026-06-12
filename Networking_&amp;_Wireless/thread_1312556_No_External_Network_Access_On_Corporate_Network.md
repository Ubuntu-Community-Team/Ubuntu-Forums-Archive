---
title: "No External Network Access On Corporate Network"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by mike3244 on 2009-11-03
I have been using 9.10 on my company network quite happily since it was released, however this morning I am unable to access the internet.

I still have access to our Intranet, I can browse our Windows network and Evolution is still pulling mail from OWA.

Pinging and address resolves the name and returns no errors and I can run tracrt.

Booting into windows works as before.

I am going to change location tommorrow and see if things are OK there - but if anyone has any thoughts.

=====
Proxy configuration script now in use by company - added address to Firefox

---

### Post by pedro_orange on 2009-11-03
Sorry but your description was a little short.

Are you actually going through your company intranet to get to the internet? Are you a member of the domain? Perhaps IS have done something to stop you going through the firewall.

Or are you connected to a separate network for the internet? If so, check your routing table and the connection. 

Attempt to address the gateway. Perhaps the problem is out of your reach (Unless you have access to internal IS!)

EDIT: Ignore this! Glad you're sorted!

---

