---
title: "MS Win 2003 server"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-06-25
HI

I'm runnning Ubuntu 10.04 Desktop, and i need to connect to a Windows 2003 server, i've clicked on places at the top of the screen selected connect to server and put in my detains in all the vairing options and i still cant get on.

if it could be explained that information i need and where i can get it from in XP, i also need to log in then i access it from xp.

I'm sorry i'm unaquainted with servers so please treat me as a newbe.

Thanks

chris

---

### Post by emyr42 on 2010-06-25
Have you ensured Samba-client is installed?

---

### Post by Ceiber Boy on 2010-06-25
> **emyr42 said:**
> Have you ensured Samba-client is installed?


sudo apt-get install Samba-client

is this right?

---

### Post by pricetech on 2010-06-25
I'm thinking Samba should be there already, at least the client portion, but I always install Samba anyway, so I could be mistaken.  You can install it via Synaptic also.  Choose system-config-samba to get Samba plus the GUI configuration tool in case you need to share something for whatever reason.

More specific to your question, you should use the same credentials under Ubuntu that you would use under windows to log in.  Also the IP and Sharename would be the same as well.

---

### Post by CharlesA on 2010-06-25
What's the error you get back after you try to connect?

---

