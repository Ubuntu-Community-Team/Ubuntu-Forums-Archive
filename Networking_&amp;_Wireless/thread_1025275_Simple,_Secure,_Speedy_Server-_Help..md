---
title: "Simple, Secure, Speedy Server- Help."
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by trashjunkid on 2008-12-29
I apologize in advance for my stupid questions.

I have a dell inspiron 530 quad core desktop that I wiped and made dual boot. There's windows xp home (what it shipped with) and ubuntu 8.04.

My intention all along was to have a desktop which could infrequently be used as a desktop (but ready and raring to go when called into service) and to almost always act as a server (hooked up to the printers, sharing external drives) to our home network.

As an aside, the principle computers in the house are laptops running windows xp and vista, though most of them dual boot as ubuntu- but they are run almost always in windows.

It's working, but barely. Following this post: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) , I have setup samba shares (which I admittedly only sort of understand) and I'm able to connect to the drives and the printer.

However, I use Adobe Lightroom to organize our photos. Whenever I fly through the photos (say, scroll rapidly through a few hundred photos) the network connection breaks. It happens with Adobe Lightroom, but it also happens when I open a folder on the drive, preview a photo there and rapidly page through the photos.

Second, the connection speeds to the drives are quite slow- I don't know how to quantify it. I know that if I plug the external drive directly into my laptop, It takes a few minutes to transfer a 4 gb file. If I do that over the network, it takes in the neighborhood of an hour. I have two external drives, both are slow over the network (one is vfat, the other is nfts). In addition, there are permission issues with 

The router in between this all is a linksys wrt160n- i have swapped out the original firmware for the appropriate dd-wrt firmware. (More about that at [http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices) )

What can I do to get a simple, secure, speedy network solution? I realize I have likely left some gaping information holes in this description, so please, please ask me for more relevant information.

Please help!

Trashjunkid

---

### Post by bgerlich on 2008-12-29
1. How is the machine connected to the router, wired, wireless ?

2. Do use the Lightroom on the server or on one of your laptops?

3. Does the connection break on both windows and linux?


Opinion: I think you are aproaching the whole thing from a wrong angle. A machine like your 4 core monster is too much for a home server. If I was you I would get a low power atom motherboard for 70$, an efficient power supply, stick in an old box and use that as server. It would be much quieter and much less power hungry.

---

### Post by trashjunkid on 2008-12-30
The server is wired to the router.

I use lightroom on the laptop and store the original photos on the server- so there's a small catalog on the laptop but any alterations or difference in zoom level when viewing the photos will result in the original photos on the server being accessed. Can I run Adobe Lightroom on the ubuntu server and use it from my windows or ubuntu laptop at the same time?

I will test to see if the ubuntu laptop accessing the photos causes breakage and report back.

In regards to your opinion: it certainly is overkill, but you'd think it would be easier to get the network going on a newer machine/hardware rather than older gear (my older gear was limping from severe age). Besides, I did get the desktop at a steeply reduced rate from dell outlet. 

Regardless, thanks for considering my problem- I look forward to more feedback and suggestions,

Trashjunkid

---

### Post by bgerlich on 2008-12-30
The testing procedure you should go through:

1. Test the same situation on Ubuntu desktop (your server) and laptop (wireless) with Gimp - if the application behavior is correct the problem lies in Lightroom, a bug (or "feature") possibly, try inquiring on the Adobe tech support forums, chats etc.

2. If the problem persists in Laptop - even on Ubuntu, but not on your desktop/server (XP and Ubuntu)  - the issue would be with your internet connection, some buffers or proxies enabled maybe...

Regarding your setup, if you need a powerful machine, you need a powerful machine ;) and if the noise or electricity bill doesn't bother you (the modern upper mid range systems can use up to 200W when idle!) than there is really no difference what equipment you use.

If above test cases won't help try to start some file transfer in the background and observe the netwotk transfer rate (whole network - not just the file transfer) while testing your app, does it drop/fluctuate ?

---

