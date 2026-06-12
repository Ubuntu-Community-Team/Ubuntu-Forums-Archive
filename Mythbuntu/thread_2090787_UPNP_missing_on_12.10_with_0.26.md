---
title: "UPNP missing on 12.10 with 0.26"
date: 2012-12-03
forum: Mythbuntu
---

### Post by odror on 2012-12-03
OS: ubuntu 12.10
mythtv version :0.26

After upgrading from 12.04/0.25 to 12.10/0.26 UNPN is no longer seen in my home network.

Yes in /etc/rc.local I have the following line

> route add -net 239.0.0.0/8 eth0 &

and route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default      MY_ISP 0.0.0.0         UG    0      0        0 eth2
MY_ISP_IP     *               255.255.240.0   U     1      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
239.0.0.0       *               255.0.0.0       U     0      0        0 eth0



There are no error in /var/log/syslog

Any ideas how I can debug it or fix it/

Thanks

---

### Post by nickrout on 2012-12-03
I was about to shoult out that there had been a thread regarding this in the mailing list recently...

But I think it was your thread :(

---

### Post by odror on 2012-12-03
> **nickrout said:**
> I was about to shoult out that there had been a thread regarding this in the mailing list recently...

But I think it was your thread :(

There was no much help in the mythtv mailing list. I think it is an Ubuntu issues. possibly a 12.10 only issue. I have had UPNP working for years. Now That android and media devices are UPNP compatible I do  not have it.

---

### Post by nickrout on 2012-12-03
Have you tried 12.04? Personally I would always go with LTS versions of ubuntu for mythtv boxes. In gact I think mythbuntu is only making ISOs for LTS versions now.

---

### Post by odror on 2012-12-03
> **nickrout said:**
> Have you tried 12.04? Personally I would always go with LTS versions of ubuntu for mythtv boxes. In gact I think mythbuntu is only making ISOs for LTS versions now.

I had no issue with 12.04/0.25. Did not try with 12.04/0.26. At this point I am committed to 12.10. I am looking for a way to identify the source of the problem.

---

### Post by nickrout on 2012-12-03
> **odror said:**
> I had no issue with 12.04/0.25. Did not try with 12.04/0.26. At this point I am committed to 12.10. I am looking for a way to identify the source of the problem.Oh and the services api is a far better way of getting your recordings onto android. Myth's UPNP does no transcoding so you get massive files that are unlikely to play well on android, with the services api the backend transcodes to h264 and serves up a HLS stream.

Of course yes, identifying the source of the problem would be good!

---

### Post by odror on 2012-12-03
> **nickrout said:**
> Oh and the services api is a far better way of getting your recordings onto android. Myth's UPNP does no transcoding so you get massive files that are unlikely to play well on android, with the services api the backend transcodes to h264 and serves up a HLS stream.

Of course yes, identifying the source of the problem would be good!
It was almost OK with the TF300 (better then iconia 500). I have a nexus 10 now. May be it will work for it. MY TV and the xbox have DLNA. I would like also to try xbmc instead of mythfrontend. Xbmc does not recognize the recordings without UPNP) At leas in my system it did not.

---

### Post by nickrout on 2012-12-03
> **odror said:**
> It was almost OK with the TF300 (better then iconia 500). I have a nexus 10 now. May be it will work for it. MY TV and the xbox have DLNA. I would like also to try xbmc instead of mythfrontend. Xbmc does not recognize the recordings without UPNP) At leas in my system it did not.XBMC 12 works with mythtv via at least three methods:

myth:// protocol
mythbox addon
XBMC's PVR support.

I put XBMC on my phone last night, very cool!

---

### Post by odror on 2012-12-03
> **nickrout said:**
> XBMC 12 works with mythtv via at least three methods:

myth:// protocol
mythbox addon
XBMC's PVR support.

I put XBMC on my phone last night, very cool!
Thank you. that can be a solution to my problem. If it works I can wait for UPNP on 13.04.

---

### Post by odror on 2012-12-10
> **nickrout said:**
> XBMC 12 works with mythtv via at least three methods:

myth:// protocol
mythbox addon
XBMC's PVR support.

I put XBMC on my phone last night, very cool!
I tried all three methods on xbmc 12. None woked.

myth:// did not connect.
mythbox addon is not compatible with mythtv 0.26
XBMC PVR support does not have the mythtv addon. PVR.cmyth

---

