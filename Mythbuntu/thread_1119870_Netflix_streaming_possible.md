---
title: "Netflix streaming possible"
date: 2009-04-08
forum: Mythbuntu
---

### Post by 7bigjohn on 2009-04-08
I just found this [http://www.themediamall.com/playon]("http://www.themediamall.com/playon")

It's a upnp server that allows you to stream netflix movies through your network.  All you have to do is install it on a windows machine on you network and then add it as network resource in xbmc, boxee, xbox, or playstaion.  I just installed boxee in mythbuntu and it worked great!  It looked good too.  I'm not sure how to add a upnp source in mythbuntu though.

Just thought I'd share.

---

### Post by newlinux on 2009-04-08
I don't think you can add it to myth. Myth can be a UPnP server, but I think it only uses UPnP as a client for it's own backends (for autodiscovery). But good stuff nonetheless. I think I remember something about this working with DirecTV HR-20/21/22 boxes as well

---

### Post by Boppy3125 on 2009-04-09
Do you think there is any reason the windows machine couldn't be a virtual machine.  The only machine I have on all the time is my Myth backend.  I am contemplating installing a VM with windows just for kicks anyway.

---

### Post by newlinux on 2009-04-09
I can't say for sure, but I think it might work... Heck, I might actually try that when I get time... (I don't have a netflix account anymore though). I've already got a XP running in Virtualbox on one of my machines.

---

### Post by nickrout on 2009-04-09
> **newlinux said:**
> I don't think you can add it to myth. Myth can be a UPnP server, but I think it only uses UPnP as a client for it's own backends (for autodiscovery). But good stuff nonetheless. I think I remember something about this working with DirecTV HR-20/21/22 boxes as well

you can if you install djmount. It will act as a upnp client. something like this:

mkdir /var/lib/mythtv/videos/upnp
sudo djmount -o allow_other /var/lib/mythtv/videos/upnp

and allow browsing on videos in setup

---

### Post by 7bigjohn on 2009-04-10
Thanks.  I'll give it a try.

---

### Post by nrune on 2009-04-10
The only thing about this that, bothers me is what happens when hulu or netflix quits working.  Hate to spend $40, and then not have it working just a week later.

---

