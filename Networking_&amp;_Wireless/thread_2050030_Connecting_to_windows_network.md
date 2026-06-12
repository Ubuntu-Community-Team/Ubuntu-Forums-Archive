---
title: "Connecting to windows network"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by scampbell70 on 2012-08-29
I use Ubuntu at home and I love it. At my job I have been asked to connect a linux machine to our existing windows network and it is not Ubuntu, I believe it is an arch distro that the last guy setup. Changing the distro is not an option so I have to ask what software does ubuntu gnome use that allows for automatic discovery of network computers. I need to be able to not only see the entire network at boot but allow users to access windows shares and map them to there home folders without them having to do anything. Can the community please give me a hand solving this issue. I am sure there are some masters out there who can tell me exactly how to do this or what software I need to install.

Thank you in advance

---

### Post by beboylips on 2012-08-30
Install Samba.

```

apt-get install samba

```

Network Shares/Hosts will appear in Network Servers either right away or after restart or can be connected to manually.

---

### Post by dandnsmith on 2012-08-30
You only need the client side of the Samba software - and this is often supplied as default in the distro, even tho' the server side isn't.
The client side gets the SMB facility, which is what Windows uses for file and printer shares.

---

### Post by beboylips on 2012-08-30
Install the hole package, client AND server. That way, your computer will be accessible and you will be able to access others.

---

