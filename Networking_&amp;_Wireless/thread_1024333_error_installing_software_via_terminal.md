---
title: "error installing software via terminal"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by abhinav.p on 2008-12-28
my dell laptop has gytsy installed on it.my network is wireless provided by university with sufficient speed.my problem is whenever i try to get some software ,say vlc from the terminal,it spits some lines untimately terminating at "unable to resolve PROXY ADDRESS".what does this mean?.when i am able to connect to net normally all the time,why does terminal connection giving me trouble?u  know how installing downloaded deb files keep bothering u about dependencies.my last attempt of installing vlc required me to download 7 deb dependencies and the 8th one some "dvdread4" required dvdread4 itself as dependency!!!i had to terminate my attempt there.same thing happened before with dbus.
someone help.all my applicatins need updates!!!!!!!

---

### Post by anubhavrocks on 2008-12-28
I think you haven't exported http_proxy.You can try this out in the terminal:

```
export http_proxy=http://host.com:port/
export HTTP_PROXY=http://host.com:port/
```

Offcourse host.com:port should be replaced with your proxy servers IP and port.

Also try Synaptic.

---

### Post by abhinav.p on 2008-12-30
thanks it worked but now it says "ldconfig deferred processing now taking place"...what does it mean??(while installing mplayer)

---

