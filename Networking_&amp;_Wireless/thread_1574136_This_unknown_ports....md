---
title: "This unknown ports?..."
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2010-09-13
I did a port scan and found two additional ports open:

Port    State    Service
80    open    www
139    open    netbios-ssn
445    open    microsoft-ds
45690    open    unknown
58260    open    unknown

I can understand why the first three should be open, but what is the other two for? I would like to close this ports if their not being used?

---

### Post by gordintoronto on 2010-09-13
A Google search turned up this:
[http://www.speedguide.net/port.php?port=45690&print=friendly](http://www.speedguide.net/port.php?port=45690&print=friendly)

---

### Post by VcDeveloper on 2010-09-13
Thanks! Then, I will just keep these ports open for now...

---

### Post by MaindotC on 2010-09-14
Those ports are open on whatever access point you're connected to.  Usually those high ports are for torrent traffic.  If you have access to the AP I advise you log in and shut them off.

---

### Post by BkkBonanza on 2010-09-14
First, what did you scan and from where? Your computer from another computer on your LAN, your router from the internet, your gateway/router from inside the LAN - it makes a big difference to know what you scanned and from what direction.

If your computer was scanned then on your computer run **sudo netstat -lntup** to see what program is opening the ports. If your router was scanned then login to it and see if some service is enabled on those ports (or they're forwarded). 

If you don't have a reason to have them open then they should be closed. They may be for a torrent client or some other program like Skype but you should identify them before deciding what to do, or whether to ignore them.

---

### Post by VcDeveloper on 2010-09-21
> **BkkBonanza said:**
> First, what did you scan and from where?

I got cha! I was scanning within the same computer.  And, I scanned from another computer and didn't get the unknow ports!

Thanks!

---

