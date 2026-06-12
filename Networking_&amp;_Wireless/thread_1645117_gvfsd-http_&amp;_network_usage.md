---
title: "gvfsd-http &amp; network usage"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by stlucifer on 2010-12-14
Hi everyone,
today i noticed something weird in the system monitor, i was constantly uploading something at 60kb/s (wich is pretty much all my bandwith) with no reason.

after some research and some trial & error i figured out that the responsible was the process **gvfsd-http**

i killed it and now everything seems to works fine, but i'm not sure if it's really ok to just kill it. i think it exist for some purpose right?

anyone knows what gvfsd-http is needed for? and why it uses all my bandwith?

thanks everyone!

PS: i'm on ubuntu desktop 10.10 update from 10.04

---

### Post by puppywhacker on 2010-12-14
gvfsd-http is GNOME Virtual File System. I think the http part refers to a mounted filesystem for WebDAV. It's for sharing documents over a network

It may have some CPU or Memory issues, especially for bigger files. It's memory usage might choke your computer, or it may constantly synchronize files. finding the share and unmounting it should help more than killing it. Ubuntu runs fine if you kill it, but you run the risk of file corruption towards the http server it is sync'ing with.

---

### Post by stlucifer on 2010-12-15
thanks for the insight!

after a while the process came back, without the anomalous network usage

it seems that the problem occur only when it first starts after system boot

i don't have any local network share mounted, but i have ubuntu one and dropbox set up, do you think it may be one of those services?

---

