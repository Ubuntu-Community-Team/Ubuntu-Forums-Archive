---
title: "IP range curiosity with a VM."
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by Mike_N on 2013-05-11
Hello all,

So I made a VM last night which I have done countless times before. I've always found that the VM adopted the same IP range as the host but not this time. Host was 192.168.1.10 while the VM was 10.x.x.x. I was able to ping the host from the guest but I couldn't ssh into the guest from the host. I googled it and then tried changing the network adaptor in Virtual Box to 'bridged' but there was no change. I then used ifconfig to assign it an IP of 192.168.1.66 and I was then able to ssh in. I assumed this was temporary so I rebooted the guest to test and when it came back up, it had an IP of 192.168.1.11. 

Can anyone explain this for me?

Thanks, Mike

---

