---
title: "Repeated Network Authentication Requests"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by larryma on 2009-01-29
I am new to Linux and have installed Ubuntu 8.10 on my Dell Precision M60 laptop. Pretty much everything works well after the installation, but I have a problem with the wireless networking. At login, it asks for wireless network authentication. The passphrase is already in the passphrase box, so I can hit "connect" and it will connect to the network.

Unfortunately, it will repeatedly ask for network authentication, with the same box. The network still seems to be connected, even if I "cancel" a repeated authentication popup. I can get a number of these repeat requests.

I hope you can help me with 2 items:

1. how can I stop the repeated auth requests?
2. how can I bypass auth requests in the future all together (at least for networks where I have the passphrases)?

Thanks in advance for your help!

Larry

---

### Post by lisati on 2009-01-30
I'm using Vista at the moment so I'm unable to check on my machine, but one thing you might want to check are your "keyring" settings.

---

### Post by larryma on 2009-01-30
Thanks, Lisati!

When i go to System-Preferences-Encryption and Keyrings, I find:

PGP Passphrases tab: Always remember passphrases radio button is set. All other boxes unchecked.

Encryption tab: Default Key: None, prompt for a key

Is there some other place to check?

Larry

---

### Post by larryma on 2009-02-04
Anyone have other suggestions?

---

### Post by nellmathew on 2009-02-04
Try simply disabling wireless (uncheck "Enable Wireless" from the checkbox) and renable, that stops it from asking me, I had the same issue with WPA. Maybe there's a way to make a script to do this during boot if it works?

---

