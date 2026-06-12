---
title: "Terrible speeds when downloading torrents"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Jimmey on 2009-03-03
My torrents just won't download at full capacity, even when there's 1000+ seeding!

Using ktorrent on 64bit Ubuntu 8.10 with a BCM43XX card.

My speeds never seem to exceed 100kbps (normally around 20), where I have seen it reach upwards of 800.

I have port 41170 mapped with TCP and 41171 mapped with UDP from my router to my computer, and both ports open on my computer. Should the port numbers be the same at the router? Or should they be different values?

How can I speed things up?

---

### Post by whoop on 2009-03-03
The open ports on your router should match the ports your torrent client is using.

---

### Post by Cybie257 on 2009-03-03
Use this link (With Transmission OPEN)

[http://utorrent.com/testport.php?port=51000](http://utorrent.com/testport.php?port=51000)

with your port number (Replce 51000 in the link)

This will tell you if your port is forwarding ok.

-Cybie

PS. be sure you have Transmission settings to your open port

Edit->Preferences->Network On Transmission if you didn't already know. :)

---

### Post by cb951303 on 2009-03-03
you know 1000 seed means *nothing* if the leecher count is more than 1000, right?
what counts is the seed/leech ratio.

---

### Post by whoop on 2009-03-03
> **Cybie257 said:**
> Use this link (With Transmission OPEN)

[http://utorrent.com/testport.php?port=51000](http://utorrent.com/testport.php?port=51000)

with your port number (Replce 51000 in the link)

This will tell you if your port is forwarding ok.

-Cybie

PS. be sure you have Transmission settings to your open port

Edit->Preferences->Network On Transmission if you didn't already know. :)

He is using ktorrent. But your method works anyway; it is not client specific.

Jimmey: post the output of:
[http://utorrent.com/testport.php?port=41170](http://utorrent.com/testport.php?port=41170)

---

### Post by Jimmey on 2009-03-03
[quote=uTorrent Port Checker]OK! Port 41170 is open and accepting connections.

You will be able to receive incoming BitTorrent connections.[/quote]

I have the UDP ports forwarded aswell - Is there any specific settings I should check?

---

### Post by xtremethegreat1 on 2009-03-03
I think ktorrent is not very useful. Try using Deluge Bit torrent Client. Install it from Add/Remove Programs. It does not have any such issues.

---

### Post by SuperIntense on 2009-03-04
Is Dluge the file downloader fo chice? If so how do I get it

---

