---
title: "xbox xbmc"
date: 2009-02-15
forum: Mythbuntu
---

### Post by dontpntpool on 2009-02-15
Trying to get my mythtv box working with my xbox running xbmc. I installed the script but it cant connect to my mythtv box. I thought I read somewhere about some incompatibility with ver 9 of mythtv. Could someone point me to a fix.

---

### Post by nunrgguy on 2009-02-15
Are you using the script (if so which one?) or the myth:// protocol?
The old script no longer works.

---

### Post by The Odometer on 2009-02-15
The XBMC MythTV script no longer works. It worked for versions of MythTV prior to 0.21. MythTV is now at 0.21. However, XBMC does natively support the myth protocol. In my experience though (when using an Xbox)--it is choppy, at best. The easiest way to view recordings is via UPnP. I've had a good bit of success that way. The program data shows up and you just hit play. To set it up that way, you just add your Mythbox as a UPnP video source. You can also add the Myth protocol via adding video source. However, Live TV doesn't work very well, at all. (Granted, I am viewing over a wireless network, so you mileage may vary).

You can also use a Samba share--but you don't get the programming data that way...

Hope this helps.

---

### Post by jtpiano on 2009-03-14
I have my xbox working just fine.  I have an original xbox not a 360.  The video play back is smooth and no choppieness for me.  I am using myth ver .20-40b (Hardy Heron).  I am using XBMC script with a fairly recent t3ch build.  There was one script that needed updating.  Other than that it all installed easily.

---

### Post by rerobins on 2009-03-15
If you pull down the version that is in the XBMC svn repository it will work out of the box with version 0.21.  The version that is distributed will not work with .21.

---

### Post by nunrgguy on 2009-03-16
myth protocol is very choppy for me on an original xbox on live tv and none transcoded recordings but fine on anything transcoded. I've made several posts about it on the xbmc forum. It's nothing to do with overall network speed as the effect is the same whether I connect to the backend via Homeplug AV, Wireless N or cable, so the issue is either: speed of the Xbox NIC, Xbox CPU or the ringbuffer setting in DVD player. 

The mythtv side of things is fine and on my Linux HTPC everything works great in XBMC via Wireless N.

---

