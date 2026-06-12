---
title: "Mythbuntu Upnp issues"
date: 2008-10-01
forum: Multimedia Software
---

### Post by x20mar on 2008-10-01
Hi there,

I've recently setup a mythbuntu backend server to stream to by xbox 360, with a myth frontend planed at a later date.

Now my problem lies in that the xbox 360 doesn't see the media server at all. According to the mythtv wiki it should be seen via Upnp.

So I feel that I'm missing something completely obvious the files are stored in the video folder (produced by the video plugin)

Thanks

---

### Post by tgilber1 on 2008-10-01
Assuming that package dependencies are satisfied, make sure that the firewall on your Linux box or router is not blocking UPnP packets.  Use Wireshark, protocol analyzer, to verify that your linux box is sending and receiving UPnP packets from your xbox.  From wireshark, you should see packets with IP address 239.255.255.250 going between the two boxes.


> **x20mar said:**
> Hi there,

I've recently setup a mythbuntu backend server to stream to by xbox 360, with a myth frontend planed at a later date.

Now my problem lies in that the xbox 360 doesn't see the media server at all. According to the mythtv wiki it should be seen via Upnp.

So I feel that I'm missing something completely obvious the files are stored in the video folder (produced by the video plugin)

Thanks

---

### Post by mvillarejo on 2009-03-12
Hello! did you make it work??

---

