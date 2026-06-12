---
title: "Hauppauge PVR-150 together with HVR-950"
date: 2007-10-09
forum: Mythbuntu
---

### Post by dashmytv on 2007-10-09
I can get the Hauppauge PVR-150 to work fine in Mythbuntu 7.10.  No special procedures required and nothing else needed to be installed; it simply works.  I can watch live TV and record. The audio also works fine.  

For the HVR-950, I followed the directions from here:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)

The Hauppauge HVR-950 also works fine in Mythbuntu 7.10.  I can watch live TV and record. The audio also works fine.

Separately, the PVR-150 and the HVR-950 each work OK. Together, they don&#8217;t. I had the PVR-150 installed first. It was working fine. Then I installed the HVR-950.  After the installation, the HVR-950 works fine, but the PVR-150 no longer works.  

I've also installed the HVR-950 first, then the PVR-150.  It makes no difference.  I get the same results.

As the result of the HVR-950 installation, I&#8217;m certain the software for the HVR-950 has overtaken the PVR-150, but I don&#8217;t understand the HVR-950 installation procedure well enough to trace what happened. All I know for certain is that the PVR-150 no longer works, whereas it was working fine prior to the HVR-950 installation.

If anyone has the PVR-150 and the HVR-950 both working together in Mythbuntu 7.10, please post some hints about how this was done.

---

### Post by superm1 on 2007-10-10
As per that website you linked, the only solution listed was:

> pixelguy444 and Bigchris, the only idea I have come up with so far to resolve the issue (and it is not nearly an efficient one) is to install the hvr950 on one of your client computers (in other words, not on the master backend) and have the client computer also run as a slave backend. So you would have your pvr 1/2/350s on your master backend and have the hvr950 all by itself on your slave backends (which each could also have a front end of course).
 Not the prettiest resolution, but it should work.


My understanding of this problem is that the driver for the hvr-950 isn't compatible with the standard V4L tree.  The V4L developers wanted the person authoring the 950 driver to redo some things in the code to merge, but he never did it.  Instead he decided to fork V4L.

Really sad actually.

---

