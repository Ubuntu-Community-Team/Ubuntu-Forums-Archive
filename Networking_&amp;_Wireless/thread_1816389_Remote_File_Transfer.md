---
title: "Remote File Transfer"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by biggiee on 2011-08-01
Hello.
I am trying to set up a computer so that I can remotely torrent files and then transfer the files to my PC while I am at college. 
I set up my computer so that it has a dynamic dns as well as hosting via DynDns. 
I have recently hit a wall when trying to find a way to transfer my files from the computer at home to my Windows 7 computer at school.

Any advice and thoughts would be greatly appreciated,
Thanks!

---

### Post by CyberPingU on 2011-08-02
And where are you? 
You have physical access to which machine when you attempt the transfer?

---

### Post by biggiee on 2011-08-02
I am going to be on the windows machine @ coolege

---

### Post by CyberPingU on 2011-08-02
> I am going to be on the windows machine @ coolege

So you can use:
- ftp server on your home linux;
- ssh server on your home linux (you can use pscp as if it was ftp: just look for putty on the net);
- use OpenVPN;
- if you're blocked by a proxy you have to run your ssh server on the port that the proxy uses. For example if all you can do is surf the internet, then check the proxy settings: if it's on port 8080, then let the ssh server run on that port.

By the way... won't it be better an usb key?

---

### Post by biggiee on 2011-08-02
i am going to assume i am blocked from a proxy since i could not torrent on any port the last semester. 
Thanks for the advice, i will get learning how to do that.

---

