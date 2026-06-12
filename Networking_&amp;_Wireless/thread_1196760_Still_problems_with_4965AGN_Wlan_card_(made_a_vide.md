---
title: "Still problems with 4965AGN Wlan card (made a video of it)"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by andlinux on 2009-06-25
If I start my laptop then most of the time there is no internet connection because the wlan card couldn't connect to my router. So I have to do some things to let it connect.

Here is my video: [http://www.youtube.com/watch?v=ads5jhOZB-A](http://www.youtube.com/watch?v=ads5jhOZB-A)

If somebody know how to fix this, please let me know.

---

### Post by philcamlin on 2009-06-25
try unplugging and replugging in your router 

thats a hard reset and should correct any connection issues :popcorn::popcorn::popcorn:

that happened with my belkin 54g a few years back

---

### Post by andlinux on 2009-06-25
> **philcamlin said:**
> try unplugging and replugging in your router 

thats a hard reset and should correct any connection issues :popcorn::popcorn::popcorn:

that happened with my belkin 54g a few years back
Well, I already tried that and I even bought another modem/router, but I still got this problem.

---

### Post by Melk79 on 2009-06-25
I can at least tell you you're not alone.  It doesn't happen to me everytime I open my computer, but enough to make it frustrating.  There always seem to be some connection troubles, but there are so many elements in play it makes it tough to figure out.  Hopefully, someone else may know.  Cheers.

---

### Post by wirelessmonkey on 2009-06-26
I use Kubuntu, so your mileage may vary.

I don't have problems with my4965agn, unless I hibernate or sleep my laptop.  When I do, wireless is gone, and the 4965 module has unloaded. To fix the problem, I do this (a la terminal):

```
 
sudo modprobe iwlagn
sudo /etc/init.d/NetworkManager restart
sudo /etc/init.d/NetworkManager restart

```

I always restart NM twice, because it doesn't always associate with my network automatically on the first restart, and I'm far too lazy to click the menu.


Best of Luck

---

