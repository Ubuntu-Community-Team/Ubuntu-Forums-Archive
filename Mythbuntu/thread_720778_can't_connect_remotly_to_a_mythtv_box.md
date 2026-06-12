---
title: "can't connect remotly to a mythtv box"
date: 2008-03-10
forum: Mythbuntu
---

### Post by lime4x4 on 2008-03-10
I need to remotley control this box. It was running version 7.10 mythbuntu vnc stopped working. so i upgraded to 8.04. I can atleast connect to the box thru terminal server client but as soon as i click on anything on the remote desktop vnc crashes. I can ssh into the box fine just can't use remote desktop. Any ideas?

---

### Post by TehSnarf on 2008-03-11
I had this same problem.. what fixed it for me was that I had to have actual physical control of the box with a keyboard/mouse plugged directly in, ran mythbuntu-control-centre, disabled/enabled the VNC service, restarted, and it seemed to be fine.

I did a few other things, but I think this is what resolved it for me.

---

### Post by Calash on 2008-03-11
If you have SSH enabled you can try 

ssh -X [ip or host name]

Then you can start mythbuntu-control-centre from a remote computer and use it's controls to get VNC up and running.

This works well on a wired connection, but from my understanding is not that fast over a wireless.  Still it should let you access the area needed to get VNC going again.

---

