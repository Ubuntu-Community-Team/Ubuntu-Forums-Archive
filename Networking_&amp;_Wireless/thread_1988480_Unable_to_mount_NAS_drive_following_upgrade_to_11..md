---
title: "Unable to mount NAS drive following upgrade to 11.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by andy_acacia on 2012-05-27
I recently added a NAS to my network in 10.04
The installation ran pretty simply, following the instructions that I managed to find here [http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

For a few days I was able to play movies and music directly from my DLNA connected TV. Subsequently I have upgraded to 11.04 and the network drives no longer mount.
When running **sudo mount -a** I get the following error message:
**[COLOR=Red][COLOR=Black]Unable to find suitable address*.*[/COLOR][/COLOR]**

I have tried altering the /ect/fstab to include the IP but have reverted to the name of the NAS as this is what previously worked. Neither the IP or name works.
My fstab contains the lines at the bottom: 
# Mount our network drive
//IX2-200-TIIU4H/Movies //media/Video smbfs smbguest 0 0
#//192.168.1.71/Movies //media/Video smbfs smbguest 0 0

What am I doing wrong??? I have spent most of a sunny weekend indoors getting nowhere. Please can somebody help. It would be greatly appreciated.

My apologies if what I have posted here is insufficient or does not make sense. I try to learn as I go along but am finding open source challenging.

---

