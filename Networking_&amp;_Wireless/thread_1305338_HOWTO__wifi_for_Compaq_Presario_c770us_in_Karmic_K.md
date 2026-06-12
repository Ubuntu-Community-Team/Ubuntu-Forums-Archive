---
title: "HOWTO:  wifi for Compaq Presario c770us in Karmic Koala 9.10"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2009-10-29
This solution is for the Compaq Presario c770us and Ubuntu Studio 9.10 i386 32-bit Karmic Koala.  However, it should be applicable for any c700 series laptop with any 32-bit Ubuntu 9.10 variant.

You need to download and unzip the following file:

[indent][Atheros 5007eg drivers](http://www.mediafire.com/?sharekey=be3c593053b114b9d956df2962098fcb6d14ef878fe89961a2d0568e5b24962e)[/indent]

When that is done, go to synaptic package manager and install the following packages (plus all the packages that go with them):

```
ndisgtk
network-manager-gnome
```

Go to terminal (or hit ALT-F2) and run "gksu ndisgtk".  Add the driver you unzipped from the previous link.  Specifically, you want to point ndisgtk to the "ar5007eg-32-0.2/ar5007eg/net5211.inf" file.

Once you have done that, go find the network icon which should appear in the upper-right corner of the screen.  If you can't find the icon, you can create one by right-clicking on a panel and choosing "Add to Panel" > "Notification Area".

Use the network icon to connect to a wireless network.

That should do it!

---

