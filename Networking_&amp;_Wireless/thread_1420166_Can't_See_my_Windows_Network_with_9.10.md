---
title: "Can't See my Windows Network with 9.10"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by mauprice on 2010-03-02
I have 2 ubuntu servers, one is running 9.04 and the other has been upgraded to 9.10 but the 9.10 server no longer browses or connects to the windows network, but the 9.04 server sees the windows network fine.

I have checked the smb.conf file against the 9.04 server which has the same configuration as the 9.10 server. 

It's strange that the 9.04 version server is working perfectly and the latest version 9.10 is not.

any suggestions would be appreciated.

---

### Post by jruberto on 2010-03-02
```
sudo /etc/init.d/samba restart
```It seems I need to bounce the samba service before I can get anything to work at all, even after a fresh restart.  Try it.

---

### Post by mauprice on 2010-03-02
I restarted the samba server but it is still unable to see the network.

it gives the error message from Nautilus as 

Unable to mount Location 
Failed to retrieve share list from server.

the strange thing is it is working perfectly on the other server under 9.04 with the same conf.

---

### Post by jruberto on 2010-03-02
There's a lot of stuff to try here & some posts near the end that seem somewhat authoritative.  Good luck.

[http://ubuntuforums.org/showthread.php?t=1082148](http://ubuntuforums.org/showthread.php?t=1082148)

---

### Post by Iowan on 2010-03-02
Anything in [this]("http://ubuntuforums.org/showthread.php?t=1169149") one help?

---

