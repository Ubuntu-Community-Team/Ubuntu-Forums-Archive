---
title: "NetworkManager config dir missing"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-06-05
Hi guys,
I want t use NetworkManager to handle my NFS mounts (mount them as soon as a connection is established). I was told that NetworkManager can execute up/down-scripts found in /etc/NetworkManager/dispatcher.d - but this directory doesn't exist on my machine. I tried creating it and placing the script there - but it didn't work.

Do you have any ideas? Basically I want that as soon as the connection is up, the submounted NFS shares become mounted, and when the connection is dropped, I unmount the submounted dirs.

Tom

---

