---
title: "Torrent software suggestion"
date: 2018-03-31
forum: Multimedia Software
---

### Post by moto1860 on 2018-03-31
Which one should I use? I'd like to keep on using uTorrent, on their website there's a version for 13.04 that I assume would run on latest version. How do I install it once downloaded the tar.gz file?

---

### Post by SeijiSensei on 2018-03-31
I've used Transmission, Deluge, and KTorrent (I use KDE) at various times. Most of the time I stick with Transmission.  All of them are in the repositories.

---

### Post by Yellow Pasque on 2018-03-31
Isn't ubittorrent browser-based nowadays? I wouldn't touch it since it went to paid versions and ads. qbittorrent or Transmission for me.

> How do I install it once downloaded the tar.gz file? 
There's no "one size fits all" answer. You need to follow the instructions included with the software.
Anyway, I would not try and download/install a 5 year old tar.gz, especially if you're not comfortable with building software in the terminal. It probably has old dependencies that will cause you grief.

---

### Post by moto1860 on 2018-03-31
Thanks, I went for Transmission and installed but it's not downloading the files, network settings are as follows:

[IMG]https://image.ibb.co/dUkyaS/Screenshot_from_2018_03_31_22_40_19.png[/IMG]

---

### Post by moto1860 on 2018-03-31
Ok that Port is closed, this si gonna be tough as I don't know admin and pass to this router....

do I have to allow for remote access?

---

### Post by SeijiSensei on 2018-04-01
I don't have any ports open, and Transmission still works fine for downloading.  It will upload during the session as well, and to peers found during the session for a while after that. I have two NAT routers between my computers and the Internet, too.

---

### Post by moto1860 on 2018-04-01
What else could be the reason for torrents stalling (never even started to be more precise)? Sorry, just used to launch uTorrent in win and all's fine althought the ports test need to be positive (that was my understanding).

---

### Post by Yellow Pasque on 2018-04-01
You should try with a torrent that is known to have a ton of peers (like the Ubuntu 16.04 iso): [http://releases.ubuntu.com/16.04/ubuntu-16.04.4-desktop-amd64.iso.torrent](http://releases.ubuntu.com/16.04/ubuntu-16.04.4-desktop-amd64.iso.torrent)

> Sorry, just used to launch uTorrent in win and all's fine

Well, what port settings do you use there?

---

### Post by moto1860 on 2018-04-01
Well... now I feel dumber than ever. As suggested by Temujin it was a peers issue not the software settings. At least I've learned ports not need to be open for torrent client to function.

---

### Post by Yellow Pasque on 2018-04-01
Having port forwarding set up correctly will help you get more peers and may be the difference between getting a torrent or not being able to find any peers.
But... if you don't have control over the router, there's not much you can do except check the UPnP/NAT-PMP box and hope the router cooperates.

Please mark the thread solved.

---

