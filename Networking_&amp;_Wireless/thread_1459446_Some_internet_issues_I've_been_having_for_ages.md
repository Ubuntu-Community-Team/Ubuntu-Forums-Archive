---
title: "Some internet issues I've been having for ages"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by I Dunno on 2010-04-21
I've been having 2 issues with my internet connection on ubuntu for as long as I can remember, I've tried updates but they haven't seemed to work so great and am pretty fed up with this.

So I have a Netgear wg111t wireless usb dongle which I got working through ndiswrapper. The 2 issues I am having are:

1. after a random period of time my internet just decides to disconnect, the strange thing is the bars at the top still say I'm connected. The only way to get the internet working again is to turn the pc off and on. Another way I have experienced this happening is usually when I'm downloading something off a torrent.

2. This problem isn't so bad, just a little annoying: after restarting my pc the wifi usb isn't recognised and i can't connect to the internet

Someone please help it would be greatly appreciated as I have been having these problems for at least more than a year

---

### Post by ciaopaulo on 2010-04-21
According to...

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WG111T](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WG111T)

you need to install two sets of .inf and .sys files.

Have you tried that?

---

### Post by I Dunno on 2010-04-22
My cd only seems to have come with one set of inf and sys which is netwg111t. 

There is another inf file called autorun but trying to install that gives the message "error while installing" and "invalid driver!"

---

### Post by I Dunno on 2010-04-22
I was wondering if I should use the netgear drivers that the link you put up was providing, maybe they work better with ubuntu? Im not too sure

---

### Post by ciaopaulo on 2010-04-22
Those are the drivers that the developers are saying they used to get it to work, so yes I'd try it.

---

### Post by I Dunno on 2010-04-23
no dice, the other drivers don't work at all. The problems I have are really inconsistent sometimes I stay connected for a very long time even when downloading from a torrent, other times I get disconnected in a short amount of time. It tries reconnecting but fails and then asks me to re-enter my WEP code and tries connecting again only to ask for my code and so on...
:(

---

### Post by I Dunno on 2010-04-23
What is the best internal wireless network card for use with Linux, is there anything that works with most variations of Linux straight out of the box without having to deal with weird driver issues.

---

