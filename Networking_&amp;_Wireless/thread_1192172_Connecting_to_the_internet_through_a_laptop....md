---
title: "Connecting to the internet through a laptop..."
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by wangusangus on 2009-06-19
I just purchased a new desktop, and realized once I received it that it doesn't come with a wireless adapter (silly on my part, I know).  I have a netbook, also running Ubuntu, and both for curiosity's sake and so I can begin setting up my desktop before I find an adapter, I'd like to set up my netbook so that I can connect my desktop to the internet using my netbook's existing wireless connection.  I know there's a way of doing this in Windows, but the tutorial I found only showed how to do it in Windows, and it seems it might not be as straightforward with Ubuntu (or it is, and I just don't get it).  Can anyone lend me a hand?

Please keep in mind I am not a computer whiz... I'll need pretty basic instructions, especially since I'm very, very new to Ubuntu, as well as Linux in general.

---

### Post by s3a on 2009-06-19
If you're asking to make the netbook share its internet connection with your desktop, you can achieve that using the (GUI) program called *firestarter* which can be obtained from the repositories. The wizard guides you through internet sharing. Although I have never done this myself, I can try to help you further if the wizard isn't straightforward enough for you.

---

### Post by RadarBat on 2009-06-19
I also have just gotten a netbook (Asus Eee 1000HE) that has wireless. I am somewhat familiar with Ubuntu, but I have never used wireless before. Is there a guide or a wiki page that tells how to use WiFi? Please point me that way.  Thanks,   Ben

---

### Post by s3a on 2009-06-19
_Radarbat:_
First step (to see if you have network-manager-gnome installed): **apt-cache policy network-manager-gnome**

---

### Post by RadarBat on 2009-06-19
Installed: 0.7.1~rc4.1-0ubuntu2
I checked in SPM and it is installed.

---

### Post by Iowan on 2009-06-22
[Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a How-To for internet sharing through wireless... but it may be "the wrong way around"

---

