---
title: "Nebook remix file share problems"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Stephen Shellard on 2009-11-03
I have recently purchased a Dell Mini 10 with the  ubuntu 8.04 netbook remix.  

I am trying to share files via my wireless network with my Zoostorm computer which I have just upgraded to Karmic Koala.

There is also a computer in the house running Windows XP.  For this reason I am using Samba to permit file sharing between all of these computers.  

I have set the share options on the folders I wish to share on each of these computers. This was straightforward. However I would make the following observations:

At the outset shared files appeared only intermittently on the network - more often not - for example, on my Zoostorm KK computer when trying to access Places/network.  

The Windows XP share has appeared fairly consistently on both my KK computer and the Mini 10 - but is of least interest to me.

On the Dell Mini I can only access my Zoostorm KK shares  consistently via Nautilus by entering the pathname: SMB://192.168.0.2/sharename/.  This also incidentally displays a folder  "print$" , which I have not shared and the significance of which I do not know.  

This could be quite acceptable but I would also like to be able to access the shares on my Dell Mini from the Zoostorm KK computer but am completely unable to do so, even when entering the [fixed] ip address in nautilus together with the sharename -     smb:192.168.0.3/DELLDOCS/   [As already observed, this procedure seems to work fine the other way round.]

I have attempted to mount this Dell Mini share directory from my Zoostorm KK computer but would admit to being very uncertain of the code and paramters.  Here is one of my attempts:

stephen@zoostorm:~$ sudo mount ext3 smb://192.168.0.3/  /media/dellmini/

Perhaps I should upgrade the Dell Mini to Karmic Koala?  I have only an 8GB SSD on it.

Any advice gratefully received.

---

