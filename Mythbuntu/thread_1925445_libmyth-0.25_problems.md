---
title: "libmyth-0.25 problems"
date: 2012-02-14
forum: Mythbuntu
---

### Post by williammanda on 2012-02-14
I just updated to the latest master via mythbuntu repos and libmyth-0.25 won't install due to libmyth-0.24 is using a file that is needed.

E: /var/cache/apt/archives/libmyth-0.25-0_2%3a0.25.0~master.20120214.dcfe7b0-0ubuntu0mythbuntu4_amd64.deb: trying to overwrite '/usr/lib/libmythavformat.so.52.101.0', which is also in package libmyth-0.24-0 2:0.25.0~master.20120212.5942398-0ubuntu0mythbuntu4

Any ideas?

---

### Post by williammanda on 2012-02-14
On the advice of the mythtv-users list I removed the libmyth-0.24-0 files but it also removed several other packages (mythbackend, common, etc...). I re-installed them via the mythbuntu control centre. Everything seems to be working but videos. I first came a cross the problem when scanning for videos. After selecting "m" then scan for changes, I get an error, Failed to scan SG video hosts, then the host name of the backend. I went and checked to video directory, /var/lib/mythtv/videos and videos are there and work in vlc. I went into mythbackend and checked SG's video entry and it was /var/lib/mythtv/videos. Upon exiting mythbackend I get an error that there isn't /var/lib/mythtv/videos and do I want to correct it.
Please advise.
Thanks

---

### Post by nickrout on 2012-02-15
This is NOT the place to get advice on running master. Go to the -dev mailing list.

---

### Post by williammanda on 2012-02-15
> **nickrout said:**
> This is NOT the place to get advice on running master. Go to the -dev mailing list.

If it is packaged by Mythbuntu then it is.

---

### Post by nickrout on 2012-02-15
> **williammanda said:**
> If it is packaged by Mythbuntu then it is.


No, there are very few myth developers here. The developers are continually telling people to subscribe to -dev and -commits and to read them and to expect breakages and that the code is experimantal. You are a tester. Subscribe to the required mailing lists and ask there.

---

### Post by williammanda on 2012-02-15
> **nickrout said:**
> No, there are very few myth developers here. The developers are continually telling people to subscribe to -dev and -commits and to read them and to expect breakages and that the code is experimantal. You are a tester. Subscribe to the required mailing lists and ask there.

I did subscribe and did post this on mythtv-users but to help others out here I wanted to alert them of the potential problem of the latest update. Also again, this is the official Mythbuntu forums so Mythbuntu problems are to be reported here.

---

### Post by azmyth on 2012-02-15
I would probably uninstall 0.24 and then install 0.25 versus updating 0.25 over 0.24.

---

### Post by williammanda on 2012-02-15
Mario stated on the mythtv-users list that another mythbuntu package update was coming soon. I will try that update.

---

