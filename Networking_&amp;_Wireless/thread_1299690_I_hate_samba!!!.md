---
title: "I hate samba!!!"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by watchitman on 2009-10-24
I'm ready to put my fist through my screen. NONE of the howtos for sharing a folder work. I've googled and googled and they all say something differnt and NONE of them work! Does anyone REALLY know how to share a folder on a local network from one Ubuntu machine to another? ](*,)

---

### Post by swerdna on 2009-10-24
If you can finger the specific problem, we can give focused advice.


Meanwhile, while you're buying a replacement screen:P, these might be worth a read:
The segment: [Setting up a Samba Server (Browsing and Sharing)]("http://ubuntu.swerdna.org/ubulanprimer.html#server") shows how to make shares.
It's from this tutorial: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home or Office LAN/Network.]("http://ubuntu.swerdna.org/ubulanprimer.html")

For more advanced shares se this section: [Part II: Defining and Using File Shares (Services)]("http://ubuntu.swerdna.org/ubusambaserver.html#shares") which comes from this more advanced tutorial: [Ubuntu & Kubuntu -- HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html")

---

### Post by Iowan on 2009-10-24
> **watchitman said:**
>  Does anyone REALLY know how to share a folder on a local network from one Ubuntu machine to another?  Samba isn't the only - or even the best - way to share files between Ubuntu machines. Perhaps [NFS]("http://ubuntuforums.org/showthread.php?t=249889") would be more to your liking.

---

### Post by coffeecat on 2009-10-24
> **watchitman said:**
> NONE of the howtos for sharing a folder work.

You've obviously not come across this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Make sure you've covered all the points in dmizer's first post and you should be fine. I can confirm that this worked for me and I can browse shares Ubuntu > Ubuntu, Ubuntu > Windows, Ubuntu > MacOS, Ubuntu > LAN Fileserver, and all combinations thereof.

Oh, and check that yours is not a firewall issue.

You might want to check your firewall. A badly/wrongly configured one is the commonest share problem. In this regard, the default SMB rule in ufw/gufw **doesn't work**. If you've enabled ufw/gufw, the default SMB rule doesn't allow share browsing. If that's your problem, I can post a link to fix it.

Oh, and did I say to check your firewall? :p

---

### Post by ST3ALTHPSYCH0 on 2009-10-24
I always ask the stupid, basic questions (because that's the stuff I always miss my self). Did you set up any samba user accounts?

---

### Post by ikt on 2009-10-24
> **watchitman said:**
> Does anyone REALLY know how to share a folder on a local network from one Ubuntu machine to another? ](*,)

Right Click on X (X being the folder you want to share) > Sharing Options > Tick 'Share this folder' > Done


To be more specific,

Where is the complication happening?

---

