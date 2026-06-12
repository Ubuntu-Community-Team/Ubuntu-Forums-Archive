---
title: "Need Video Card Advice: MythTV, Feisty, x86, Video-out, AGP"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by dtgolder on 2007-04-30
Been struggling with an ATI 9250 that I had laying around, and I'm giving up--need to get an nVidia it seems, so here's the need:

I've got a box set up with Feisty, MythTv, Hauppage 150 etc. and everything works great, EXCEPT the video out on the ATI 9250 AGP.

I get a signal, but the vertical sync is off (like on the old tv's). I have it hooked to a 15" monitor (and the card works) but video out is not working.

Now--playing around I DID get the video out to work (and be viewable) but then the output to the monitor was not acceptable--washed out and difficult to read (and that was with Edgy and the ATI drivers from their site, and a LOT of tweaking).

SO--it seems nVidia might be the way to go--I'm looking for advice on the best card to search for--don't want to spend a fortune (and don't need it--I have an older box and need an AGP card and not PCI-e).

Anyone have a recommendation for an AGP nVidia card that will have a TV-out that's compatible with Feisty and MythTV? I'd like to get something that will work "out of the box" so I don't need to tweak the thing...hope that's not asking for too much.

Don't need hot dog graphics--just the video out so that the MythTV will display on my TV, but still able to use the monitor for the remainder of any computing/surfing with Ubuntu.

Thanks!
d

---

### Post by disturbed1 on 2007-04-30
Just about any of these cards [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+106790727&name=GeForce+FX+series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+106790727&name=GeForce+FX+series)

I have an nVidia FX5500, works like a champ. However, I don't currently have myth tv installed. I did with knopmyth a few months back, using the same card.

As far as tweaking goes, I did have to hand edit xorg.conf to add the svideo out, and mode lines. All I did, was a search on this forum for nVidia tv out.

On the myth tv forums, the FX5200 seems to be the most talked about.

---

### Post by Erlander on 2007-05-01
I have one of these:

[http://tw.giga-byte.com/Products/VGA/Products_Overview.aspx?ProductID=2334](http://tw.giga-byte.com/Products/VGA/Products_Overview.aspx?ProductID=2334)

and am very happy with it although I haven't done much in the way of fancy settings or TV out etc.

It is fanless and AGP.

Rob

---

