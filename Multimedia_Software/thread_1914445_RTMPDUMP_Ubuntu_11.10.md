---
title: "RTMPDUMP Ubuntu 11.10"
date: 2012-01-24
forum: Multimedia Software
---

### Post by moltra1 on 2012-01-24
I use a program called serviio to stream my videos and online video sources to my TVs and other Devices. In order to stream RTMP sources I need RTMPDUMP 2.4 installed on my Ubuntu 11.10 computer. When I install RTMPDUMP and try to connect to an online RTMP stream I get a handshake error. I have researched this below is some information that I have been able to find about this. It looks like the wrong version of librtmp0 2.3 is getting installed instead of 2.4
 
> **"moltra"]There is a problem with Ubuntu 11.10 and RTMPdump. I compliled the RTMPdump from the serviio download page and still get the handshake error.
it is something about the dynamic library used. The below is from the hulu plugin thread. 
[quote="moltra"]Found this tried it and still handshake error
```
git clone git://git.ffmpeg.org/rtmpdump
cd rtmpdump
make
sudo make install 
But the resulting binary still failed with this error message:
 WARNING: HandShake: Type mismatch: client sent 6, server answered 9
WARNING: HandShake: Server not genuine Adobe!
ERROR: RTMP_Connect1, handshake failed. 
After a bit of digging it turned out that my new rtmpdump used the old dynamic library. I had to set the rpath of the new binary, so that it used the new version of the library. There are several ways to do this said:**
> 
here is more abotu the problem.
[http://lists.infradead.org/pipermail/get_iplayer/2011-October/002131.html](http://lists.infradead.org/pipermail/get_iplayer/2011-October/002131.html)
```
 Another thing to check: Make sure you upgrade the "librtmp0" package from
>> 2.3 (from Ubuntu repo) to the 2.4 version in the PPA.  I noticed that
>> librtmp0 2.3 is included in the base install for Ubuntu 11.10 desktop
>> edition (it wasn't in 11.04), and the package isn't automatically upgraded
>> when you install get_iplayer from the PPA.
>
> oh.  I thought I'd fixed that!  sorry.
I had a look at what I've done with dependencies, and I'm confused as
to why this breaks. Perhaps someone who knows ubuntu and/or debian
packaging better than I do can help.
In oneiric (11.10) librtmp0 2.3 is already installed courtesy of a
dependency from libcurl3-gnutls (though where the dependency comes
from shouldn't matter)
If you then add my ppa and install get_iplayer, this depends on
rtmpdump, which in turn depends on librtmp0.  get_iplayer calls for
2.4 or later of rtmpdump, and this gets installed (2.4-something is in
the ppa), but people are reporting that librtmp0 doesn't get updated,
even though there's a newer version (2.4-something) in the ppa.
Any idea why?
Arguably rtmpdump 2.4 should depend on the same version of librtmp0,
but that's not the way its packaged in ubuntu anyway (all I did was
steal the existing packaging and update the source).  But it should be
ok, because the latest rtmpdump works with the latest librtmp0.
 
confused...
Jon

```
I just found this last information about librtmp0 and will have to try updating it tonight.
 
 
 
From this link [http://forum.serviio.org/viewtopic.php?f=5&t=4645&start=10#p34821](http://forum.serviio.org/viewtopic.php?f=5&t=4645&start=10#p34821)
 
Any and all help would be apprciated.

---

### Post by sujoe on 2012-01-27
The team xbmc unstable ppa has a librtmp2.4+ from git that is working for myself with xbmc and rtmp addons. Before I upgraded to rtmp from this repo I was getting handshake errors.

---

