---
title: "What is needed to view video on frontend?"
date: 2008-05-22
forum: Mythbuntu
---

### Post by bogoliubov on 2008-05-22
If I have a frontend separate from the backend, how do I watch video or play music? Do I need to mount the folders of the backend (with NFS, SAMBA or similar), or will it work automatically? 

What about if I want to use a UPNP device as a frontend? I'm thinking of buying a Pinnacle Showcenter 200, to listen to music and watch video (not just TV recordings!) from the backend...

---

### Post by volkswagner on 2008-05-22
Yes you have to create a mounted share on the frontend.  NFS or Samba.  You will change the frontend video location to the mounted share.

This has a simple how to, just to get you started.

[http://ubuntuforums.org/showthread.php?t=799297]("http://ubuntuforums.org/showthread.php?t=799297")

---

### Post by bogoliubov on 2008-05-23
Well, I know it's not very difficult to set up (though I'd prefer sshfs); but it kind of spoils the point for me to have mythtv for this purpose, since I want to use a UPNP device as a frontend.

---

