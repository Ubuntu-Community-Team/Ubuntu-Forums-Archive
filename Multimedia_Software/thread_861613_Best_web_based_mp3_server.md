---
title: "Best web based mp3 server?"
date: 2008-07-16
forum: Multimedia Software
---

### Post by ovitz on 2008-07-16
Hi there,

I just got a pc which I'd like to set up to serve my very large collection of mp3s and audio over my network and to a few friends on the internet. 

What is the best utility for this? Thanks.

---

### Post by bronkeydain on 2010-03-01
Better late than never :)

The piece of software for this is Ampache. It is a web based Music system. You can create some users and steam your music over the network or internet. It is packed with features!

I noticed with Ubuntu 9.10 it is in the repositories so just type:
sudo apt-get install ampache 

Then restart your apache server:
sudo /etc/init.d/apache2 restart

Then point your browser to [http://localhost/ampache](http://localhost/ampache) and follow the instructions to finalize the install.

---

