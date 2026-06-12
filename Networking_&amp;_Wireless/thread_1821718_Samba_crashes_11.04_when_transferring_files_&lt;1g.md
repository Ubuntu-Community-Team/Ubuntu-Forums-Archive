---
title: "Samba crashes 11.04 when transferring files &lt;1gb"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by Kezspez on 2011-08-09
I'll preface this by saying I'm a total cheap ***.  

I've got a quadcore PC, 2gb ram pc running ubuntu 11.04 with samba set up on a shared folder - the plan is to share files and media between myself and my housemates. However, I do not have the router attached by ethernet, I am connecting to the router (in another room) by a d-link wireless dongle. 

I can access the share without real issue from my windows  laptop and other computers in the house share I'm part of, and I can happily transfer a text file here and there, but it seems to be anything over 20mb will not go. All the files I am trying to transfer are >1gb and it's driving me mad.

After some decent transfer rates of around 1mb per second it just freezes up. The screen attached to the actual server goes blank and the host becomes unreachable by ping.

I'll be happy to provide any command results or anything to get this working. any assistance would be welcome!

---

### Post by hymerman on 2011-08-09
I'm getting a similar thing. Browsing the samba share using a Windows 7 PC, and doing anything involving a lot of writing (e.g. copying from the Windows machine to the share, or copying files from one place on the share to another) locks the Ubuntu machine up completely; can't connect to it via ssh, samba, web etc, and the screen freezes seemingly indefinitely. I'm on 11.04 too.

I can't see anything suspect in any logs.

In my case, the directory being shared is a RAID 5 array. I was just about to say it's healthy, but I just checked /proc/mdstat and that reports it's resyncing. The hard reset from the last lock up probably didn't help.

---

### Post by WilhelmT on 2011-10-03
I have something that seems related to this
I have a Ubuntu Server running Samba and when I access the share with my Windows 7 laptop or MacBook the router often crashes. I then need to reboot the router.

I disabled the dhcp on the server and made the IP address static (outside the dhcp range of the router) and it improves, but doesn't fix the problem completely.

---

