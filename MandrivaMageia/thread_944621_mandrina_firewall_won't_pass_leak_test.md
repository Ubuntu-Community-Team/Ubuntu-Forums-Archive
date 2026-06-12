---
title: "mandrina firewall won't pass leak test ?"
date: 2008-10-11
forum: Mandriva/Mageia
---

### Post by smooth3006 on 2008-10-11
i ran a leak test at grc shields up and every port was stealth other than port 113, it was closed ? so i failed the test basically. how can i configure this to be a totally stealth system? 

also should i open a port for the transmission p2p application ?

---

### Post by smooth3006 on 2008-10-11
anybody ?

---

### Post by Antman on 2008-10-11
> **smooth3006 said:**
> i ran a leak test at grc shields up and every port was stealth other than port 113, it was closed ? so i failed the test basically. how can i configure this to be a totally stealth system? 

My default install was completely stealthed according to GRC. You may want to check that your security level is set to 'High' in the *Set Up Security Level and Audit* applet.

---

### Post by AdamWill on 2008-10-11
113 is set to closed because it's the identd port. identd was an ancient service for 'identifying' yourself. The reason to set it closed not stealth is that many IRC servers still look for a response on the identd port before letting you in. No-one runs identd any more, but IRC servers still look for it, for some bizarre reason. If you set the port to stealth, than when you try and log in to IRC it'll sit there for several minutes before the identd check times out and lets you in.

As antman says, I think if you raise the security level, it will change it to stealth.

and yes, it's probably a good idea to open a port for transmission. See what port it's set to use (you can see in its preferences) and open that port. If you use a router, you will also have to forward that port through the router to your system.

---

### Post by tommcd on 2008-10-11
> **smooth3006 said:**
> 
also should i open a port for the transmission p2p application ?

Try p2p without opening ports first, to see if it works. I have never opened any ports on my D-Link DI-634M router and torrents run just fine, even though Transmission reports that the default port it uses is closed.

---

### Post by AdamWill on 2008-10-12
Bittorrent will *work* with the upload port closed, but you won't get anywhere like the download speed you would get if it was open (it's set to penalize systems which aren't uploading properly).

---

### Post by Vulpus on 2008-10-13
> **Antman said:**
> My default install was completely stealthed according to GRC. You may want to check that your security level is set to 'High' in the *Set Up Security Level and Audit* applet.

My default install was also 100% stealthed, but now I am thinking about changing port 113 to open just to see how it affects the performance of KTorrent?

---

### Post by AdamWill on 2008-10-13
You're getting your signals crossed. Port 113 has nothing to do with Bittorrent :) To improve bittorrent performance you need to open whatever port you have your Bittorrent app set to listen on (which won't be 113), and you should also forward this port through your router to your PC, if you use a router.

---

### Post by Vulpus on 2008-10-13
You are correct, i am confused and bewildered!  I had a look at the KTorrent settings and the port is certainly not 113.  I think I will just walk away quietly and forget this conversation!

---

