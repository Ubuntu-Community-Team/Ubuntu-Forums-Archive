---
title: "Wireless Internet Dropping Out"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by dondiego2 on 2010-02-17
This is weird.  I will be working on the internet with several tabs open and all of a sudden  the pages won't update.  I can't go anywhere - it's like I lost the connection.  I am also downloading bittorrents with uTorrent running with WIne and that doesn't seem to be affected.  I also have gPodder and I tried to update podcasts with that and it also hangs up as if it can't connect. 

The only way I have been able to solve this has been to reboot (which I just did).  Any suggestions?

---

### Post by adam814 on 2010-02-17
Hmm...maybe with a few more details we'd have a better idea of what's really happening.  Is it a wired or wireless connection?  What NIC and driver are you using?

Do you get any messages when it happens?  Are pages actually timing out or is your browser just not responding?

The only thing I could suggest that *might* help without knowing any of those details is using Transmission or Azureus from the repos instead of uTorrent in wine.

---

### Post by dondiego2 on 2010-02-17
> **adam814 said:**
> Hmm...maybe with a few more details we'd have a better idea of what's really happening.  Is it a wired or wireless connection?  What NIC and driver are you using?

Do you get any messages when it happens?  Are pages actually timing out or is your browser just not responding?

The only thing I could suggest that *might* help without knowing any of those details is using Transmission or Azureus from the repos instead of uTorrent in wine.

I'm on wireless and using a Broadcom B43 Wireless Driver.  It appears to be when I'm downloading a torrent with uTorrent as it happened again after I posted but it eventually came back after waiting a bit.  

Right now I am not downloading any torrents , just uploading a few and it seems to be working fine.

No messages when it happens.  The wireless icon still says I am connected to my router.  The pages will just say loading for a while  and then can't connect.  I can close the browser (firefox) and then open it again trying to connect to Google and it still times out and says can't connect.  

I am using uTorrent because it is required on the private torrent site I am on.  Other torrent software will download but not upload from the site and you need to keep the upload to download ratio above a specific level or they boot you off.

---

### Post by adam814 on 2010-02-17
Well, I've heard of a lot of problems with the B43's, but if it's working without uTorrent running and not with that would tend to indicate a problem with uTorrent (or wine).

I'm not sure I follow about why other apps won't upload to their trackers.  I've used uTorrent before too, I didn't know it had any more functionality than other BitTorrent clients like that.

---

