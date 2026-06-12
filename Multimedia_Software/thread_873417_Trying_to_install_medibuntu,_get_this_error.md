---
title: "Trying to install medibuntu, get this error:"
date: 2008-07-29
forum: Multimedia Software
---

### Post by jusayo on 2008-07-29
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread 8.1.2-0medibuntu6.2
  404 Not Found [IP: 87.98.249.30 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread-escript 8.1.2-0medibuntu6.2
  404 Not Found [IP: 87.98.249.30 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free acroread-plugins 8.1.2-0medibuntu6.2
  404 Not Found [IP: 87.98.249.30 80]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6 [151kB]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free mozilla-acroread 8.1.2-0medibuntu6.2
  404 Not Found [IP: 87.98.249.30 80]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6 [292kB]
Fetched 443kB in 2s (212kB/s)      
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu6.2_amd64.deb)  404 Not Found [IP: 87.98.249.30 80]
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu6.2_amd64.deb)  404 Not Found [IP: 87.98.249.30 80]
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu6.2_amd64.deb)  404 Not Found [IP: 87.98.249.30 80]
Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.2-0medibuntu6.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.2-0medibuntu6.2_amd64.deb)  404 Not Found [IP: 87.98.249.30 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What exactly does all of this mean?  It won't install, and I don't know any workarounds on Ubuntu as of yet.  Help?

---

### Post by aysiu on 2008-07-29
Looks as if something is wrong with your internet connection *or* Medibuntu's server.

---

### Post by kpkeerthi on 2008-07-29
404 means file not found. Click on [http://packages.medibuntu.org](http://packages.medibuntu.org) in Firefox and see what happens.

---

### Post by dether on 2008-07-29
Same over here :-(

If I direct my browser to [http://packages.medibuntu.org](http://packages.medibuntu.org) I'm redirected to [http://www.eric-beuque.com/freetuxtv/blog/](http://www.eric-beuque.com/freetuxtv/blog/). But if I browse to [http://packages.medibuntu.org/dists/hardy/free/binary-amd64/](http://packages.medibuntu.org/dists/hardy/free/binary-amd64/) directly, I am able to download the file Packages.gz manually.

Nevertheless wget doesn't work.

---

### Post by smooth3006 on 2008-07-30
it gave me that 404 error for a few days as well. seems to be ok now though. must of been a server issue ?

---

