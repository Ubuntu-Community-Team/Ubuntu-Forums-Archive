---
title: "UPnP media sharing?"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by christianxxx on 2007-12-23
I've been playing around with different solutions for UPnP media sharing, but I just can't find a complete setup which both looks good and works great.

I've tried the following:
- Intel Tools for UPnP (server/controller/renderer). Windows. Works nice, but slow indexing.
- Cidero (controller). Linux. Works nice, but everything is slow due to Java.
- VLC. Linux. Just couldn't find out how to do it.

I've heard that MediaTomb is supposed to be great, but I don't know what to expect, and since there is no .deb yet, I was kind of put off by the extremely long howto.

Also, I know that MediaPortal 2 (windows) is going for a server/renderer setup, although I'm not sure  if they're going to use UPnP.

As this seems to be the way for media sharing, and media sharing is really something I want to explore for my multiple computers setup at home, I sure would like to know if there's something I've missed, or if I just have to sit and wait. (No, I'm hardly a developer myself, so creating it on my own is  really not an option)

Anyone?

---

### Post by adelodder on 2007-12-23
What are you trying to do exactly?

If your are looking for a Media Center solution with UpnP support, I advice you to have a look at:

[http://xboxmediacenter.com/forum/forumdisplay.php?f=52](http://xboxmediacenter.com/forum/forumdisplay.php?f=52)

It's the best.

The Linux port is still in an Alpha fase.

I have it running on my system.

Hope I was of any help.

---

### Post by christianxxx on 2007-12-24
> **adelodder said:**
> What are you trying to do exactly?

.


That is actually a really good question. I guess I want to be able to view any media, from different UPnP enabled sources, on a single computer hooked up to my tv and home theater.
I know there are other ways without UPnP, but from what I've seen, UPnP makes it quite easy once you have the software and hardware to support it.

XBMC might be a good solution, I'll have a look. Alpha and beta versions are fun, but for this I'm looking for a proper solution. The Windows solutions are not an option either as we've completly migrated to Ubuntu. 


Christian

---

### Post by Existentialist on 2007-12-24
uShare is a command line based UPnP server for linux.  I've been using it to stream media to my 360 and it works well.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by christianxxx on 2007-12-24
> **Existentialist said:**
> uShare is a command line based UPnP server for linux.  I've been using it to stream media to my 360 and it works well.

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

Yeah, I've heard so too, but for some strange reason it insisted on using my eth0 interface even if I specified a different interface. I got GMediaServer working. It's pretty similar from what I understand.

So it's the client side left. The renderer/control point...

---

### Post by christianxxx on 2008-01-04
*bump*

---

### Post by ISNT on 2008-01-19
Another bump - I'm also looking for a upnp client.  Rythmbox will see my upnp music from my NAS and will list it, but it refuses to play any of the tracks....

---

### Post by gasparov on 2008-02-22
Stil didn't get what you want:


If you have content shared on some devices and you want to see it on your pc you need a mediarender, still have to find wich is the best but on debian you should have gmediarender (my desktop is on gentoo and there is no gmediarender in portage).The "Keep it simple stupid" solution is djmount, you mount the shared content from anydevice on your network ,i use it with my nokia n95. Then you can simply double click on it and read the file (or play the movie), maybe is not a stream.

If you want to share content from your pc so you can read it from other upnp media renders on your network (psp, xbox ecc ecc)  you have many choices, ushare the simple and the one I'm gonna try cause is said is the best:mediatomb.

---

