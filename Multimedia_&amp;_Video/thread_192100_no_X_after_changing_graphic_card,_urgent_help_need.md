---
title: "no X after changing graphic card, urgent help needed"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Stefan_hb on 2006-06-08
Hi,
first of all: I still have Breezy, I was just afraid of the breezy forum not beeing frequented anymore, that´s why I post here, I hope you don´t mind.
I changed my graphic card from OLD nvidia ti 4200 to NEW nvidia Geforce 6600. Before I did , I asked in the ubuntu help channel, if I would have to reconfigure X, the folks there said , no, should work without changing anything.
I changed the card, when I boot now, I get a very colourful ragged picture on the sreen (excuse my english), a wiered pattern. 
I tried: sudo dpkg-reconfigure xserver-xorg,
with no result, (I chose the "nv" driver there).
I was using the generic nvidia driver before and didn´t change anything about it.
Please help, I´m writing this using MS Windows, this shows you in what kind of desperate situation I am :)

---

### Post by mscman on 2006-06-08
Try switching to the generic VESA or VGA drivers and seeing if that will at least let you get to an X session.  You won't have any 3d acceleration, but you'll be able to work on getting updated drivers installed and such.

---

