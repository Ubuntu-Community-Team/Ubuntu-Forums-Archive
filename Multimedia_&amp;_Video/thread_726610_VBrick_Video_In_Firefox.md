---
title: "VBrick Video In Firefox"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by highflyer on 2008-03-16
So I've searched and searched for the answers to this all over the place but could not find a damn thing. On my campus, we have TVoverIP powered by VBrick's software. It works fine on Windows systems running firefox, but for some reason I can't get it to run on Ubuntu.

I downloaded and installed the two plugins that were missing: MDS.rpm and nutcracker-plugin.rpm. I had to convert using Alien to a .deb install and it says that it installed fine. However, going back to the site to access the multicast streams, I still get the missing plugin errors. 

I checked to see where those two programs installed, and it seems to install in the plugins directory of firefox.

I'm running the latest version of Firefox on 7.10 .

ANY help in the right direction would be much appreciated!

---

### Post by guitarman_usa on 2008-03-22
I'm having the same problem (running 7.10 32bit).  My school uses VBrick too.  I also tried installing the MDS.rpm and nutcracker plugins with alien.

Apparently when you use alien with MDS.rpm and nutcracker-plugin.rpm, alien doesn't actually copy the libnutcracker-plugin.so to the plugins directory, or at least it didn't in my case.  After installing MDS.rpm and nutcracker-plugin.rpm (sudo alien --to-deb *packagename*) here's what I did.

sudo cp /usr/local/nutcracker/lib/libnutcracker-plugin.so /usr/lib/firefox/plugins/libnutcracker-plugin.so

and then restarted firefox.  VBrick seems to be working now.

UPDATE:
I was receiving an error about not being able to receive packets, did a quick google search of what port VBrick uses, so just make sure your firewall isn't blocking port 554 and you should be all set.

This stopped working on me, so I used wireshark to see what port it was using and I got 4443 and now its working.

---

