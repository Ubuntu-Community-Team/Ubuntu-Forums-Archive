---
title: "mythweb access out of network?"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-03-29
I was wondering how to get access to mythweb out of the network.  Today at work I tested to make sure my dyndns service was working by SSHing into the box with hans.dnsdojo.com and it worked.

I tried going to mythweb by typing [http://hans.dnsdojo.com](http://hans.dnsdojo.com)   and [http://hans.dnsdojo.com/mythweb](http://hans.dnsdojo.com/mythweb)
either of them didn't resolve.

I tried searching the documentation or forum posts about this but had no luck.  Anyone know how to do this?

Thanks for the help,
Hans

---

### Post by reclusivemonkey on 2007-03-30
Have you installed apache?

---

### Post by hansoffate on 2007-03-30
Yes.  I have access to mythweb IN my network.  Just when I am away from network, I want to be able to access it.

Any ideas?
Thanks for the help
-Hans

---

### Post by Monchanger on 2007-04-07
I just fixed this issue on my myth box.

The problem was that my ISP was blocking port 80, so I couldn't forward it through my router.  Making my web server listen to a second port to did the trick (this way the default port 80 still works inside my LAN, keeping my girlfriend ignorant of the tinkering and happy).

If you don't know what that all means, learn a little more about how the web works, specifically what a network port is (read [http://en.wikipedia.org/wiki/Network_port)](http://en.wikipedia.org/wiki/Network_port)).  After that, you're probably using the Apache web server, so seek relevant material on how to change the port number your web server is "listening on".  Then, make sure your router is capable of forwarding, and configure it to forward that port.  I'm a big fan of Netgear's MR814 series, though most home routers have this feature.

Please keep security in mind.  If you allow anyone access to your web server, they can really mess your computer up.

Good luck.

---