### Post by nickrout on 2012-12-10
> **odror said:**
> I tried all three methods on xbmc 12. None woked.

myth:// did not connect.
mythbox addon is not compatible with mythtv 0.26
XBMC PVR support does not have the mythtv addon. PVR.cmythWhich version of the mythbox plugin are you using? You need this one [https://github.com/mitchcapper/mythbox](https://github.com/mitchcapper/mythbox)

I compiled the pvr plugin, from some intructions I was given on the mythtv-users mailing list. [http://wiki.xbmc.org/index.php?title=PVR/Backend/MythTV/BuildFromSource](http://wiki.xbmc.org/index.php?title=PVR/Backend/MythTV/BuildFromSource)

Sorry I cannot establish if the myth:// protocol specifically works with 0.26, it does with 0.25. What are you putting into the url. From memory it is myth://mythtv:password@backend.ip.or.dnsname

---

### Post by odror on 2012-12-10
> **nickrout said:**
> Which version of the mythbox plugin are you using? You need this one [https://github.com/mitchcapper/mythbox](https://github.com/mitchcapper/mythbox)

I compiled the pvr plugin, from some intructions I was given on the mythtv-users mailing list. [http://wiki.xbmc.org/index.php?title=PVR/Backend/MythTV/BuildFromSource](http://wiki.xbmc.org/index.php?title=PVR/Backend/MythTV/BuildFromSource)

Sorry I cannot establish if the myth:// protocol specifically works with 0.26, it does with 0.25. What are you putting into the url. From memory it is myth://mythtv:password@backend.ip.or.dnsname
Actually I was not very specific. Non of these methods worked on my nexus 10 tablet. The PVR method only worked on the w7 client. The ubuntu machines use mythfrontend. I can wait for the sable xbmc. So my issue is the android tablet.

---

### Post by QA_manager on 2013-03-03
odror, you aren't the only one having this problem, and yes it also affects 12.04/0.26. I have installed a primary backend-only of 12.04 at least four times now, and UPNP is missing every time. I have been using MythTV since before Mythbuntu existed, so although I do make mistakes, I don't think I am making one this time.

Have you filed a bug report against 12.10?

Did you install a backend-only, or some other flavor?

How do we troubleshoot? What process should be running in order to create the UPNP service?

---

### Post by nickrout on 2013-03-04
> **QA_manager said:**
> odror, you aren't the only one having this problem, and yes it also affects 12.04/0.26. I have installed a primary backend-only of 12.04 at least four times now, and UPNP is missing every time. I have been using MythTV since before Mythbuntu existed, so although I do make mistakes, I don't think I am making one this time.

Have you filed a bug report against 12.10?

Did you install a backend-only, or some other flavor?

How do we troubleshoot? What process should be running in order to create the UPNP service?Are you using 127.0.0.1 or your lan address for the backend? uPnP is disabled if you use 127.0.0.1.

---

### Post by QA_manager on 2013-03-04
> **nickrout said:**
> Are you using 127.0.0.1 or your lan address for the backend? uPnP is disabled if you use 127.0.0.1.

No, having been using Myth since before Mythbuntu existed, I know to avoid that trap.

---

### Post by odror on 2013-03-04
> **nickrout said:**
> Are you using 127.0.0.1 or your lan address for the backend? uPnP is disabled if you use 127.0.0.1.
No I am using the local IP address

---

### Post by odror on 2013-03-04
> **QA_manager said:**
> odror, you aren't the only one having this problem, and yes it also affects 12.04/0.26. I have installed a primary backend-only of 12.04 at least four times now, and UPNP is missing every time. I have been using MythTV since before Mythbuntu existed, so although I do make mistakes, I don't think I am making one this time.

Have you filed a bug report against 12.10?

Did you install a backend-only, or some other flavor?

How do we troubleshoot? What process should be running in order to create the UPNP service?
I did not file a bug report.

I installed 0.26 from the PPA package. (in 12.10 0.25 is the default package) I have full version

---

### Post by QA_manager on 2013-03-04
> **odror said:**
> I did not file a bug report.

I installed 0.26 from the PPA package. (in 12.10 0.25 is the default package) I have full version

Oh, my mistake - I was thinking 12.04 had upgraded to 0.26 and I didn't go check.

So, back to my other question - who knows how to troubleshoot this? What process/demon should be running to provide the UPNP service? That is a good place to start.

---

