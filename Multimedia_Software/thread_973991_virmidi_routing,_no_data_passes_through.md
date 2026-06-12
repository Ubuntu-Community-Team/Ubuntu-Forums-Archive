---
title: "virmidi routing, no data passes through"
date: 2008-11-07
forum: Multimedia Software
---

### Post by oedipuss on 2008-11-07
I'm trying to use the alsa virtual midi ports.
The module loads fine, jack shows all ports properly, but I can't see any data passing through any connections I make in qjackctl.

For instance, I have a midi app sending stuff to virtual port 0, which I can see with 'amidi -p hw:2,0 --dump' . The application is indeed sending midi data to the right port.
When I connect this port to virtual port 1 for instance, using qjackctl, and do a 'amidi -p hw:2,1 --dump' there's nothing passing through .. 

I tried connecting the two ports with aconnect too, but I think that's exactly what qjackctl does anyway.

Am I doing this wrong ? Shouldn't I see data from hw:2,0 in hw:2,1 after I connect those two ports ?

---

### Post by raboofje on 2009-01-24
I seem to be having the same issue: when I connect vkeybd to a virmidi on one end, and kmidimon on the other, my vkeybd keypresses don't show up in kmidimon.

I pasted my aconnect configuration at [http://pastebin.com/m1bafc777](http://pastebin.com/m1bafc777)

---

