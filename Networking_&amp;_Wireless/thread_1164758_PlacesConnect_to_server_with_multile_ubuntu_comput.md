---
title: "Places/Connect to server with multile ubuntu computers"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by michael37 on 2009-05-20
For almost two years, I've had a great home networking set up with my Ubuntu Desktop double-tasking a file server.  Samba works great for sharing with other computers, mostly Windows laptops around the house.

I just passed a critical point: I now have more Ubuntu laptops than Windows laptops at home.  So, I am trying to find a better way to do networking sharing than Samba shares.

Here is what I tried.  Going to Places/Connect to server, both SFTP and Windows Share work.  Performance over both is rather slow.

My preference for performance is NFS.  Nautilus doesn't seem to support it.  Performance is great, esp for video streaming, but the setup is all command line and awfully annoying esp since laptops go outside of the house.  That excludes anyone by myself from using NFS.  Is there a graphical support for NFS as a remote resource?

Are there better options?

---

### Post by dmizer on 2009-05-20
What about FTP? Take a look at the fifth link in my sig. Just because FTP is primarily thought of as a WAN file sharing protocol, doesn't mean it won't work perfectly well over a LAN.

---

### Post by michael37 on 2009-05-20
> **dmizer said:**
> What about FTP? Take a look at the fifth link in my sig. Just because FTP is primarily thought of as a WAN file sharing protocol, doesn't mean it won't work perfectly well over a LAN.

Indeed, I haven't considered FTP.  What's your experience with streaming video over FTP?

---

### Post by dmizer on 2009-05-20
It's at least as fast as NFS, and extremely portable. You can also use the "places" > "connect to server" function of Nautilus (it works much better with FTP than it does with samba). For streaming video and other media, some clients will be more difficult to set up (Windows) than others, but FTP has been a part of the network for so long that there are tools for any OS you could imagine.

---

