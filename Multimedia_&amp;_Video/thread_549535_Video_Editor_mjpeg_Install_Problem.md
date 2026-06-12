---
title: "Video Editor mjpeg Install Problem"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by ggordon on 2007-09-12
I'm running 64 bit Feisty and trying to install a video editor.  I tried to install several different editors and keep getting similar errors for all of them.  They all seem to be dependent on libmjpegtools0, libmjpegtools0c2a, and mjpegtools.  When I try to install I get errors like the following:

> E: /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_amd64.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0


It appears that libmjpegutils is contained in both libmjpegtools0 and libmjpegtools0c2a.  Do I have incompatible versions?  libmjpegtools0 is version 1:1.8.0-0.4   Do libmjpegtools0 and libmjpegtools0c2a need to be at the same version number?  Synaptic only lists one version for each package.  How do I get a different version if that is my problem?

---

### Post by ggordon on 2007-09-13
I found the solution.  Someone reported a similar problem as a bug (Bug #121131 in mjpegtools (Ubuntu)).  Daniel Chen responded that it was not a bug, but rather that the problem was likely due to getting libmjpegtools0 from a third party repository.  He then suggested trying `sudo dpkg -P --force-depends libmjpegtools0 && sudo apt-get -f install'.  I tried this and it fixed my problem.

---

