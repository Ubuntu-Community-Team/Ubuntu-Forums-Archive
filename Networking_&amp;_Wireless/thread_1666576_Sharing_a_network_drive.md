---
title: "Sharing a network drive"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by uberalles on 2011-01-13
Hello everyone
i'm new here, but i've been lurking for a little over a week and its been very helpful.

Here's my problem:
I have a Netgear WNDR3400 with a USB hard drive attached as a server. strictly media on th HD. i've been using it with my windows computers.
I recently picked up a Foxcon nettop to use as a HTPC. Installed Ubuntu 10.4 and XBMC. It seems to run fine.
HOWEVAH - i can't see the server or the other computers in the network. When i click on the icon i get the "unable to mount location: failed to retrieve share list from server" response.

I've disabled the home groups in windows and if i log into the router it shows the HTPC as a connected device. In fact, through my laptop i can see the HTPC as a media device (i enabled controlling with other computers in xbmc)
but windows does not recognize it on the network and i can't get to my server from the HTPC.

Any ideas?

thanks

---

### Post by blakep2 on 2011-01-13
Look into samba.

I had a similar problem last year.

---

### Post by uberalles on 2011-01-14
i do want to set it up as a samba server, but i assumed being able to access it first was more important. All my windows and mac machines can access it. the HTPC can't seem to get on the network (has internet access though)

this is my first experience with ubuntu and i'm in a little over my head.

---

### Post by uberalles on 2011-01-14
small update: i installed samba on the HTPC and i can see it on the windows network, but i can't get to the network through the HTPC. getting the same message.

feeling like i'm close....

---

### Post by uberalles on 2011-01-20
fixed it with this:

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

---

### Post by uberalles on 2011-01-20
fixed it with this:

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

---

### Post by uberalles on 2011-01-20
fixed it with this:

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

---

